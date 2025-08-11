# elastic-threat-hunting-workshop

# install docker
```
wget https://raw.githubusercontent.com/miko550/mikoscript/main/getdockerV2.sh -O getdocker.sh && bash getdocker.sh
```

## Setup elastic stack
```
wget "https://www.dropbox.com/scl/fi/mycn3p00npt360o22n7cy/elastic-workshop.tar.gz?rlkey=4qgk9kw9lze828oo4cvhu7c2j&e=1&st=831lmiro&dl=1"
tar -xvzf elastic-workshop.tar.gz
cd elastic-workshop
docker volume create elastic-workshop_elasticsearch
sudo cp -a elasticsearch_data/* /var/lib/docker/volumes/elastic-workshop_elasticsearch/_data/
sudo chown -R 1000:1000 /var/lib/docker/volumes/elastic-workshop_elasticsearch/_data/
docker compose up -d
```

## Ingest dataset
```
cd logs
apt install python3.11-venv
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 ingest <dateset.ndjson>
```
## Access elastic and start hunting
1. Open browser and navigate to http://<IP>:5601
2. Use Credential elastic:elastic@hunter2025
