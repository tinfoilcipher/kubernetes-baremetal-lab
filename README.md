# kubernetes-baremetal-lab
Configurations to build a HA Kubernetes lab on bare metal using kubeadm, ansible, helmfile

## tl;dr

Don't do that. This repo is intended for use with the blog post [Building a Bare Metal Kubernetes Lab](https://www.tinfoilcipher.co.uk/2023/01/20/building-a-bare-metal-kubernetes-lab-part-1/?preview=true).

If you are struggling to deploy a cluster for the first time or understand why anything works, this post will (hopefully) explain some things. There's a lot of moving parts there so let me know if anything doesn't make sense.

## I Already Know What I'm Doing

If you insist!

Prereqs:

- (ansible)[https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html]
- (kubectl)[https://kubernetes.io/docs/tasks/tools/#kubectl]
- (kubeadm)[https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/]
- (helmfile)[https://github.com/helmfile/helmfile]

Update the values in:

- `ansible/inventory.yaml`
- `ansible/main.yaml`
- `helmfile/values.yaml`
- `helmfile/apps/metallb/manifests/loadbalancer_bootstrap.yaml`

```bash
cd ansible
ansible-playbook -i inventory.yaml main.yaml -K
cd ..
```

Init cluster with `kubeadm`, at least 3 control plane nodes and as many data notes as you need.

Apply the flannel overlay and namespaces:

`kubectl apply -f kubernetes/.`

Deploy the Kubernetes internal network infrastructure, PKI and obersavility tools:

`helmfile -f helmfile/helmfile.yaml -e default sync`

## Proper Documentation

This repo is intended for use with the blog post [Building a Bare Metal Kubernetes Lab](https://www.tinfoilcipher.co.uk/2023/01/20/building-a-bare-metal-kubernetes-lab-part-1/?preview=true).

If none of the words above mean anything to you, then that post will (hopefully) make cover everything well.

Please have a read through before raising any issues. There's a lot of moving parts there so let me know if anything doesn't make sense.
