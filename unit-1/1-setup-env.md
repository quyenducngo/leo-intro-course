# 1. Setup Environment

## Install Git and Rust

1. **Install [Git](https://git-scm.com/downloads)**
	- Follow the instructions on the Git website to download and install Git for your operating system.
2. **Install [Rust](https://www.rust-lang.org/tools/install)**
	- Follow the instructions on the Rust website to download and install Rust.

Note: After installation, if your `git` and `rustc` command don't work, try closing the current terminal window, opening a new one, and try again.

## Install leo

1. **Clone the `leo` repository:**
```bash
# Download the source code
git clone https://github.com/AleoHQ/leo
cd leo
```

2. **Build and install the `leo` CLI:**
```bash
# Build and install
cargo install --path .
```

3. **Verify the installation:**
```bash
# To use leo
leo
```


For more details about how to use `leo` CLI, check out the [Leo Commands Guide.](https://developer.aleo.org/leo/commands)

## Install snarkOS

1. **Clone the `snarkOS` repository:**
```bash
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS
```

2. **[For Ubuntu users] Run the helper script to install dependencies:**
```bash
./build_ubuntu.sh
```

3. **Install snarkOS**:
```
cargo install --path .
```

4. **Ensure ports are open**:
```
Make sure ports 4133/tcp and 3033/tcp are open on your router and OS firewall.
```


For more details about how to use `snarkOS` CLI, check out the [snarkOS Installation Guide.](https://developer.aleo.org/testnet/getting_started/installation/#22-installation).

## Install `leo` IDE Syntax Highlighting:

Follow the guide [here](https://developer.aleo.org/leo/installation#3-ide-syntax-highlighting) to set up syntax highlighting for Leo in your IDE.

## Docker pull leo

This is the development environment Docker image for the Aleo blockchain, which includes Leo, Rust, and Git installed.

Pull docker image
```
docker pull 0xaragondocker/leo_docker:latest
```

Run docker
```
docker run -it 0xaragondocker/leo_docker /bin/bash
```
