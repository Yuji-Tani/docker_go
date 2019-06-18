# docker_go

## 通常のgoの実行
```
$ go run docker_go
```

## コンテナビルド
```
$ docker image build -t docker_go/echo:latest .
```

## コンテナ起動
```
$ docker container run -d docker_go/echo:latest
$ docker container run -d yujitani/docker_go:latest
```

## コンテナ停止
```
$ docker container stop $(docker container ls --filter "ancestor=docker_go/echo" -q)
$ docker container stop $(docker container ls --filter "ancestor=yujitani/docker_go" -q)
```

## ポートフォワードでの起動
```
docker container run -d -p 9000:8080 docker_go/echo:latest
```

### 起動・疎通確認
```
$ curl http://localhost:9000/
Hello Docker!!
```

## docker hubへのpush
IDを変更
```
$docker image tag docker_go/echo:latest yujitani/docker_go:latest
```
docker hubへpush
```
$ docker image push yujitani/docker_go:latest
The push refers to repository [docker.io/yujitani/docker_go]
f9e080a40b80: Pushed
31cebc68dace: Pushed
186d94bd2c62: Mounted from library/golang
24a9d20e5bee: Mounted from library/golang
e7dc337030ba: Mounted from library/golang
920961b94eb3: Mounted from library/golang
fa0c3f992cbd: Mounted from library/golang
ce6466f43b11: Mounted from library/golang
719d45669b35: Mounted from library/golang
3b10514a95be: Mounted from library/golang
latest: digest: sha256:385a82bb8e20dd7b63a25b62765d67ec0edd09b1380202523ec089c97766cf27 size: 2417
```