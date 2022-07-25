# Deep study k8s

Related files for <https://time.geekbang.org/column/intro/100015201>.

## prepare k8s

> WSL2 is also can work.

1. Install docker-ce via <https://mirrors.bfsu.edu.cn/help/docker-ce/>

2. Install minikube via <https://minikube.sigs.k8s.io/docs/start/>

    ```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
    sudo dpkg -i minikube_latest_amd64.deb
    ```

3. Create k8s cluster

    ```bash
    # https://minikube.sigs.k8s.io/docs/handbook/vpn_and_proxy/
    export HTTP_PROXY=http://<proxy hostname:port>
    export HTTPS_PROXY=$HTTP_PROXY
    export NO_PROXY=localhost,127.0.0.1,10.96.0.0/12,192.168.59.0/24,192.168.49.0/24,192.168.39.0/24

    minikube start --driver=docker --cpus='6' --memory='16g' --image-mirror-country='cn'

    #minikube delete --all
    ```

4. Some usefull bash alias

    ```bash
    alias kubectl="minikube kubectl --"
    alias kc="kubectl"
    alias kca="kubectl apply"
    alias kcd="kubectl delete"
    alias kcl="kubectl logs"
    alias kcs="kubectl describe"
    alias kcga="kubectl get secret,configmap,pod,rs,service,statefulset,jobs,cronjobs,pvc,pv -o wide"
    # 'nslookup' command in busybox has issues.
    alias kcrnetdbg="kubectl run net-debug --image=nicolaka/netshoot --image-pull-policy=IfNotPresent -it --rm -- /bin/sh"
    alias kcdnetdbg="kubectl delete pod/net-debug"
    ```
