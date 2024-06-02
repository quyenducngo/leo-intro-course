1. Setup Environment

Install Git and Rust

	1.	Install Git:
	•	Follow the instructions on the Git website to download and install Git for your operating system.
	2.	Install Rust:
	•	Follow the instructions on the Rust website to download and install Rust.

Note: After installation, if the git and rustc commands don’t work, try closing the current terminal window, opening a new one, and trying again.

Install Leo

	1.	Clone the leo repository:
 # Download the source code
git clone https://github.com/AleoHQ/leo
cd leo

	2.	Build and install the leo CLI:
 # Build and install
cargo install --path .

	3.	Verify the installation:
 leo
 	3.	For more details on how to use the leo CLI, check out the Leo Commands Guide.

Install snarkOS

	1.	Clone the snarkOS repository:
 git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS

	2.	[For Ubuntu users] Run the helper script to install dependencies:
 ./build_ubuntu.sh

 	3.	Install snarkOS:
  cargo install --path .

  	4.	Ensure ports are open:
	•	Make sure ports 4133/tcp and 3033/tcp are open on your router and OS firewall.
For more details on how to use the snarkOS CLI, check out the snarkOS Installation Guide.

Install Leo IDE Syntax Highlighting

Follow the guide here to set up syntax highlighting for Leo in your IDE.

Docker Pull for Leo

This is the development environment Docker image for the Aleo blockchain, which includes Leo, Rust, and Git installed.

	1.	Pull the Docker image:
 docker pull 0xaragondocker/leo_docker:latest

 	2.	Run Docker:
  docker run -it 0xaragondocker/leo_docker /bin/bash
