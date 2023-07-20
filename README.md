## ssd hook sidecar

Simple sidecar based on [kubevirt hook example.](kubevirt.io/kubevirt/cmd/example-hook-sidecar)

The sidecar appends qemu args to append sata disks `rotation_rate=1`.

This is needed for some specific use cases where we wish the sata virtual disks to appear as `ssd` to the guest.

Ensure kubevirt feature gate `Sidecar` is enabled.

Annotations needed to make this work are:

```yaml
annotations:
  # Request the hook sidecar
  hooks.kubevirt.io/hookSidecars: '[{"image": "docker.io/gmehta3/ssd:dev"}]'
  # Annotation to trigger ssd arguments
  ssd.vm.kubevirt.io/ssd-patcher: "true"
```