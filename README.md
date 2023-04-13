[![CI](https://github.com/stiliajohny/macos-ansible-playbook/actions/workflows/ci.yml/badge.svg)](https://github.com/stiliajohny/macos-ansible-playbook/actions/workflows/ci.yml)

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![GPL3 License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
[![Ask Me Anything][ask-me-anything]][personal-page]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/stiliajohny/macos-ansible-playbook">
    <img src="https://raw.githubusercontent.com/stiliajohny/macos-ansible-playbook/main/.assets/logo.png" alt="Main Logo" width="80" height="80">
  </a>

  <h3 align="center">macos-ansible-playbook</h3>

  <p align="center">
    The "Mac Development Ansible Playbook" installs and configures software for web and software development on macOS using Ansible.
    <br />
    <a href="./README.md"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/stiliajohny/macos-ansible-playbook">View Demo</a>
    ·
    <a href="https://github.com/stiliajohny/macos-ansible-playbook/issues/new?labels=i%3A+bug&template=1-bug-report.md">Report Bug</a>
    ·
    <a href="https://github.com/stiliajohny/macos-ansible-playbook/issues/new?labels=i%3A+enhancement&template=2-feature-request.md">Request Feature</a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->

## Table of Contents

- [Table of Contents](#table-of-contents)
- [About The Project](#about-the-project)
  - [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Overriding Defaults](#overriding-defaults)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Acknowledgements](#acknowledgements)

<!-- ABOUT THE PROJECT -->

## About The Project

The "MacOS Ansible Playbook" is an open-source project that uses Ansible automation to install and configure software packages for web and software development on a Mac computer. The project includes a set of tasks that install and configure a range of applications, tools, and packages, including Homebrew, ChromeDriver, Docker, Firefox, Google Chrome, and Sublime Text, among others. Additionally, the playbook includes dotfiles that help configure various aspects of macOS for better performance and ease of use.

The "MacOS Ansible Playbook" is designed to be fully customizable and flexible, allowing users to add, remove or modify applications, packages, and configurations as needed. The playbook also includes detailed documentation that provides instructions for installing and using the playbook, as well as a full guide for a 100% from-scratch installation.

The project is maintained by Jeff Geerling, an author and consultant who specializes in Ansible and DevOps. It is continuously tested on GitHub Actions' macOS infrastructure, ensuring its reliability and accuracy.

### Built With

- Ansible
-

GETTING STARTED

## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.

- npm

```sh
npm install npm@latest -g
```

### Installation

1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):

   1. Run the following command to add Python 3 to your $PATH: `export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"`
   2. Upgrade Pip: `sudo pip3 install --upgrade pip`
   3. Install Ansible: `pip3 install ansible`

3. Clone or download this repository to your local drive.
4. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
5. Run `ansible-playbook main.yml --ask-become-pass` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

## Usage

### Overriding Defaults

Not everyone's development environment and preferred software configuration is the same.

You can override any of the defaults configured in `default.config.yml` by creating a `config.yml` file and setting the overrides in that file. For example, you can customize the installed packages and apps with something like:

```yaml
homebrew_installed_packages:
  - cowsay
  - git
  - go

mas_installed_apps:
  - { id: 443987910, name: "1Password" }
  - { id: 498486288, name: "Quick Resizer" }
  - { id: 557168941, name: "Tweetbot" }
  - { id: 497799835, name: "Xcode" }

composer_packages:
  - name: hirak/prestissimo
  - name: drush/drush
    version: "^8.1"

gem_packages:
  - name: bundler
    state: latest

npm_packages:
  - name: webpack

pip_packages:
  - name: mkdocs

configure_dock: true
dockitems_remove:
  - Launchpad
  - TV
dockitems_persist:
  - name: "Sublime Text"
    path: "/Applications/Sublime Text.app/"
    pos: 5
```

---

## Roadmap

See the [open issues](https://github.com/stiliajohny/macos-ansible-playbook/issues) for a list of proposed features (and known issues).

---

## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## License

Distributed under the License. See `LICENSE` for more information.

## Contact

John Stilia - john.stilia@iusearchbtw.blog

---

ACKNOWLEDGEMENTS -->

## Acknowledgements

- [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
- [Img Shields](https://shields.io)
- [Choose an Open Source License](https://choosealicense.com)
- [GitHub Pages](https://pages.github.com)

[contributors-shield]: https://img.shields.io/github/contributors/stiliajohny/macos-ansible-playbook.svg?style=for-the-badge
[contributors-url]: https://github.com/stiliajohny/macos-ansible-playbook/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/stiliajohny/macos-ansible-playbook.svg?style=for-the-badge
[forks-url]: https://github.com/stiliajohny/macos-ansible-playbook/network/members
[stars-shield]: https://img.shields.io/github/stars/stiliajohny/macos-ansible-playbook.svg?style=for-the-badge
[stars-url]: https://github.com/stiliajohny/macos-ansible-playbook/stargazers
[issues-shield]: https://img.shields.io/github/issues/stiliajohny/macos-ansible-playbook.svg?style=for-the-badge
[issues-url]: https://github.com/stiliajohny/macos-ansible-playbook/issues
[license-shield]: https://img.shields.io/github/license/stiliajohny/macos-ansible-playbook?style=for-the-badge
[license-url]: https://github.com/stiliajohny/macos-ansible-playbook/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/johnstilia/
[product-screenshot]: .assets/screenshot.png
[ask-me-anything]: https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg?style=for-the-badge
[personal-page]: https://github.com/stiliajohny
