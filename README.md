# consul-template-practice

## serverで実行
consul-template -consul 127.0.0.1:8500 -template "/root/hosts-node.ctmpl:/etc/hosts" -dry

## node01で実行しserverの表示が変化することを確認
consul leave


# Running Registrator

docker run -d \
    --name=registrator \
    --net=host \
    --privileged \
    --volume=/var/run/docker.sock:/tmp/docker.sock \
    gliderlabs/registrator:latest \
    consul://localhost:8500

curl 127.0.0.1:8500/v1/catalog/services
