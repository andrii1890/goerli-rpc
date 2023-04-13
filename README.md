# ETH RPC node on Goerli network
 ***HTTP*** request will be available on: ***http://<YOUR_IP>:8545***
 
  ***WS*** request will be available on: ***ws://<YOUR_IP>:8546***
 
 Monitoring will be available without credentials on: ***http://<YOUR_IP>:3000***
 
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
    echo 'alias lighthouse_log="docker logs goerli-rpc-lighthouse-1 -f"' >> $HOME/.profile
    echo 'alias influxdb_log="docker logs goerli-rpc-influxdb-1 -f"' >> $HOME/.profile
    echo 'alias prometheus_log="docker logs goerli-rpc-prometheus-1 -f"' >> $HOME/.profile
    echo 'alias grafana_log="docker logs goerli-rpc-grafana-1 -f"' >> $HOME/.profile
    echo 'alias goerli_log="cd $HOME/goerli-rpc/ && docker compose logs -f"' >> $HOME/.profile
    source $HOME/.profile
    ```
    now you can simply find logs: geth_log, lighthouse_log, influxdb_log, prometheus_log, grafana_log, and all-in goerli_log 
### Also you can find your geth and lighthouse logs in Goerli Dashboard   
### Understanding Geth's Dashboard https://geth.ethereum.org/docs/monitoring/understanding-dashboards

### If Geth Dashboard doesn't work
Go to: CONFIGURATION > Data Sources > InfluxDB > Scroll to InfluxDB Details and find Database (it wiil be clear) write: geth > Save & test
![geth](https://user-images.githubusercontent.com/95629373/230673978-bf5174c0-d652-4306-b0c0-499f3f150778.png)

# You are free to make any changes in docker-compose.yml if you know what you do :wink:

