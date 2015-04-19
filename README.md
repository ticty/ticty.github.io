
*一份来自漂亮的 [林安雅的博客][] 的 [拷贝][]*

## 使用说明

### 运行环境配置

以 ubuntu server 14.04 为例，以下命令可配置一个最接近 github 解释 markdown 的环境

#### 安装软件

```
sudo apt-get install build-essential git-core ruby2.0 ruby2.0-dev zlib1g-dev nodejs
```

#### 配置ruby

为了后续gem下载包更快速，先按需配置安装源：

```
# 移除原先官方源，此源速度一般很慢
gem source -r https://rubygems.org/
gem source -r http://rubygems.org/

# 添加速度快的附近的源服务器
gem source -a http://mirrors.aliyun.com/rubygems/
```

运行以下命令获得默认ruby版本

```
ruby --version
```

如果显示是2.0以下版本，执行以下命令[切换默认ruby版本至2.0][]：

```
cd /usr/bin/

# 强制链接2.0版本可执行
sudo ln -sf ruby2.0 ruby
sudo ln -sf gem2.0 gem
sudo ln -sf erb2.0 erb
sudo ln -sf irb2.0 irb
sudo ln -sf rake2.0 rake
sudo ln -sf rdoc2.0 rdoc
sudo ln -sf testrb2.0 testrb

# 刷新信息
sudo gem update --system
sudo gem pristine --all
```

安装 bundler

```
sudo gem install bundler
```

#### 配置网站

克隆网站

```
git clone https://github.com/ticty/ticty.github.io
```

配置 github-page 环境

切换至网站目录，配置'Gemfile'文件

```
# cd ticty.github.io

# 配置 github-page 依赖
echo 'source "http://mirrors.aliyun.com/rubygems/"' > 'Gemfile'
echo 'gem "github-pages"' >> 'Gemfile'

# 如果系统使用的是 windows, 请多执行以下命令添加额外配置
# echo 'gem "wdm"' >> 'Gemfile'
```

运行一下命令自动安装所有依赖

```
# 必要时需输入sudo密码
bundle install
```

### 运行

切换至网站目录，执行下面命令

```
# cd ticty.github.io
bundle exec jekyll serve
```

//references
[林安雅的博客]:           <http://painterlin.com/>
[拷贝]:                   <https://github.com/lay1010/lay1010.github.io>
[切换默认ruby版本至2.0]:   <http://www.kaijia.me/2014/08/ubuntu-14-04-switch-defaults-to-ruby-2-0/>
