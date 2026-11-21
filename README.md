# cloudfail

Cloudflare can hide an origin server while older DNS records, public databases, and forgotten subdomains still expose clues. cloudfail checks these sources to help authorized testers assess whether a site's origin IP may be discoverable.

## Features

- Query DNSDumpster.com for DNS records associated with a target.
- Search the Crimeflare.com database for previously reported origin IPs.
- Test more than 2,500 common subdomains for additional DNS records.
- Route requests through Tor when the `--tor` option is enabled.

## Installation

Install Python 3 and the system packages required by the project:

```bash
sudo apt-get update
sudo apt-get install -y python3 python3-pip python3-setuptools tor
```

From the cloudfail project directory, install the Python dependencies:

```bash
python3 -m pip install -r requirements.txt
```

If Tor is needed for a scan, start the service before running cloudfail:

```bash
sudo service tor start
```

## Usage

Run a scan against a target domain:

```bash
python3 cloudfail.py --target example.com
```

Route the scan through Tor:

```bash
python3 cloudfail.py --target example.com --tor
```

**Use cloudfail only against systems you own or have explicit permission to test.** Results are not guaranteed, and a correctly configured Cloudflare deployment may leave no publicly discoverable origin address.

## License

cloudfail is licensed under the MIT License.

This project is based on [m0rtem/CloudFail](https://github.com/m0rtem/CloudFail). The original project is licensed under the MIT License, and this attribution is retained in accordance with that license.
