# Django Starter

## Description
使用 docker 来搭建 python 2.7.14、django、django restframework 开发环境。

需要配合 `https://github.com/WisZhou/django-starter-template.git` 一起食用

依赖
```
Django<2.0
django-cors-headers
django-nose
djangorestframework
djangorestframework-jwt
raven
coreapi
django-rest-swagger
celery
django-test-without-migrations
django-nose
coverage
mysqlclient
pycrypto
django-multi-captcha-admin
django-recaptcha
django-simple-captcha
```

## Usage

### Install
``` bash
# clone
git clone https://github.com/WisZhou/django-starter.git $starter_dir
# build
cd django-starter && git checkout 2.7.14 && docker build . -t django-starter:2.7.14
```
### create project & runserver
```
# create project
docker run --rm -t -v `pwd`:/code django-starter:2.7.14 /bin/create_project your_project

# build project image
cd your_project
build . -t your_project_name:latest

# edit docker-compose.yml
# change image to your project image

# install fabric
pip install fabric

# runserver
cd your_project
fab migrate
fab runserver
```

### project structure
```
your_project
|── .gitignore      # Python gitignore
|── Dockerfile
|── docker-compose.yml      # 启动docker配置
|── fabfile.py              # 常用任务
├── manage.py
├── requirements
│   ├── base.txt
│   ├── dev.txt
│   └── prod.txt
└── story
├── __init__.py
├── admin.py       # 自动加载所有 models 到 django admin
├── migrations
│   └── __init__.py
├── models         # 所有 models 统一放到这个文件夹管理
│   └── __init__.py
├── settings.py
├── configs # 生产环境和开发环境配置做隔离
│   ├── __init__.py
│   └── config.py
│   └── dev_config.py
│   └── test_config.py
│   └── pro_config.py
├── urls.py
    └── wsgi.py
```
