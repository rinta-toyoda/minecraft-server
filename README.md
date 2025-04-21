# Hosting Minecraft server with Docker and Ngrok on Linux PC
Easy way to host a minecraft server using ngrok and docker on linux pc for free (Java version).

## Requirements
- Download [docker](https://docs.docker.com/desktop/setup/install/linux/)
- Download [git](https://git-scm.com/downloads/linux)
- Download [brew](https://brew.sh/) (Optional)
- Download [task](https://taskfile.dev/installation/) (Optional)
- Make a [ngrok account](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://dashboard.ngrok.com/signup&ved=2ahUKEwjSmPyv7eOMAxUyR2wGHaw0DEQQFnoECAkQAQ&usg=AOvVaw0Eem619whOco8fyiLYYfC6) and add credit card information (required for using tcp option, but there will be no charges).

Make sure after you download docker, you run:
```
sudo usermod -aG docker $USER
```
And restart your pc.

## Procedures

### Step 1: Clone this repository
Clone this repository by using the command:
```
$ git clone https://github.com/rinta-toyoda/minecraft-server.git
```
on your terminal.

### Step 2: Adding NGROK_AUTHTOKEN
From your ngrok account, get NGROK_AUTHTOKEN. Open cloned repository and paste it into .env 's NGROK_AUTHTOKEN after "=".
```
NGROK_AUTHTOKEN=xxxxxxxxxxxxxxx
```

### Step 3: Changing server settings (optional)
If you want to change the minecraft version, memory, and difficulty, simply change .env's below parts:
```
VERSION=1.21.5          # Specify the Minecraft version here
MEMORY=4G               # Adjust memory allocation if needed
DIFFICULTY=2            # Adjust difficulty 0=Peaceful, 1=Easy, 2=Normal, 3=Hard    
```

If you want to enable whitelist, you can change
```
ENABLE_WHITELIST=false
```
to
```
ENABLE_WHITELIST=true
```
and you can add initial whitelist usernames like below:
```
WHITELIST=username1,username2,username3
```

You can also set admin users by writing usernames after OPS (make sure to uncomment it):
```
OPS=username1,username2,username3
```

### Step 4: Run server
All you got to do is run:
```
$ task
```
on your terminal.

If you don't have task command, run:
```
docker-compose up -d minecraft
```
and
```
docker-compose run --rm ngrok
```
instead.

### Step 5: Connect to server!!!
Go to minecraft multiplayer then type in the address part after tcp.
eg:
```
0.tcp.xx.ngrok.xx:xxx
```

Make sure that the version of the minecraft you're playing and the server's minecraft version are matching!


## Other useful commands:
- If you want to bring the server down (Server's save data will still persist):
```
$ task down
```
Don't worry if `task: Failed to run task "down": exit status 1` error occurs


- If you want to add whitelist user (add username to where username1 is):
```
$ task add-whitelist user=username1
```

- If you want to remove user from whitlist:
 ```
$ task remove-whitelist user=username1
```

- If you want to delete server data:
```
$ task remove-server
```

- If you want to see logs of minecraft server:
```
$ task logs
```
