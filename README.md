# Touist webservice

This is a tool designed to run touist commands from the web

## Installation

Simply run the following script:

```bash
# init
sudo apt update
sudo apt install opam golang-go
opam init
opam install menhir minisat jbuilder re
eval $(opam env)
export GOPATH=~/go 
mkdir ~/go
mkdir ~/go/bin
export GOBIN=$GOPATH/bin

# dl
mkdir webservice
cd webservice
git clone https://github.com/Uriopass/touist
git clone https://github.com/hintikkasworld/touist_webservice
cd touist

# build touist
jbuilder build
jbuilder install
cd ..

# build go webservice
cd touist_webservice
go get ./...
go build -o main
cp main ../
cd ..

# setup runner
echo "nohup ./main &" > rungoserv.sh
chmod +x rungoserv.sh
```

## Port

You may change the port used at the end of the main function, default is 7015.
