## git-secrets

Prevents you from committing passwords and other sensitive information to a git repository.

### 0. 环境要求

git 版本在 **2.9** 及以上。

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

全局安装，这样对后续本机所有仓库的提交包含的变更文件都会自动做检查。

```sh
git secrets --install -g
```

### 3. 全盘检查

#### 对当前文件以及历史提交做全盘检查。

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
git config --add secrets.allowed AKIDxxxxx
```

### Q&A

#### SourceTree 下 commit 时提示 `git: 'secrets' is not a git command`：

请参考下面的步骤修复：

[https://gist.github.com/Neo23x0/1b03425d60c3735a0bc5b18dc08c9abd](https://gist.github.com/Neo23x0/1b03425d60c3735a0bc5b18dc08c9abd)

#### tlinux 上 git 版本较旧

请参考下面的指引升级。

```sh
# 安装SCL工具
yum install tlinux-release-scl -y

# 卸载旧版 Git
yum remove git -y

# 安装 Git 2.18
yum install rh-git218 -y

# 启用CLI
yum remove git

# 查看已安装Git版本
git --version
```

[http://km.oa.com/group/799/articles/show/299371?ts=1587007135](http://km.oa.com/group/799/articles/show/299371?ts=1587007135)


#### Centos 机器 git 版本较旧

可以参考 [https://www.softwarecollections.org/en/scls/rhscl/rh-git218/](https://www.softwarecollections.org/en/scls/rhscl/rh-git218) 安装。

不要忘记添加到环境变量中, 在 `~/.bash_profile` 中添加：

```sh
source /opt/rh/rh-git218/enable
```

