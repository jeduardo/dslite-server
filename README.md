# DS-Lite Server

These scripts configure a [DS-Lite](https://www.rfc-editor.org/rfc/rfc6333) Linux server as an [AFTR](https://www.rfc-editor.org/rfc/rfc6333#section-6) relay.

## Deployment

Make sure that the script is executable:

```shell
chmod a+x ./dslite-server
```

## Usage

The script supports two actions: `start` and `stop`. The script needs to be run either as `root` or with `sudo`, as it uses privileged system binaries.
