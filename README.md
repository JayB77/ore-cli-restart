# ORE CLI

A command line interface for ORE cryptocurrency mining. This version will restart itself if an error occurs and halts the miner. I would suggest running the miner in a screen using the "Screen -S" command so it will continue to run even if the terminal is killed for some reason. Screen help can be found at https://help.ubuntu.com/community/Screen.

## Install

To install the CLI, use [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html):

```sh
cargo install ore-cli
```
### Edit the CLI Restart Command in mine.rs
Replace "your-cli-command-here" with something like: ore mine --cores 32 --priority-fee 10000
```sh
// Run the CLI command
        let command = "your-cli-command-here"; // Replace with your actual ore command 
        if let Err(cmd_err) = Command::new("sh")
            .arg("-c")
            .arg(command)
            .output()
        {
            eprintln!("Failed to execute command: {:?}", cmd_err);
        }
```

### Dependencies
If you run into issues during installation, please install the following dependencies for your operating system and try again:

#### Linux
```
sudo apt-get install openssl pkg-config libssl-dev
```

#### MacOS (using [Homebrew](https://brew.sh/))
```
brew install openssl pkg-config

# If you encounter issues with OpenSSL, you might need to set the following environment variables:
export PATH="/usr/local/opt/openssl/bin:$PATH"
export LDFLAGS="-L/usr/local/opt/openssl/lib"
export CPPFLAGS="-I/usr/local/opt/openssl/include"
```

#### Windows (using [Chocolatey](https://chocolatey.org/))
```
choco install openssl pkgconfiglite
```

## Build

To build the codebase from scratch, checkout the repo and use cargo to build:

```sh
cargo build --release
```

## Help

You can use the `-h` flag on any command to pull up a help menu with documentation:

```sh
ore -h
```
