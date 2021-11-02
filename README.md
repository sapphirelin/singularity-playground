# singularity-playground
install in Ubuntu 20.04
## Install system dependencies
singularity development tools & libraries
```
# Ensure repositories are up-to-date
sudo apt-get update
# Install debian packages for dependencies
sudo apt-get install -y \
    build-essential \
    libseccomp-dev \
    pkg-config \
    squashfs-tools \
    cryptsetup
```

## Install Go
latest go 1.17.2
```
export VERSION=1.17.2 OS=linux ARCH=amd64  # change this as you need

wget -O /tmp/go${VERSION}.${OS}-${ARCH}.tar.gz \
  https://dl.google.com/go/go${VERSION}.${OS}-${ARCH}.tar.gz
sudo tar -C /usr/local -xzf /tmp/go${VERSION}.${OS}-${ARCH}.tar.gz
```
add to PATH
```
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
```

## Install golangci-lint
for linting
```
curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin
```
add to PATH
```
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> ~/.bashrc
source ~/.bashrc
```

## Clone the repo
```
git clone https://github.com/sylabs/singularity.git
cd singularity
git checkout v3.9.0-rc.1
```

## Install SingularityCE

```
./mconfig
make -C builddir
sudo make -C builddir install
```

done.
```
singularity --version
```
