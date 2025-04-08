# kubernetes

Generate talos config:
```
talosctl gen config cluster01 https://10.120.0.10:6443   --with-secrets secrets.yaml   --config-patch @patches/allow-controlplane-workloads.yaml   --config-patch @patches/cni.yaml   --config-patch @patches/dhcp.yaml   --config-patch @patches/install-disk.yaml   --config-patch @patches/interface-names.yaml   --config-patch @patches/kubelet-certificates.yaml   --config-patch-control-plane @patches/vip.yaml   --output rendered/
```

Apply changes in config to cluster:
```
talosctl apply-config -f rendered/controlplane.yaml -n 10.120.0.11 -n 10.120.0.12 -n 10.120.0.13
```
