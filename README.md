# minecraft-server
Easy way to host a minecraft server using ngrok and docker on linux pc for free.

## Step 1: Downloading Docker
Download [docker](https://docs.docker.com/desktop/setup/install/linux/)

## Step 2: Making ngrok account
Make a [ngrok account](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://dashboard.ngrok.com/signup&ved=2ahUKEwjSmPyv7eOMAxUyR2wGHaw0DEQQFnoECAkQAQ&usg=AOvVaw0Eem619whOco8fyiLYYfC6) and add credit card information (required for using tcp option, but there will be no charges).

## Step 3: Downloadin git
Download [git](https://git-scm.com/downloads/linux)

## Step 4: Clone this repository
Clone this repository by using the command:
```
git clone https://github.com/rinta-toyoda/minecraft-server.git
```

## Step 5: Adding NGROK_AUTHTOKEN
From your ngrok account, copy NGROK_AUTHTOKEN and paste it into docker-compose.yaml 's NGROK_AUTHTOKEN after "=" on your pc (into the cloned repository).

## Step 6: Run server
Run below 2 commands to run server (if they don't work, add sudo at the front):
1) Start minecraft server
```
docker-compose up -d minecraft
```

2) Make a tunnel with ngrok
```
docker-compose run --rm ngrok
```
Server address will be shown like :
```
Forwarding                    tcp://0.tcp.xx.ngrok.xx:xxx -> localhost:25565   
```

## Step 7: Connect to server!!!
Go to minecraft multiplayer then type in the address part after tcp.
eg)
```
0.tcp.xx.ngrok.xx:xxx
```

Make sure that the versions are matching
