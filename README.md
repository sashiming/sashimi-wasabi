# sashimi-wasabi

『[作って学ぶ]OSのしくみ』に沿って作っているOS

## Build

```sh
rustup target add x86_64-unknown-uefi # only first time
mkdir -p mnt/EFI/BOOT # only first time
cargo build --target x86_64-unknown-uefi
cp target/x86_64-unknown-uefi/debug/wasabi.efi mnt/EFI/BOOT/BOOTX64.EFI
```

## Run

適宜OVMF.fdをローカルに入れておく

```sh
qemu-system-x86_64 -bios ./OVMF.fd -drive format=raw,file=fat:rw:./mnt
```