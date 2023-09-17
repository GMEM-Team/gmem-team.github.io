

## GMEM主页

* 安装mkdocs

  [MkDocs 文档开发教程 (mkdocs-like-code.readthedocs.io)](https://mkdocs-like-code.readthedocs.io/zh_CN/latest/get-started/create-program/) 

  ```sh
  pip install mkdocs
  # 安装主题
  pip install mkdocs-material
  ```

* mkdocs基本命令

  ```sh
  # Print help message
  mkdocs -h
  # 在本地查看网页
  mkdocs serve
  # 构建并发布网页到gh-pages分支
  mkdocs gh-deploy --force --no-history -f ./mkdocs.yml
  ```

* 网页组成

  更新master分支，会自动构建并发布网页

  ```sh
  mkdocs.yml    # The configuration file.
  docs/
      index.md  # The documentation homepage.
      ...       # Other markdown pages, images and other files.
  ```

