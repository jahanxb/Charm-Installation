# README: Installing Charm Crypto on WSL (Ubuntu)

This guide provides step-by-step instructions on setting up the Charm Crypto library on a Windows Subsystem for Linux (WSL) environment running Ubuntu 20.04 or 22.04.

## Prerequisites

- Windows 10 or later.
- Administrative privileges to install WSL.

## Step 1: Install WSL and Ubuntu
----------------------------------

1. **List available WSL distributions**:
   ```bash
   wsl --list --online
   ```

2. **Install Ubuntu 20.04**:
   ```bash
   wsl --install -d Ubuntu-20.04
   ```
   Alternatively, you can choose Ubuntu 22.04:
   ```bash
   wsl --install -d Ubuntu-22.04
   ```

3. **Launch Ubuntu**:
   After installation, launch Ubuntu from the Start menu or by typing `wsl` in the command line.

4. **Switch to the root user**:
   ```bash
   sudo su
   ```
   Enter the password you've set up during the Ubuntu installation.

## Step 2: Install Basic Development Tools
------------------------------------------

To build and run Charm, you need several development tools and libraries. Install them with the following commands:

```bash
# Update package list
apt update

# Install required packages
apt install -y gcc make wget python3 python3-pip python3-dev libssl-dev libgmp-dev bison flex
```

## Step 3: Install PBC Library
------------------------------

Charm depends on the PBC (Pairing-Based Cryptography) library. Download and install it with the following commands:

```bash
# Download PBC source
wget https://crypto.stanford.edu/pbc/files/pbc-0.5.14.tar.gz

# Extract the archive
tar -xvzf pbc-0.5.14.tar.gz

# Navigate to the extracted directory
cd pbc-0.5.14

# Configure and install PBC
./configure
make
make install
```

## Step 4: Install Jupyter Notebook
-----------------------------------

To use Charm with Jupyter Notebooks, you need to install Jupyter. Follow these steps:

```bash
# Install Jupyter Notebook
apt install jupyter-notebook

```


## Step 5: Install Charm Crypto
-------------------------------

Now that all dependencies are ready, you can clone and install Charm Crypto:

1. **Clone the Charm repository**:
   ```bash
   git clone https://github.com/JHUISI/charm.git
   ```

2. **Navigate to the Charm directory**:
   ```bash
   cd charm
   ```

3. **Configure the build**:
   ```bash
   ./configure.sh
   ```

   You should see an output similar to this:
   ```
      root@Lilly:~/charm# ./configure.sh
    Install prefix    /usr/local
    data directory    /usr/local/share/charm
    binary directory  /usr/local/bin
    library directory /usr/local/lib
    config directory  /usr/local/etc
    Source path       /root/charm
    CFLAGS            -O2 -g
    CHARM_CFLAGS       -m64 -Wall -Wundef -Wwrite-strings -Wmissing-prototypes  -fstack-protector-all -Wendif-labels -Wmissing-include-dirs -Wempty-body -Wnested-externs -Wformat-security -Wformat-y2k -Winit-self -Wignored-qualifiers -Wold-style-declaration -Wold-style-definition -Wtype-limits
    LDFLAGS           -m64
    make              make
    python            /usr/bin/python3
    python-config     /usr/bin/python3-config
    build_ext options build_ext
    install           install
    host CPU          x86_64
    wget              /usr/bin/wget
    gprof enabled     no
    profiler          no
    static build      no
    -Werror enabled   no
    integer module    yes
    ecc module        yes
    pairing module    yes
    disable benchmark no
    libm found        yes
    libgmp found      yes
    libpbc found      yes
    libcrypto found   yes
    Documentation     no
   ...
   ```

4. **Compile and install Charm**:
   ```bash
   make
   make install
   ```

## Step 6: Running Jupyter Notebook
-----------------------------------

After installing Charm, you can start a Jupyter Notebook to use Charm in a notebook environment:

```bash
jupyter-notebook
```

This command will launch a Jupyter Notebook server and open it in your default web browser. Follow the link provided in the terminal, which will look something like this:
```
http://127.0.0.1:8888/?token=your/token
```

## Step 7: Verify Charm Installation with a Custom Notebook
-----------------------------------------------------------

To verify that Charm is installed correctly, you can use a custom Jupyter Notebook. Download the `crypto_assignment.ipynb` file from the GitHub repository and run it in your Jupyter Notebook environment.

## Troubleshooting
------------------

- Ensure all dependencies are properly installed.
- Check if the `pbc` and `charm` libraries are correctly linked.
- Verify Python paths and library paths if you encounter issues during the build.

## Additional Dependencies
--------------------------

If additional dependencies are required for your specific use case, they can be installed using `apt` or `pip` as demonstrated above. Update this README accordingly with any additional steps you take.

## Conclusion
-------------

You have successfully installed Charm Crypto on your WSL Ubuntu environment. Now, you can explore and use the Charm library for your cryptographic applications.


Feel free to add more dependencies and enhance this README as needed.

