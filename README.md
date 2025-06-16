# Gensyn Node


### Download Mobxterm to connect with VPS and run node

* Open - [Download_Mobxterm](https://mobaxterm.mobatek.net/download.html)
* Download free portable edition of Mobxterm and extract and install it.
* Until it downloads, make a ssh key file using your local ubuntu

### **SSH Key File**

* Open ubuntu and run this code
  
```
ssh-keygen -t rsa -f ~/.ssh/username -C root
```
* Change `username` after slash with your username that you want

* it will ask for password two times, can put any or just press `enter`
* it will give output like RSA something
* Open you file explorer and at bottom left you will see Linux -> ubuntu
* go to this path by opening folders `Ubuntu -> home -> your ubuntu folder (username that you created with) -> .ssh -> file named by your username that you changed above while creating ssh key, copy that file onto desktop (not the pub file)`

### **Connect to VPS**
* Open Mobxterm -> session from menu -> SSH -> Input you VPS IP address
* Tick the specify username box and write root
* Advanced SSH settings below -> tick use private key -> click on notebook icon in front of it and select the file you saved on desktop -> press OK
* enter your password or press enter if you left it empty
* VPS is connected. continue with below codes

### Run Node

1️⃣ Installing dependencies 🛠
```
sudo apt-get update && sudo apt-get upgrade -y
```
```
sudo apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
```
sudo apt-get install python3 python3-pip python3-venv python3-dev -y
```
```
sudo apt-get update
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install -g yarn
```
```
curl -o- -L https://yarnpkg.com/install.sh | bash
```
```
export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```
```
source ~/.bashrc
```


2️⃣ Checking libraries

```
node -v
yarn -v
npm -v
python3 --version
```


3️⃣ Cloning Gensyn Repository

```
git clone https://github.com/gensyn-ai/rl-swarm/
```


4️⃣ New screen

```
tmux
```


5️⃣ Changing directory

```
cd rl-swarm
```

```
python3 -m venv .venv
source .venv/bin/activate
```

* Download the deepseek attached file from telegram
* In Mobxterm left side panel -> you will see file structure -> go to rl-swarm -> hivemind_exp -> configs -> mac -> right click on the present file and delete it -> click on green upload icon (third icon from left just above) -> select the file you download and upload that, or drag and drop from desktop
* run the below codes


6️⃣ Run gensyn node

```
./run_rl_swarm.sh
```

* Press `Y` when asked to connect with testnet
* Choose math a by pressing `a`
* Choose 1.5 by sending `1.5` 
* It will download dependencies and ask to login, wait for output like waiting for userjson something
* In Mobxterm left side, click on the star icon and you will see you IP address, double click on it and it will create new tab -> input password and run below code to get gensyn login page

👇 **Get link to login gensyn account via gmail**

```
npm install -g localtunnel
```

```
lt --port 3000
```

* Select the link with mouse and it will ciopy by itself, paste and login via gmail account
* after verifying code, go to the previous tab where code was running
* Save your ORG ID, which will show on screen for somewhat around 30 seconds
* after sometime, it will ask for huggingface -> press `n` and done, wait for it to start and everything will work.

 **Done ✅**
