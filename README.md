一份来自漂亮的[林安雅的博客](http://painterlin.com/)的[拷贝](https://github.com/lay1010/lay1010.github.io)  

## Usage
### Install Prequirement
Take debian based Linux distrubtion as example(mine is Ubuntu 14.04):

    # modify the name as requirement
    RepoName='ticty.github.io'

    # some basic but may not require
    sudo apt-get install buile-essential git-core

    # ruby and js parser
    sudo apt-get install ruby ruby-dev zlib1g-dev nodejs

    # clone this blog template
    git clone https://github.com/ticty/ticty.github.io $RepoName

    # Some optional steps you need manual do:
    #  1. modify 'CNAME' to your custom domain, or just delete it before push to your repo;
    #  2. check and modify '__config.yml' file, notice the author, title and url info;

    # modify the gem source to a faster one
    #  gem source -r https://rubygems.org/
    #  gem source -r http://rubygems.org/
    #  gem source -a http://mirrors.aliyun.com/rubygems/

    # install bundle
    sudo gem install bundler

    # configure for bundle
    # modify the ruby gem source as require
    cd $RepoName
    echo 'source "http://mirrors.aliyun.com/rubygems/"' > 'Gemfile'
    echo 'gem "github-pages"' >> 'Gemfile'
    # if run on windows, add below:
    # echo 'gem "wdm"' >> 'Gemfile'

    # install dependence
    bundle install

### Run
    cd $RepoName
    bundle exec jekyll serve
