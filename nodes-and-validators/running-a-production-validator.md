---
description: Getting a validator live is just the beginning
cover: ../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# Running a Validator

## Mainnet Setup and Tooling

Getting a Validator live is just the beginning. Running a Production Validator requires far more than the initial steps. Preparing your architecture for maximum uptime and redundancy falls outside the scope of this documentation, but a few of the bare-minimum requirements are:

* How will you handle chain upgrades?
  * consider: **Cosmovisor**
* How will you know your node is up?
  * consider: **Monitoring and Alerts**
* How will you mitigate DDOS attacks?
  * consider: **Sentry Nodes**
* How much storage will you need and how will you grow storage?

Answering these questions can be daunting, so there is some advice below.

#### Chain upgrades

In order to streamline chain upgrades and minimize downtime, you may want to set up [cosmovisor](setting-up-cosmovisor.md) to manage your node.

#### Backups

Backups of chain state are possible using the commands specified [here](https://hub.cosmos.network/main/gaia-tutorials/join-mainnet.html#export-state). If you are using a recent version of Cosmovisor, then the default configuration is that a state backup will be created before upgrades are applied. [This can be turned off using environment flags](https://docs.cosmos.network/master/run-node/cosmovisor.html#command-line-arguments-and-environment-variables).

Taking backups of the `.starsd/data` folder is important for quick recovery if required

#### Alerting and Monitoring

Alerting and monitoring is desirable as well - you are encouraged to explore solutions and find one that works for your setup. Prometheus is available out-of-the box, and there are a variety of open-source tools. Recommended reading:

* [https://medium.com/solar-labs-team/cosmos-how-to-monitoring-your-validator-892a46298722](https://medium.com/solar-labs-team/cosmos-how-to-monitoring-your-validator-892a46298722)
* [https://medium.com/simply-vc/cosmos-monitoring-and-alerting-for-validators-8e3f016c9567](https://medium.com/simply-vc/cosmos-monitoring-and-alerting-for-validators-8e3f016c9567)
* [https://chainflow.io/cosmos-validator-mission-control/](https://chainflow.io/cosmos-validator-mission-control/)
* [https://medium.com/cypher-core/cosmos-how-to-set-up-your-own-network-monitoring-dashboard-fe49c63a8271](https://medium.com/cypher-core/cosmos-how-to-set-up-your-own-network-monitoring-dashboard-fe49c63a8271)

And for real-time alerting, consider:

* [https://github.com/blockpane/tenderduty](https://github.com/blockpane/tenderduty)

**Simple setup using Grafana Cloud**

Using only the raw metrics endpoint provided by `starsd` you can get a working dashboard and alerting setup using Grafana Cloud. This means you don't have to run Grafana on the instance.

1. First, in `config.toml` enable Prometheus. The default metrics port will be `26660`
2. Download Prometheus - this is needed to ship logs to Grafana Cloud.
3. Create a `prometheus.yml` file with your [Grafana Cloud credentials](https://grafana.com/docs/grafana-cloud/reference/create-api-key/) in the Prometheus folder. You can get these via the Grafana UI. Click 'details' on the Prometheus card:

```
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: cosmops
    static_configs:
    - targets: ['localhost:26660']
      labels:
        group: 'cosmops'

remote_write:
  - url: https://your-grafana-cloud-endpoint/api/prom/push
    basic_auth:
      username: ID_HERE
      password: "API KEY HERE"
```

3\. Set up a service file, with `sudo nano /etc/systemd/system/prometheus.service`, replacing `<your-user>` and `<prometheus-folder>` with the location of Prometheus. This sets the Prometheus port to `6666`

```
[Unit]
Description=prometheus
After=network-online.target

[Service]
User=<your-user>
ExecStart=/home/<your-user>/<prometheus-folder>/prometheus --config.file=/home/<your-user>/<prometheus-folder>/prometheus.yml --web.listen-address=:6666 --storage.tsdb.path=/home/<your-user>/<prometheus-folder>/data
Restart=always
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
/etc/systemd/system/prometheus.service
```

4\. Enable and start the service.

```
sudo -S systemctl daemon-reload
sudo -S systemctl enable prometheus
sudo systemctl start prometheus
```

5\. Import a dashboard to your Grafana. Search for 'Cosmos Validator' to find several options. You should see logs arriving in the dashboard after a couple of minutes.

For more info:

* [https://grafana.com/docs/grafana-cloud/quickstart/noagent\_linuxnode/](https://grafana.com/docs/grafana-cloud/quickstart/noagent\_linuxnode/)
* [https://forum.cosmos.network/t/monitoring-alerting-for-your-validator/446/28](https://forum.cosmos.network/t/monitoring-alerting-for-your-validator/446/28)

#### Avoiding DDOS attacks

{% hint style="info" %}
If you are comfortable with server ops, you might want to build out a [Sentry Node Architecture](https://docs.tendermint.com/master/nodes/validators.html) validator to protect against DDOS attacks.
{% endhint %}

The current best practice for running mainnet nodes is a Sentry Node Architecture. There are various approaches, as [detailed here](https://medium.com/@kidinamoto/tech-choices-for-cosmos-validators-27c7242061ea). Some validators advocate co-locating all three nodes in virtual partitions on a single box, using Docker or other virtualization tools. However, if in doubt, just run each node on a different server.

Bear in mind that Sentries can have pruning turned on, as outlined [here](https://hub.cosmos.network/main/gaia-tutorials/join-mainnet.html#pruning-of-state). It is desirable, but not essential, to have pruning disabled on the validator node itself.

#### Managing storage

{% hint style="info" %}
If you are using a cloud services provider, you may want to mount `$HOME` on an externally mountable storage volume, as you may need to shuffle the data onto a larger storage device later. You can specify the `home` directory in most commands, or just use symlinks.
{% endhint %}

Disk space is likely to fill up, so having a plan for managing storage is key.

If you are running sentry nodes:

* 512GB storage for the full node will give you a lot of runway
* 256GB _each_ for the sentries with pruning should be sufficient

Managing backups is outside the scope of this documentation, but several validators keep public snapshots and backups.

#### Ballpark costs

To give you an idea of cost, on AWS EBS (other cloud providers are available, or you can run your own hardware), with two backups a day, this runs to roughly:

* $150 for 1TB
* $35 for 200GB
* Total cost: $220

What approach you take for this will depend on whether you are running on physical hardware co-located with you, running in a data centre, or running on virtualized hardware.

### Communication

It's extremely important to be vigilant in the monitoring of both your node(s) as well as the Stargaze validator ecosystem:

* Ensure you're alerted to all notifications on the #validator-announcements channel on the [Stargaze Discord Server](https://discord.gg/QeJWCrE)
* Watch for new governance votes and VOTE appropriately for you and your delegations
