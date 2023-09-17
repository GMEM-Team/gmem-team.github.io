

## GMEM主页编辑

[GMEM's Home](https://gmem-team.github.io) 

* 安装mkdocs

  [MkDocs 文档开发教程 (mkdocs-like-code.readthedocs.io)](https://mkdocs-like-code.readthedocs.io/zh_CN/latest/get-started/create-program/) 

  ```sh
  pip install mkdocs
  # 安装主题
  pip install mkdocs-material
  
  # Print help message
  mkdocs -h 
  ```

* 网页组成

  ```sh
  mkdocs.yml    # The configuration file.
  docs/
      index.md  # The documentation homepage.
      ...       # Other markdown pages, images and other files.
  site/
      index.html # 由mkdocs生成的静态网页，托管到gh-pages分支
      ... 
  ```

* 在本地查看网页

  ```sh
  mkdocs serve
  ```
  
* 更新网页到gh-pages分支

  ```sh
  mkdocs gh-deploy --force --no-history -f ./mkdocs.yml
  ```

