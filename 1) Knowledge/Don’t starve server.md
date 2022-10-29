’t starve server

KU_snvhg2Y9

[Google Cloud Platform](https://accounts.google.com/ServiceLogin?service=cloudconsole&passive=1209600&osid=1&continue=https://console.cloud.google.com/compute/instancesDetail/zones/europe-west1-b/instances/dontstarve?project%3Dgeardev-prod&followup=https://console.cloud.google.com/compute/instancesDetail/zones/europe-west1-b/instances/dontstarve?project%3Dgeardev-prod)

[Steam Community :: ToNiO :: Guides](https://steamcommunity.com/id/ToNiO44/myworkshopfiles/?section=guides&appid=322330)

```other
sudo dpkg --add-architecture i386
sudo apt-get update
sudo sudo apt-get install lib32gcc1 lib32stdc++6 libcurl4-gnutls-dev:i386 screen
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar -xvzf steamcmd_linux.tar.gz
mkdir server_dst

./steamcmd.sh
> login anonymous
> force_install_dir /home/rudolf/server_dst
> app_update 343050 validate
> quit

echo "cd /home/rudolf/server_dst/bin" >> start.sh
echo "./dontstarve_dedicated_server_nullrenderer -console -cluster MyDediServer -shard Master" >> start.sh
chmod +x start.sh

# Update
cd steam
./steamcmd.sh
> login anonymous
> force_install_dir /home/rudolf/server_dst
> app_update 343050
> quit
```

Start for the first time with `./start.sh` then kill it again. You will have a new directory at `~/.klei` that can be used to upload new servers.

```other
rm -r .klei/DoNotStarveTogether/MyDediServer/Master .klei/DoNotStarveTogether/MyDediServer/Caves
mv MyDediServer/* .klei/DoNotStarveTogether/MyDediServer/
```

To start:

```other
screen -S "Cave" ./cave.sh 
screen -S "Main" ./main.sh
```

To reattach:

`screen -r`

```other
cat .klei/DoNotStarveTogether/MyDediServer/cluster.ini
zip -r backup-2021-01-23 .klei/DoNotStarveTogether/MyDediServer/
```

```other
vi server_dst/mods/dedicated_server_mods_setup.lua
```

[Steam Community :: Don't Starve Together](https://steamcommunity.com/app/322330/workshop/)



