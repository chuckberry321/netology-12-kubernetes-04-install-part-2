# Домашнее задание к занятию "12.4 Развертывание кластера на собственных серверах, лекция 2"

## Задание 1: Подготовить инвентарь kubespray


Статус нод

```
vagrant@vagrant:~/netology-12-kubernetes-04-install-part-2$ kubectl get nodes
NAME    STATUS   ROLES                  AGE    VERSION
cp1     Ready    control-plane,master   3h2m   v1.24.3
node1   Ready    <none>                 3h1m   v1.24.3
node2   Ready    <none>                 3h1m   v1.24.3
node3   Ready    <none>                 3h1m   v1.24.3
node4   Ready    <none>                 3h1m   v1.24.3
vagrant@vagrant:~/netology-12-kubernetes-04-install-part-2$
```

etcd на control-plane ноде

```
yc-user@cp1:~$ etcd
{"level":"info","ts":"2022-08-21T18:38:58.790Z","caller":"etcdmain/etcd.go:73","msg":"Running: ","args":["etcd"]}
{"level":"warn","ts":"2022-08-21T18:38:58.790Z","caller":"etcdmain/etcd.go:105","msg":"'data-dir' was empty; using default","data-dir":"default.etcd"}
{"level":"info","ts":"2022-08-21T18:38:58.790Z","caller":"embed/etcd.go:131","msg":"configuring peer listeners","listen-peer-urls":["http://localhost:2380"]}
{"level":"info","ts":"2022-08-21T18:38:58.790Z","caller":"embed/etcd.go:139","msg":"configuring client listeners","listen-client-urls":["http://localhost:2379"]}
{"level":"info","ts":"2022-08-21T18:38:58.790Z","caller":"embed/etcd.go:368","msg":"closing etcd server","name":"default","data-dir":"default.etcd","advertise-peer-urls":["http://localhost:2380"],"advertise-client-urls":["http://localhost:2379"]}
{"level":"info","ts":"2022-08-21T18:38:58.790Z","caller":"embed/etcd.go:370","msg":"closed etcd server","name":"default","data-dir":"default.etcd","advertise-peer-urls":["http://localhost:2380"],"advertise-client-urls":["http://localhost:2379"]}
{"level":"warn","ts":"2022-08-21T18:38:58.790Z","caller":"etcdmain/etcd.go:146","msg":"failed to start etcd","error":"listen tcp 127.0.0.1:2379: bind: address already in use"}
{"level":"fatal","ts":"2022-08-21T18:38:58.790Z","caller":"etcdmain/etcd.go:204","msg":"discovery failed","error":"listen tcp 127.0.0.1:2379: bind: address already in use","stacktrace":"go.etcd.io/etcd/server/v3/etcdmain.startEtcdOrProxyV2\n\t/go/src/go.etcd.io/etcd/release/etcd/server/etcdmain/etcd.go:204\ngo.etcd.io/etcd/server/v3/etcdmain.Main\n\t/go/src/go.etcd.io/etcd/release/etcd/server/etcdmain/main.go:40\nmain.main\n\t/go/src/go.etcd.io/etcd/release/etcd/server/main.go:32\nruntime.main\n\t/go/gos/go1.16.15/src/runtime/proc.go:225"}
yc-user@cp1:~$
```

Изменения для kubectl вносил на локальной машине в config в раздел для кластера mk, который создавал на прошлом занятии.

В k8s-cluster.yml добавил  supplementary_addresses_in_ssl_keys: [158.160.8.69]

