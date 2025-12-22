# mkobsidiansfs

A bash script used to make a SquashFS image with multiple packages to be installed on an ObsidianOS installation with `obsidianctl`.

## Usage

```bash
sudo ./mkobsidiansfs [config] [output_sfs]
```

`config` (optional): a config file that let's you configure your system declarativly.
Example:
```
BUILD_DIR="obsidian_rootfs" # SquashFS generation directory # Below is default packages for an install of arch and this script to work.
PACKAGES="base linux linux-firmware networkmanager sudo vim nano efibootmgr python squashfs-tools arch-install-scripts base-devel git gptfdisk f2fs-tools grub gpm wget os-prober pv"
HAVE_AUR="yay-bin"        # Manual AUR package. Only set to yay-bin or none. Only use none if you do not have base-devel or git there ^
YAY_GET="obsidianctl-git plugind-git obsidianwall-git obsidian-control" # Packages to get from the AUR with yay.
OUTPUT_SFS="system.sfs"   # Output SquashFS
TIMEZONE=""               # Olson Timezone
NETUPDATE=""              # DO NOT SET. Used internally to enable obsidianctl netupdate.
HOSTNAME="obsidianbtw"    # Hostname
SERVICES="NetworkManager gpm plugind" # Services to enable with systemctl
ROOT_HAVEPASSWORD=""      # Set this to anything other than blank to remove the password from the root user.
CUSTOM_SCRIPTS_DIR=""     # Place where scripts that must run in the SquashFS will run.
ADMIN_USER="user"             # Creates an user with the 'wheel' group
ADMIN_DOTFILES=""         # If an admin is created, a git repo that will be cloned to the new user.
ADMIN_PASSWORD=""         # Password to set for ADMIN_USER, if empty will ask interactively
ADMIN_DOTFILES_TYPE=""    # Type of dotfile repo. Requires git in PACKAGES if HOME or CONFIG.
# HOME - the inside of the repo has data for your home directory (ex: .zshrc, .config, .bashrc)
# CONFIG - the inside of the repo has data for your .config directory (ex: gtk, fish, kitty, hypr)
# * - ignore dotfiles repo (can be empty string) and copy dotfiles from that user's home.
#     recommended: set this to $SUDO_USER if this is being run with sudo.
POST_INSTALL="" # Line of bash to execute after installation is done
```
An configuration should end with the `.mkobsfs` extention to identify it clearly.

`output_sfs` (optional): overrides the OUTPUT_SFS configuration
