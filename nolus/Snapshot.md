# **Height:** `1262820`     **Size**: `21.8G`     **Pruning**: `nothing`     **Indexer**: `null`

#### Install dependencies

```bash
sudo apt update
sudo apt install lz4 -y
```

```bash
sudo systemctl stop nolusd

cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup 

nolusd tendermint unsafe-reset-all --home $HOME/.nolus --keep-addr-book 
wget http://185.202.223.85:7000/nolus1262820_06.03.2023.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.nolus

mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json 

sudo systemctl start nolusd
sudo journalctl -u nolusd -f --no-hostname -o cat
```
 
