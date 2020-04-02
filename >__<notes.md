echo "export GOPATH=\$HOME/.go" >> ~/.bashrc
echo "export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin:\$HOME/.local/bin:\$HOME/.bin" >> ~/.bashrc
. ~/.bashrc

sudo apt install golang-go python3-pip python3-setuptools python3-slugify protobuf-compiler libpcap-dev libnetfilter-queue-dev git

go get github.com/golang/protobuf/protoc-gen-go
go get -u github.com/golang/dep/cmd/dep
cd $GOPATH/src/github.com/golang/dep
./install.sh
export PATH=$PATH:$GOPATH/bin
python3 -m pip install --user grpcio-tools
go get github.com/evilsocket/opensnitch
cd $GOPATH/src/github.com/evilsocket/opensnitch
make
sudo -H make install

## also had to update depends versions inui requirements to get it to compile 
