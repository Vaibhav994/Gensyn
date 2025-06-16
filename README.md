# Gensyn Node
![image](https://github.com/user-attachments/assets/df22f5d7-7211-4bad-ac74-8b3957430cce)


## Download Mobaxterm to connect with VPS and run node
### 1️⃣ Download MobaXterm Application
* Open - [Download_Mobaxterm](https://mobaxterm.mobatek.net/download.html)
* Download free portable edition of Mobaxterm and extract and install it.
* Until it downloads, make a ssh key file using your local ubuntu

### 2️⃣ **SSH Key File**

* Open ubuntu and run this code
  
```
ssh-keygen -t rsa -f ~/.ssh/username -C root
```

* Change `username` after slash with your username that you want

* it will ask for password two times, can put any or just press `enter`
* it will give output like RSA something
* Open you file explorer and at bottom left you will see Linux -> ubuntu
* go to this path by opening folders `Ubuntu -> home -> your ubuntu folder (username that you created with) -> .ssh -> file named by your username that you changed above while creating ssh key, copy that file onto desktop (not the pub file)`

### 3️⃣ **Connect to VPS**
* Open Mobaxterm -> session from menu -> SSH -> Input you VPS IP address
![image](https://github.com/user-attachments/assets/7a8b4df3-7c66-458e-badf-22443cdc2dcc)

* Tick the specify username box and write `root`
* Advanced SSH settings below -> tick use private key -> click on notebook icon in front of it and select the file you saved on desktop -> press OK
![image](https://github.com/user-attachments/assets/c5601b96-9389-4e91-b33a-be06f516cce9)

  
* enter your password or press enter if you left it empty
* VPS is connected. continue with below codes
---

## Run Node

1️⃣ Installing dependencies 🛠

* Update System Packages
```
sudo apt-get update && sudo apt-get upgrade -y
```
* Install General Utilities and Tools
```
sudo apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

* Install **Python**
```
sudo apt-get install python3 python3-pip python3-venv python3-dev -y
```

* Install **Node Js**, **Yarn**, **NPM**
```
sudo apt-get update
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install -g yarn
```
```
curl -o- -L https://yarnpkg.com/install.sh | bash
```

* Setting **Path**
```
export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```
```
source ~/.bashrc
```


2️⃣ Checking installed **dependencies**

```
node -v
yarn -v
npm -v
python3 --version
```


3️⃣ Clone **Gensyn** Repository

```
git clone https://github.com/gensyn-ai/rl-swarm/
```


4️⃣ New screen in **VPS**

```
tmux
```


5️⃣ Get into the rl-swarm directory

```
cd rl-swarm
```

* Making new **Python Environment**
```
python3 -m venv .venv
source .venv/bin/activate
```

* Download the deepseek attached file from telegram
* In Mobaxterm left side panel -> you will see file structure -> go to rl-swarm -> hivemind_exp -> configs -> mac -> right click on the present file and delete it -> click on green upload icon (third icon from left just above) -> select the file you download and upload that, or drag and drop from desktop
  ![image](https://github.com/user-attachments/assets/a2970019-4404-45f5-be0b-989d1946444e)

* run the below codes


6️⃣ Run the swarm

```
./run_rl_swarm.sh
```

* Press `Y` when asked to connect with testnet
* Choose math a by pressing `a`
* Choose 1.5 by sending `1.5` 
* It will download dependencies and ask to login, wait for output like waiting for userjson something
* In Mobaxterm left side, click on the star icon and you will see you IP address, double click on it and it will create new tab -> input password and run below code to get gensyn login page

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

![image](https://github.com/user-attachments/assets/d50be148-dc05-435a-ae97-53b8e7daccd3)

* To go out of screen, Press `CTRL + B` and than press `D`
---

* Enter the **screen** again

```
tmux attach
```
---

## Save **swarm.pem** file
* In Mobaxterm -> left side panel, folder structure -> go to rl-swarm folder -> Right click on swarm.pem file and download -> save it somewhere safe

![image](https://github.com/user-attachments/assets/d3b5dbf4-cf97-4c78-9400-c0b381b30bae)

* You can run **Gensyn** Node run using this swarm.pem file by copying this file into rl-swarm folder after gensyn github repository clone is completed, just before 6️⃣th step. (When you are running model from scratch, rl-swarm won't have any swarm.pem file, it is created once you login through gmail on website.)
* If you need to run the same ORG_ID Gensyn node, need to save the swarm.pem file somehwere safe. 
---

## Check **Wins** and **Rewards** on Gensyn Dashboard

* Open - [Gensyn Dashboard](https://dashboard.gensyn.ai/)
* Login -> gmail account and will see **Wins** and **Reward** in some hours
* You can see the Nonde name, node ID and wallet address for your node on dashboard

![image](https://github.com/user-attachments/assets/fd67127c-aa4b-42f7-bdd7-54e5e902b5bd)

---

 **Done ✅**
