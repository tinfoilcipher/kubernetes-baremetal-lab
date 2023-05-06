# kubernetes-baremetal-lab
Configurations to build a HA Kubernetes lab on bare metal using kubeadm, ansible, helmfile

## tl;dr

Don't do that.

## Proper Documentation

This repo is intended for use with the blog post [Building a Bare Metal Kubernetes Lab](https://www.tinfoilcipher.co.uk/2023/01/20/building-a-bare-metal-kubernetes-lab-part-1/?preview=true). That post (hopefully) already covers everything well.

If you don't want to read it, just be sure to update a couple of places to be suitable for your infrastructure:

- `ansible/inventory.yaml`
- `ansible/main.yaml`
- `helmfile/values.yaml`
- `helmfile/apps/metallb/manifests/loadbalancer_bootstrap.yaml`

