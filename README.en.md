[简体中文](https://github.com/QingdaoU/OnlineJudgeDeploy/blob/2.0/README.md) | English

## Environmental preparation (Linux)

+ System: Ubuntu 18.04 LTS

1. Install the necessary dependencies

    ```bash
    sudo apt-get update
    sudo apt-get install -y vim python3-pip curl git
    pip3 install --upgrade pip -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
    pip3 install docker-compose -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
    ```

2. Install Docker

    Install using script: `sudo curl -sSL get.docker.com | sh`

    Other installation methods: [https://docs.docker.com/install/](https://docs.docker.com/install/)

## Install

1. Please select a location with some surplus disk space and run the following command:

    ```bash
    git clone https://github.com/PUANEY/OnlineJudgeDeploy.git && cd OnlineJudgeDeploy
    ```

2. Start service

    ```bash
    docker-compose up -d
    ```

According to the network speed, the setup can be completed automatically in about 5 to 30 minutes without manual intervention.

Wait for the command execution to complete, and then run `docker ps -a`. When you see that the status of all the containers does not have `unhealthy` or `Exited (x) xxx`, it means OnlineJudge has started successfully.

3. Replace frontEnd files
 * By typing `cd OnlineJudgeFE && npm run build` and get a dist folder or downloading directly by opening the `https://github.com/PUANEY/OnlineJudgeFE/releases/download/oj1.0/dist.zip`。
 * Change directory: `cd OnlineJudgeDeploy && cd data && cd backend`.
 * Replace the dist folder.
 * Restart backend：`docker restart jhoj-backend`.

Access the server's HTTP 80 port or HTTPS 443 port through a browser, and you can start using it. The background management path is `/admin`, the super administrator user name automatically added during the installation process is `root`, and the password is `rootroot`. **If you log in successfully, please change your account password immediately.**.
