# Shentu-2.2

#Shentu Mainnet


1/ Cập nhật phiên bản mới:

    sudo apt update && sudo apt upgrade -y

2/ Bổ sung package:

    sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential git make ncdu -y

3/ Cài đặt Golang:

    ver="1.19.3" 
    cd $HOME 
    wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" 


    sudo rm -rf /usr/local/go 
    sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" 
    rm "go$ver.linux-amd64.tar.gz"

Chuyển thư mục Golang:

    echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
    source $HOME/.bash_profile

Kiểm tra phiên bản:

    go version
    
4/ Tải về bộ cài đặt node:

    cd $HOME
    git clone https://github.com/certikfoundation/shentu.git 
    cd shentu 
    git checkout v2.7.1
    make install
    
5/ Thông tin node:

    shentud init node --chain-id shentu-2.2
    
Sheet:

    shentud keys add wallet
    
    shentud keys add wallet --recover
    
    shentud tx slashing unjail --from wallet --chain-id shentu-2.2 --gas-prices 0.001uctk --gas-adjustment 1.5 --gas auto -y
    
    shentud tx distribution withdraw-rewards $(shentud keys show wallet --bech val -a) --commission --from wallet --chain-id shentu-2.2 --gas-prices 0.001uctk --gas-adjustment 1.5 --gas auto -y 
    
    shentud tx staking delegate $(shentud keys show wallet --bech val -a) 1000000uctk --from wallet --chain-id shentu-2.2 --gas-prices 0.001uctk --gas-adjustment 1.5 --gas auto -y 
    
