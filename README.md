# ETH RPC node on Goerli network
 ***HTTP*** request will be available on: <YOUR_IP>:8545
 
  ***WS*** request will be available on: <YOUR_IP>:8546
 
 Monitoring will be available without credentials on: <YOUR_IP>:3000
 
 Grafana has 3 dashboard: geth dashboard, lighthouse dashboard, and goerli dashboard (last simple all-in)

 RECOMMENDATION:
 ***configure please your firewall rules (block all income to port 8545,8546,8086,3000 and use whitelist to access to your rpc, more about that can be found:   https://github.com/chaifeng/ufw-docker)***
 
## Following parameters:
- 4-CPU
- 8-GBRAM
- 400-GBSSD

## First Step
- **Install docker and docker compose**
    ```
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
    
    docker version && docker compose version
    ```

- **Run Docker as a non-root user**
    ```
    sudo usermod -aG docker <your_user>
    ```

### Relogin to your server to take effect from usermod !!!

## Second Step 
- **Clone this repo to your server, navigate to goerli-rpc folder and spin up all docker containers**
    ```
    git clone https://github.com/andrii1890/goerli-rpc.git
    cd goerli-rpc
    docker compose up -d
    ```

## Third step
- **Add alias for docker logs**
    ```
    echo "#Goerli Alias" >> $HOME/.profile
    echo 'alias geth_log="docker logs goerli-rpc-geth-1 -f"' >> $HOME/.profile
    echo 'alias lighthouse_logs="docker logs goerli-rpc-lighthouse-1 -f"' >> $HOME/.profile
    echo 'alias influxdb_logs="docker logs goerli-rpc-influxdb-1 -f"' >> $HOME/.profile
    echo 'alias prometheus_logs="docker logs goerli-rpc-prometheus-1 -f"' >> $HOME/.profile
    echo 'alias grafana_logs="docker logs goerli-rpc-grafana-1 -f"' >> $HOME/.profile
    echo 'alias goerli_log="cd $HOME/goerli-rpc/ && docker compose logs -f"' >> $HOME/.profile
    source $HOME/.profile
    ```


# You are free to make any changes in docker-compose.yml if you know what you do :wink:

