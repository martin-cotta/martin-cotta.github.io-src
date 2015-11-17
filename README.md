
### Hexo Site for martin-cotta.github.io

``` sh
git clone https://github.com/martin-cotta/martin-cotta.github.io-src.git
git submodule init
git submodule update
npm install
hexo server
```

Deploy to github.io

``` sh
hexo clean
hexo deploy
```

```
cd themes/hueman
ln -s ../hueman_config.yml _config.yml
```

M.
