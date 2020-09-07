## git-secrets

Prevents you from committing passwords and other sensitive information to a git repository.

### 1. 安装脚本

#### macOS/Linux

```sh
make install
```

#### Windows

运行 PowerShell 脚本

```sh
PS > ./install.ps1
```

**如果运行提示策略不允许，可以采用下列方法修改策略**

```sh
set-executionpolicy remotesigned
```

### 2. 安装提交 hook

对每次提交的变更文件自动做检查。

```sh
git secrets --install -g
```

### 3. 全盘检查

对当前文件以及历史提交做全盘检查。

```sh
cd git_repo_root
git secrets --scan
```

#### 只扫描最新文件

```sh
git secrets --scan --no-history
```

#### 添加例外

对于检查出来但确认没有问题的字符串，可以添加例外来绕过检查：

```sh
git config --add secrets.allowed xxxxx
```

### Q&A

#### 在 SourceTree 下提交提示 `git: 'secrets' is not a git command`：

请参考下面的步骤修复：

[https://gist.github.com/Neo23x0/1b03425d60c3735a0bc5b18dc08c9abd](https://gist.github.com/Neo23x0/1b03425d60c3735a0bc5b18dc08c9abd)
