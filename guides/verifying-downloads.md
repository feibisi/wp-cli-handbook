---
title: "验证 WP-CLI 下载文件"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Guides
    - Repos
    - Data
---

# 验证 WP-CLI 下载文件

## 为何要验证下载文件？

验证下载文件可确保：
- **真实性**：文件由 WP-CLI 维护者创建并签名
- **完整性**：文件在下载过程中未被损坏或篡改

## 快速验证指南

下载 `wp-cli.phar` 后，您可以使用 GPG 签名或校验和进行验证。

### 方法一：使用 GPG 签名验证（推荐）

此方法提供最强的安全性，因为它同时验证了下载文件的完整性和真实性。

#### 步骤 1：下载签名文件

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar.asc
```

对于特定版本，请从 GitHub 发布页面下载（将 `X.X.X` 替换为所需版本）：

```bash
curl -LO https://github.com/wp-cli/wp-cli/releases/download/vX.X.X/wp-cli-X.X.X.phar
curl -LO https://github.com/wp-cli/wp-cli/releases/download/vX.X.X/wp-cli-X.X.X.phar.asc
```

例如，要下载版本 2.12.0：

```bash
curl -LO https://github.com/wp-cli/wp-cli/releases/download/v2.12.0/wp-cli-2.12.0.phar
curl -LO https://github.com/wp-cli/wp-cli/releases/download/v2.12.0/wp-cli-2.12.0.phar.asc
```

#### 步骤 2：导入 WP-CLI 发布签名密钥

WP-CLI 发布版本使用 WP-CLI 发布签名密钥进行签名。导入公钥：

```bash
curl -L https://raw.githubusercontent.com/wp-cli/builds/gh-pages/wp-cli.pgp | gpg --import
```

密钥指纹为：
```
63AF 7AA1 5067 C056 16FD  DD88 A3A2 E8F2 26F0 BC06
```

导入后，您可以验证密钥指纹：

```bash
gpg --list-keys --with-fingerprint releases@wp-cli.org
```

输出应包含：
```
pub   rsa2048 2018-05-31 [SC]
      63AF 7AA1 5067 C056 16FD  DD88 A3A2 E8F2 26F0 BC06
uid           [ unknown] WP-CLI Releases <releases@wp-cli.org>
sub   rsa2048 2018-05-31 [E]
```

**注意：** v1.5.1（2016年7月）之前的版本使用不同的密钥签名（指纹：`3B91 91CD 3CF1 B5C5 10EE FAF6 AFAA E4A2 85E0 40A8`）。如果您需要验证旧版本，请从[构建仓库的 README](https://github.com/wp-cli/builds/blob/gh-pages/README.md) 导入该密钥。

#### 步骤 3：验证签名

对于最新的稳定版本：

```bash
gpg --verify wp-cli.phar.asc wp-cli.phar
```

对于特定版本：

```bash
gpg --verify wp-cli-2.12.0.phar.asc wp-cli-2.12.0.phar
```

如果签名有效，您将看到类似以下的输出：

```
gpg: Signature made {DATE}
gpg:                using RSA key 63AF7AA15067C05616FDDD88A3A2E8F226F0BC06
gpg: Good signature from "WP-CLI Releases <releases@wp-cli.org>" [unknown]
```

您可能会看到关于密钥不受信任的警告：
```
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
```

如果您尚未亲自验证并签署 WP-CLI 密钥，出现此警告是正常的。关键部分是看到 "Good signature"，这确认了文件是由此密钥签署且未被修改。

### 方法 2：使用校验和验证

如果 GPG 不可用，您可以使用 SHA-512 或 SHA-256 校验和来验证完整性（但无法验证真实性）。

#### 使用 SHA-512

下载 SHA-512 校验和文件：

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar.sha512
```

或者针对特定版本（将 `X.X.X` 替换为您的版本号）：

```bash
curl -LO https://github.com/wp-cli/wp-cli/releases/download/vX.X.X/wp-cli-X.X.X.phar.sha512
```

通过比较输出结果来验证校验和：

```bash
sha512sum wp-cli.phar
cat wp-cli.phar.sha512
```

两个哈希值应完全匹配。

#### 使用 SHA-256 校验

下载 SHA-256 校验和文件：

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar.sha256
```

或下载特定版本的校验文件（将 `X.X.X` 替换为你的版本号）：

```bash
curl -LO https://github.com/wp-cli/wp-cli/releases/download/vX.X.X/wp-cli-X.X.X.phar.sha256
```

通过比较输出结果来验证校验和：

```bash
sha256sum wp-cli.phar
cat wp-cli.phar.sha256
```

两个哈希值应完全一致。

**注意：** 校验和验证仅确认文件与发布的校验和匹配，并不能验证文件是否由 WP-CLI 维护者创建。如需完整的安全性保障，请使用 GPG 签名验证。

## 验证文件存放位置

### 最新稳定版与每夜构建版

最新稳定版和每夜构建版的验证文件位于：
- <https://github.com/wp-cli/builds/tree/gh-pages/phar>

可用文件：
- `wp-cli.phar.asc` - 最新稳定版的 GPG 签名
- `wp-cli.phar.sha512` - 最新稳定版的 SHA-512 校验和
- `wp-cli.phar.md5` - MD5 校验和（出于安全考虑不推荐使用；MD5 加密算法已被破解，易受碰撞攻击）
- `wp-cli-nightly.phar.asc` - 每夜构建版的 GPG 签名
- `wp-cli-nightly.phar.sha512` - 每夜构建版的 SHA-512 校验和

### 特定版本发布

对于特定版本，验证文件可在 [GitHub 发布页面](https://github.com/wp-cli/wp-cli/releases) 获取：

每个发布版本包含：
- `wp-cli-X.X.X.phar` - WP-CLI phar 文件
- `wp-cli-X.X.X.phar.asc` - 分离式 GPG 签名
- `wp-cli-X.X.X.phar.gpg` - 内联 GPG 签名
- `wp-cli-X.X.X.phar.sha512` - SHA-512 校验和
- `wp-cli-X.X.X.phar.sha256` - SHA-256 校验和
- `wp-cli-X.X.X.phar.md5` - MD5 校验和（出于安全考虑不推荐使用；MD5 在加密层面已被破解，易受碰撞攻击）

## 完整的安装与验证示例

以下是下载、验证和安装 WP-CLI 的完整示例：

```bash
# 下载 WP-CLI
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

# 下载签名文件
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar.asc

# 导入签名密钥（仅首次需要）
curl -L https://raw.githubusercontent.com/wp-cli/builds/gh-pages/wp-cli.pgp | gpg --import

# 验证签名
gpg --verify wp-cli.phar.asc wp-cli.phar

# 如果验证成功，测试是否正常工作
php wp-cli.phar --info

# 设为可执行文件并移动到 PATH 路径
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp

# 验证安装
wp --info
```

## Additional resources

- [WP-CLI Builds Repository](https://github.com/wp-cli/builds) - Contains signing keys and latest builds
- [GitHub Releases](https://github.com/wp-cli/wp-cli/releases) - All version releases with verification files
- [GNU Privacy Guard](https://gnupg.org/) - Learn more about GPG