water
==============

Quick setup of an Osmosis database

- create your instance
  - I'm using `ami-a6926dce` and `c3.4xlarge` for now
- `sudo su && cd ~/`
- `apt-get install -y git make`
- `git clone https://github.com/osmlab/water.git`
- `cd water`
- `sh` `<your instance size>.install.sh`
    - `c3.4xlarge.install.sh`
    - `i2.xlarge.install.sh`
- download your pbf
- optionally filter data, etc..
    - `./osmosis/bin/osmosis --read-pbf-fast <pbf file> --tf accept-ways highway=* --used-node --write-pbf <new pbf file>`
- import into postgres
    - `JAVACMD_OPTIONS="-Djava.io.tmpdir=/mnt/data/tmp -Xmx29G" ./osmosis/bin/osmosis --read-pbf-fast <pbf file> --write-pgsql user="postgres" nodeLocationStoreType="InMemory"`
