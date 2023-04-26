# Full Mac Setup Process

## Initial configuration of a brand new Mac

Before starting, I completed Apple's mandatory macOS setup wizard (creating a local user account, and optionally signing into my iCloud account). Once on the macOS desktop, I do the following (in order):

- Install [Dockutil](https://github.com/kcrawford/dockutil/releases/download/3.0.2/dockutil-3.0.2.pkg)
- Install Ansible
  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
  2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):
     1. Run the following command to add Python 3 to your $PATH: `export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"`
     2. Upgrade Pip: `sudo pip3 install --upgrade pip`
     3. Install Ansible: `pip3 install ansible`
  3. Clone or download this repository to your local drive.
  4. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  5. Run `ansible-playbook main.yml --ask-become-pass` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

- Clone mac-dev-playbook to the Mac: `git clone https://github.com/stiliajohny/macos-ansible-playbook`
- Run the playbook with `--skip-tags post`.
  - Run `ansible-playbook main.yaml -k -K` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.
  - If there are errors, you may need to finish up other tasks like installing 'old-fashioned' apps first (since I try to place Photoshop in the Dock and it can't be installed automatically). Then, run the playbook again ;)
- Start Synchronization tasks:

  - Confirm iCloud is configured correctly
  - Confirm FindMy is configured correctly

  - Open Music, make sure computer is authorized, and set Library sync options

- Install old-fashioned apps:
  - [Fritzing](https://fritzing.org/download/)
  - [Arc](https://releases.arc.net/release/Arc-latest.dmg)
  - [Adobe Creative Cloud]() <!-- FIXME add link -->
  - [FinalCutPro]() <!-- FIXME add link -->
  - [VSCode](https://code.visualstudio.com/download)
  - [BlockBlock](https://objective-see.com/products/blockblock.html)
  - [KnockKnock](https://objective-see.com/products/knockknock.html)
  - [Netiquette](https://objective-see.org/products/netiquette.html)
  - [LittleSnitch](https://www.obdev.at/products/littlesnitch/download.html)
  - [AutoDesk Fusion 360](https://www.autodesk.com/products/fusion-360/students-teachers-educators)
  - [SequelPro](https://sequelpro.com/download)
  - [Gopro Webcam](https://community.gopro.com/t5/en/How-to-Use-Your-GoPro-as-a-Webcam/ta-p/394284)
  - [GyroFlow](https://gyroflow.app/)
- Manually copy `~/Documents` folder from another Mac (to save time).
- These things might be automatable, but I do them manually right now:
  - Configure Time Machine backup drive

## To Wrap in Post-provision automation

The following tasks have to wait for the initial Dropbox sync to complete before they'll succeed. So ideally I'll stick this all in a post-provision script but somehow flag it not to run on first provision.

### SSH setup.

- create an ssh key and add it to github
  `ssh-keygen -t rsa -b 4096 -C $(hostname) -f $HOME/.ssh/github_ed25519"

### Terminal setup.

- iTerm2 configuration
  - Go to Preferences > Profiles > Text and set font to `Fira Code Retina 12pt`

### Vim setup

- Open vim
- Install the plugins with `:PlugInstall`

### Tmux setup.

- Open tmux
- Install TPM:
  `git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`
- Install tmux plugins with `prefix + I`

### k3d

- Confirm k3d is installed

  ```bash
  k3d --version
  ```

- Create a cluster

  ```bash
  k3d cluster create k3s-default-local --api-port 6550 -p "8081:80@loadbalancer" -p "8444:443@loadbalancer" --agents 1
  ```

- Export the kubeconfig

  ```bash
  k3d kubeconfig get k3s-default-local >  ~/.kube/custom-contexts/k3s-default-local.yml
  ```

## Browser setup

- Install Extensiosn
- Login to Google and other SSO services
