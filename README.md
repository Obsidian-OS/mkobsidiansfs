# mkobsidiansfs

A bash script used to make a SquashFS image with multiple packages to be installed on an ObsidianOS installation with `obsidianctl`.

## Usage

```bash
sudo ./mkobsidiansfs [config]
```

`config` (optional): a config file that let's you configure your system declarativly.
Example:
```
# --- System creation ---
BUILD_DIR="/tmp/obsidian_rootfs" # SquashFS generation directory
PACKAGES="base linux linux-firmware networkmanager sudo vim nano efibootmgr python squashfs-tools arch-install-scripts base-devel" # Packages to install
OUTPUT_SFS="system.sfs" # Output SquashFS
TIMEZONE="America/New_York" # Olson Timezone
HOSTNAME="obsidian" # Hostname
CUSTOM_SCRIPTS_DIR="" # Path to a directory containing custom shell scripts, including a main.sh script.
# If provided, these scripts will be copied into the chroot environment, made executable, and main.sh will be executed within the chroot.
# This allows for custom configurations or installations to be performed inside the SquashFS image.
# --- User Creation ---
ADMIN_USER="neoapps" # Creates an user with the wheel group and adds the wheel group to the sudoers file.
ADMIN_DOTFILES="" # A git repo with dotfiles that will copy to your home directory
ADMIN_DOTFILES_TYPE="" # Type of dotfile repo.
# HOME - the inside of the repo has data for your home directory (ex: .zshrc, .config, .bashrc) (requires git to be in PACKAGES)
# CONFIG - the inside of the repo has data for your config directory (ex: gtk, fish, kitty, hypr) (requires git to be in PACKAGES)
# * - ignore dotfiles repo and copy dotfiles from that user's home.
```
An configuration should end with the `.mkobsfs` extention to identify it clearly.
