# Gensyn Node

## Download Mobaxterm to connect with VPS and run node
### 1️⃣ Download MobaXterm Application
* Open - [Download_Mobaxterm](https://mobaxterm.mobatek.net/download.html)
* Download free portable edition of Mobaxterm and extract and install it
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


6️⃣ Run the swarm

```
./run_rl_swarm.sh
```

* It will download dependencies and ask to login, wait for output like waiting for userjson something
* In Mobaxterm left side, click on the star icon and you will see you IP address, double click on it and it will create new tab -> input password and run below code to get gensyn login page

👇 **Get link to login gensyn account via gmail**

```
npm install -g localtunnel
```

```
lt --port 3000
```

* Select the link with mouse and it will copy by itself, paste and login via gmail account
* after verifying code, go to the previous tab where code was running
* Save your ORG ID, which will show on screen for somewhat around 30 seconds
  
* Now It will prompt `Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]` Enter `N`

* Now It will prompt `>> Enter the name of the model you want to use in huggingface repo/name format, or press [Enter] to use the default model.`  press `Enter` & get defalut model:

* After this, you will see node name, node id in square brackets in the logs. can save them as well or you will find that in gensyn dashboard after log in. 

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

* You can run **Gensyn** Node run using this swarm.pem file by copying this file into rl-swarm folder after gensyn github repository clone is completed, just before 6️⃣th step (When you are running model from scratch, rl-swarm won't have any swarm.pem file, it is created once you login through gmail on website)
* If you need to run the same ORG_ID Gensyn node, need to save the swarm.pem file somehwere safe
---

## 📈 Update To new release of **Gensyn** Node

* Go to gensyn screen (Vps)

```
tmux attach
```

* Stop Node run by pressing `CTRL + C` button on gensyn screen

* Move to rl-swarm directory

```
cd rl-swarm
```

* Pull the latest release from Gensyn Repository

```
git switch main
git reset --hard
git clean -fd
git pull origin main
```

* Start the swarm Node 🚀

```
./run_rl_swarm.sh
```

* Now follow the steps from 6️⃣th Point from above to login and start the swarm node.
* To go out of screen, Press `CTRL + B` and than press `D`

---

## 🔄 Restart **Gensyn** Node

* Go to gensyn screen (Vps)

```
tmux attach
```

* Stop Node run by pressing `CTRL + C` button on gensyn screen

* Move to rl-swarm directory

```
cd rl-swarm
```

* Making new **Python Environment**
```
python3 -m venv .venv
source .venv/bin/activate
```


* Run the swarm

```
./run_rl_swarm.sh
```

* Now follow the steps from 6️⃣th Point from above to login and start the swarm node.
* To go out of screen, Press `CTRL + B` and than press `D`

---

## Check **Wins** and **Rewards** on Gensyn Dashboard

* Open - [Gensyn Dashboard](https://dashboard.gensyn.ai/)
* Login -> gmail account and will see **Wins** and **Reward** in some hours
* You can see the Node name and wallet address for your node on dashboard. You can find these in logs as well

![image](https://github.com/user-attachments/assets/fd67127c-aa4b-42f7-bdd7-54e5e902b5bd)

---
# Troubleshooting

⚠️ ValueError("Your setup doesn't support bf16/gpu.")

<img width="1260" height="178" alt="image" src="https://github.com/user-attachments/assets/68764d62-ef6a-4ca1-b641-c9abb9256cf3" />


```
pip install --force-reinstall transformers==4.51.3 trl==0.19.1
pip freeze
bash run_rl_swarm.sh
```



# 👇 Gswarm Role
Instructions to setup a swarm node monitoring telegram bot and earn **The Swarm** Discord role
* Gswarm Official Docs: [Link ](https://gswarm.dev/docs)

## 1️⃣ Install Gswarm
```bash
# Install Go:
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source .bash_profile
go version
```
```
go install github.com/Deep-Commit/gswarm/cmd/gswarm@latest
```

### Verify Installation
```
gswarm --version
```

## 2️⃣  Setup Telegram Bot

**1. Create a Telegram Bot:**
* Chat with [@BotFather](https://t.me/botfather) on Telegram
* Send `/newbot` and follow the instructions (Choose a name & username)
* Save the bot token provided

 
**2. Get Your Chat ID:**
* Start a chat with your new bot and send some messages to it
* Visit `https://api.telegram.org/botYOUR_BOT_TOKEN/getUpdates` in your browser
  * Replace `<YOUR_BOT_TOKEN>` with your actual bot token.
  * Ensure the word `bot` remains in the URL before the token.
* Find your chat ID in the response
* Example: If your bot token is `1234567890:ABCdefGHIjklMNOpqrsTUVwxyz`, visit:
```
https://api.telegram.org/bot1234567890:ABCdefGHIjklMNOpqrsTUVwxyz/getUpdates
```

* In your Browser, enable `Pretty-print` for better readability.

**Sample Response:**
```
{
  "ok": true,
  "result": [
    {
      "message": {
        "message_id": 2021,
        "from": {
          "id": 123456789,
          "is_bot": false,
          "first_name": "GSwarm",
          "username": "gswarm_user",
          "language_code": "en"
        },
        "chat": {
          "id": 123456789,
          "first_name": "GSwarm",
          "username": "gswarm_user",
          "type": "private"
        },
        "date": 1704067200,
        "text": "Hello bot!"
      }
    }
  ]
}
```
* **Extract the Chat ID**: Look for the `"chat":{"id":123456789}` field. In this example, the chat ID is `123456789`. This is your Telegram ID that the bot will use to send you notifications.

**Note:** If you get an empty result `{"ok":true,"result":[]}`, you may need to send a message to your bot first, then refresh the URL.


## 3️⃣  Run Gswarm Bot

```
gswarm
```

Run `gswarm` in your terminal now and follow the prompts to enter your bot token, chat ID, and EOA address
* You'll find **EOA address**  by logging in the [Gensyn Dashboard](https://dashboard.gensyn.ai/)


## 4️⃣ Linking Discord and Telegram
To link your Discord and Telegram accounts:

**1. Get the verification code:**
* Go to Discord in `#|swarm-link` channel
* Type `/link-telegram` (this gives you a code)


**2. Verify the code:**
* Go to your Telegram bot
* Type `/verify <code>` (replace `<code>` with the code you received)

This will link your Discord and Telegram accounts and you earn **The Swarm** role.


* **Note** Use `tmux` commands if you want to keep the bot running

---

# CodeAssist - AI Programming Assistant

CodeAssist is a completely private and local AI coding assistant, developed by Gensyn. It helps you practice programming problems and train a novel assistant to help you code.

Unlike typical code assistants, CodeAssist writes directly in your editor as you work. Every keystroke - whether you type, fix, delete, or leave its output untouched - becomes a learning signal. Over time, it adapts to your habits and style, acting more like an apprentice learning from your craft than a tool following commands.

[Docs](https://docs.gensyn.ai/testnet/codeassist) | [Tutorial](https://docs.gensyn.ai/testnet/codeassist/using-codeassist) | [Leaderboard](https://dashboard.gensyn.ai/?application=CodeAssist)

# Installation

Get started with installing CodeAssist.

## Docker

Install [Docker](https://docs.docker.com/engine/install/) on your system, according to the instructions for your machine.

```bash
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null


sudo apt update
apt install docker.io
sudo apt install docker-compose-plugin

# Test Docker
sudo docker run hello-world
sudo systemctl enable docker
sudo systemctl restart docker
```

## Python

Python is required to run the main script that handles your environment. We require a version no older than 3.10.

```
sudo apt install -y python3.12 python3.12-venv python3.12-dev python3.12-distutils python3-pip  
```

## UV

UV is required to manage the dependencies of the main script. It can be installed with the following steps:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

# Downloading the Code

Clone the CodeAssist repository:

```bash
git clone https://github.com/gensyn-ai/codeassist.git
cd codeassist
```

# Running

To run CodeAssist, execute the following command:

```bash
uv run run.py
```

## HuggingFace Token

To start CodeAssist, you will need to have a HuggingFace token. Follow [these instructions](https://huggingface.co/docs/hub/en/security-tokens) and generate a token with `Write` access.

## Web UI

After the script is running, your browser should open automatically but if it doesn't, open a window and go to [localhost:3000](http://localhost:3000) to open CodeAssist (If you are using WSL, open new terminal and run below command)
```
npm install -g localtunnel
```

```
lt --port 3000
```
Open the link in browser and wait for it to load.

When the web UI loads, you'll see a login modal where you can log in with email (which sends a one-time passcode) or with Google.

Once logged in, you can select Easy, Medium, or Hard problems from the sidebar. CodeAssist will begin recording an episode. Every click, keystroke, edit, or deletion is logged as training feedback.

When you stop typing, CodeAssist takes initiative. It writes directly into your file without any pop-ups or confirmations. Whether you accept, modify, or remove its edits, each interaction contributes to the model’s understanding of your preferences.

## Training

CodeAssist continuously records your interactions while the web UI is running. To complete an episode and train your model, press `Ctrl+C` in the terminal where CodeAssist is running.

You do not need to successfully solve a LeetCode problem to train the model. You can stop recording the episode by leaving the CodeAssist web UI, returning to the terminal CodeAssist is running in, and using the `ctrl+c` command to start training.

After training completes (which takes a few minutes depending on your system), you can restart CodeAssist to use your updated model trained on your most recent episode.

---

 **Done ✅**

