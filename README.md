<img src="https://skynet-network.org/images/2021/09/10/skynet_logo_01.png" width="100">

# Skynet Docker Container
https://skynet-network.org/

## Configuration
Required configuration:
* Publish network port via `-p 9999:9999`
* Bind mounting a host plot dir in the container to `/plots`  (e.g. `-v /path/to/hdd/storage/:/plots`)
* Bind mounting a host config dir in the container to `/root/.skynet`  (e.g. `-v /path/to/storage/:/root/.skynet`)
* Bind mounting a host config dir in the container to `/root/.skynet_keys`  (e.g. `-v /path/to/storage/:/root/.skynet_keys`)
* Set initial `skynet keys add` method:
  * Manual input from docker shell via `-e KEYS=type` (recommended)
  * Copy from existing farmer via `-e KEYS=copy` and `-e CA=/path/to/mainnet/config/ssl/ca/` 
  * Add key from mnemonic text file via `-e KEYS=/path/to/mnemonic.txt`
  * Generate new keys (default)

Optional configuration:
* Pass multiple plot directories via PATH-style colon-separated directories (.e.g. `-e plots_dir=/plots/01:/plots/02:/plots/03`)
* Set desired time zone via environment (e.g. `-e TZ=Europe/Berlin`)

On first start with recommended `-e KEYS=type`:
* Open docker shell `docker exec -it <containerid> sh`
* Enter `skynet keys add`
* Paste space-separated mnemonic words
* Restart docker cotainer
* Enter `skynet wallet show`
* Press `S` to skip restore from backup

## Operation
* Open docker shell `docker exec -it <containerid> sh`
* Check synchronization `skynet show -s -c`
* Check farming `skynet farm summary`
* Check balance `skynet wallet show` 
