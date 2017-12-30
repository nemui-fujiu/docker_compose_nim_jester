
## Docker Compose構成
構成はこんな感じ

```
.
├── README.md
├── docker-compose.yml
├── mysql
├── nginx
│   ├── Dockerfile
│   └── server.conf
├── nim
│   └── Dockerfile
└── work
```

## プロジェクト構成

```
.
└── work
    └── nim_jester
        ├── bin # コンパイル後のソースを配置する。
        ├── nim_jester.nimble
        └── src
            ├── nim_jester.nim
            └── resources
                ├── conf
                │   └── conf.json
                └── templates
                    ├── base.tmpl
                    └── home.tmpl
```

## 操作方法

コンテナの作成

```
docker-compose up -d --build
```

```
docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                     NAMES
1e72f858790d        dockercomp_nginx    "nginx -g 'daemon ..."   About an hour ago   Up About an hour    0.0.0.0:9090->80/tcp      std_nginx
7919c797ba80        dockercomp_app      "/bin/bash"              About an hour ago   Up About an hour                              std_nim
e6e7e27d7efd        mysql:latest        "docker-entrypoint..."   About an hour ago   Up About an hour    0.0.0.0:43306->3306/tcp   std_mysql
e780d77338fe        redis:latest        "docker-entrypoint..."   About an hour ago   Up About an hour    0.0.0.0:46379->6379/tcp   std_redis
```

コンテナに入ってjesterの起動

```
docker exec -it std_nim bash
```

```
/opt/nim_jester# nimble serverstart
  Executing task serverstart in /opt/nim_jester/nim_jester.nimble
  Verifying dependencies for nim_jester@0.1.0
      Info: Dependency on jester@>= 0.2.0 already satisfied
  Verifying dependencies for jester@0.2.0
   Building nim_jester/nim_jester using c backend
```

あとはブラウザから確認

http://localhost:9090/