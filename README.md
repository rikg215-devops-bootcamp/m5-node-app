# M5-Node-App

## A simple app deployment on a Digital Ocean

### "Cloud Basics"

### EXERCISE 1: Package NodeJS App

Commands used:

```bash
cd app/ # switch to directory where package.json is located
npm pack # package application into tarball to enable easy transfer
```

### EXERCISE 2: Create a new server

All UI work. I have since deleted my Digital Ocean account. I am hoping I am recalling most of the UI steps from memory. I created a droplet with the smallest usage. For SSH access I generated an SSH key. I ran `ssh-keygenk -t rsa` I entered the key name as `~/.ssh/digi-ocean`. I then entered the public key into digital ocean and associated it with the droplet. I created a basic firewall that allowed ssh access (port 22 tcp) from my public IP and added the newly created droplet to it. 

### EXERCISE 3: Prepare server to run Node App

If my memory serves me correctly..Digital ocean gives you root access from the start so no need for sudo.

Commands used:

```bash
apt update
apt install npm
apt install nodejs
```

### EXERCISE 4: Copy App

Commands used:

```bash
scp bootcamp-node-project-1.0.0.tgz root@<DIGITAL-OCEAN-DROPLET-IP>:/root/ # Ran from inside of app/ folder
```

### EXERCISE 5: Run Node App

Commands used:

```bash
tar -xf bootcamp-node-project-1.0.0.tgz
cd package/
npm install
node ./server.js &
```

Command output:

`app listening on port 3000!`

### EXERCISE 6: Access from browser - configure firewall

More UI work. I went into firewall settings and added a new inbound rule for port 3000 from my home public IP. 

Tested via `<DROPLET-IP>:3000`
