# DS-Lite Server

These scripts configure a [DS-Lite](https://www.rfc-editor.org/rfc/rfc6333) Linux server as an [AFTR](https://www.rfc-editor.org/rfc/rfc6333#section-6) relay.

## Deployment

Make sure that the script is executable:

```shell
chmod a+x ./dslite-server
```

## Configuration

The script reads its configuration from `/etc/default/dslite`. Inside this file, both the `LOCAL_HOST`, which will resolve to the machine's public IP, and the `REMOTE_HOST`, which will be resolve to the remote client's public IP, need to be specified. This is necessary as the AFTR tunnel needs to have the IPs for both the local and the remote host.

By the RFC, the server will always have the IP `192.0.0.1` and the network will always be `192.0.0.0/29`. These are the values used by default, but they can be changed by tweaking the values at `TUN_IP4` and `TUN_NET`.

The tunnel interface will be named `ip6tun0` by default, but it can be adjusted by changing `TUN_IFACE`.

The WAN interface will by default be named `eth0`, but it can be adjusted by changing `WAN_IFACE`.

The MTU will be assumed to be `1280` by default, but it can be adjusted by changing `MTU`.

This is a sample of a default `/etc/default/dslite` configuration tweaking only values required for this specific connection:

```shell
LOCAL_HOST=aftr.myservers.example
REMOTE_HOST=home.myservers.example
TUN_IFACE=ip6tun0
WAN_IFACE=ens5
```

## Usage

The script supports two actions: `start` and `stop`. The script needs to be run either as `root` or with `sudo`, as it uses privileged system binaries.
