# linux-nvme-s-tracepoint

Changes made pertain to [Linux kernel 4.18](https://github.com/torvalds/linux/tree/v4.18).

Existing tracepoint 'S' is added to NVMe driver right after submissions to the Software Queue (SQ). This allows for D2S to roughly represent the time an IO spent in the driver and S2C to represent the time spent in the device (opposed to D2C including both).

Kernel modifications:
 - block/blk-core.c : exported block_sleeprq ('s') tracepoint
 - drivers/nvme/host/pci.c : added tracepoint call after submission to SQ
