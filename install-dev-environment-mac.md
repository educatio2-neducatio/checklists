# Install Dev Environment on Mac

## Homebrew

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## XCode

```
sudo xcodebuild -license
xcode-select --install
```

## rbenv

```
brew install rbenv ruby-build
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile
```

## Ruby

```
rbenv install -l
rbenv install 2.2.0
rbenv global 2.2.0
gem install bundler
gem install foreman
rbenv rehash
```

## Sublime

```
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime
```

## Git

```
brew install git
source ~/.bash_profile
which git

git config user.name "Your Name"
git config user.email your@email.abc
git config --global core.editor "sublime -n -w"
```

## Ssh

```
ssh-keygen -t rsa -C "your@email.abc"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

## Github

See: https://help.github.com/articles/generating-ssh-keys/

* Add your SSH key to github 
* Check with: `ssh -T git@github.com`

## Postgresql

```
brew install postgres
ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```

## Redis

```
brew install redis
ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

## API Server

```
cd ~/Code
git clone git@github.com:efounders/solved-api-server.git
bundle install

cp .env.example .env # ask for missing dev credentials
cp config/database.yml.example config/database.yml # edit if needed

bundle exec rake db:create
foreman run bundle exec rake db:schema:load
foreman run bundle exec rake db:seed
foreman start
```

## Node

See: http://blog.teamtreehouse.com/install-node-js-npm-mac

```
brew install node
```

## Bower

```
npm install -g bower
```

## Ember CLI

```
npm install -g ember-cli
```

## Solved-core

```
cd ~/Code
git clone git@github.com:efounders/solved-core.git
cd solved-core
npm install
bower install
cp .env.example .env # ask for missing dev credentials
foreman run ember s
```

## Solved-website

```
cd ~/Code
git clone git@github.com:efounders/solved-website.git
cd solved-website
npm install
bower install
cp .env.example .env # ask for missing dev credentials
foreman run ember s
```
