# learn-kubernetes
## Kebutuhan
- kubelet
- kubeadm
- kubectl
- docker

## Minimum Instalasi
saya menggunakan os ubuntu 14.04
- minimal harus ada 2 vm/server yang berjalan untuk menjalankan kubernetes.
- 1 untuk master
- 1 untuk werker/node

## Instalasi di master
- install docker
  - ``` apt-get install -y docker.io ```
- update dan install transport https
  - ``` apt-get update && apt-get install -y apt-transport-https ```
- menambah repository
  - ``` curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ```
    - ``` cat <<EOF >/etc/apt/sources.list.d/kubernetes.list ```
    - ``` deb http://apt.kubernetes.io/ kubernetes-xenial main ```
    - ``` EOF ```
  - ``` apt-get update ```
- install kubernetes
  - ``` apt-get install -y kubelet kubeadm kubectl ```
- setting kubeadm
  - ``` kubeadm init ```
    - ``` mkdir -p $HOME/.kube ```
    - ``` sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config ```
    - ``` sudo chown $(id -u):$(id -g) $HOME/.kube/config ```
- deploy network pada cluster
  - lihat status pada pada cluster
    - ``` kubectl get nodes ```
  - lihat status pada pods
    - ``` kubectl get pods --all-namespaces ```
  - deploy network
    - ``` export kubever=$(kubectl version | base64 | tr -d '\n') ```
    - ``` kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$kubever" ```
  - melihat status node dan pods
