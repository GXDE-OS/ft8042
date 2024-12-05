# ft8042
Keyboard and mouse driver for phytium platform notebooks

## How to build
```bash
make
sudo make install
```

Makefile 改内核名称，depmod -a 后面加内核名称

## dkms build
```bash
sudo cp ft8042 /usr/src/ft8042-0.1/
sudo dkms add -m ft8042 -v 0.1
sudo dkms build -m ft8042 -v 0.1  --kernelsourcedir=/lib/modules/6.6.47-current-arm64/build -k 6.6.47-current-arm64v
sudo dkms install -m ft8042 -v 0.1  --kernelsourcedir=/lib/modules/6.6.47-current-arm64/build -k 6.6.47-current-arm64
```