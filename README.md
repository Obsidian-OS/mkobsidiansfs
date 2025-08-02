# mkobsidiansfs

A bash script used to make a SquashFS image with multiple packages to be installed on an ObsidianOS installation with `obsidianctl`.

## Usage

```bash
sudo ./mkobsidiansfs [scripts]
```

- `scripts` (optional): Path to a directory containing custom shell scripts, including a `main.sh` script. If provided, these scripts will be copied into the chroot environment, made executable, and `main.sh` will be executed within the chroot. This allows for custom configurations or installations to be performed inside the SquashFS image.

