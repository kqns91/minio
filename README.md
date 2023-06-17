# minio

オブジェクトストレージ minio を構築する compose ファイルです。

## setup

起動すると、minio が立ち上がり、`sample`バケットが作成され、`init_data`の中身が格納されます。

```
docker-compose up -d
```

※ 起動時に作成されるバケット名を変えたい場合、compose.yml で mc の entrypoint を編集してください。

```yml
  mc:
    ...
    entrypoint: >
      /bin/sh -c "
      mc alias set myminio http://minio:9000 admin adminpass;
      mc mb myminio/sample;
      mc cp init_data/* myminio/sample;
    ...
```

## コンソール

http://localhost:9001 で minio-console をみられます。  

