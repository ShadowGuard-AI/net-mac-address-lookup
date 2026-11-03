![Banner](banner.png)

# net-mac-address-lookup
Lookup vendor information for a given MAC address using a public MAC address vendor database. Focused on basic network operations.

## Install
`git clone https://github.com/ShadowGuard-AI/net-mac-address-lookup`
`pip install -r requirements.txt`

## Usage
`python3 main.py MAC_ADDRESS [-v]`

## Parameters
- `-h`: Show help message and exit
- `mac_address`: The MAC address to lookup (e.g., 00:1A:2B:3C:4D:5E). Required. Must be six colon separated two character hex octets.
- `-v, --verbose`: Enable verbose logging (DEBUG level).

## Verified behavior
- `python3 main.py --help` matches the parameter list above, and `python3 -m py_compile main.py` passes. A missing address is rejected by argparse with exit 2, and an invalid format prints "Invalid MAC address format" and exits 1.
- A live vendor lookup was not run in this wave: the lookup contacts macvendors.co, which is outside this wave's allowed network hosts, so no live vendor result is claimed here.
- Limits, read from the code: the request sets no timeout, so a slow or silent API host can hang the lookup. Only the company field from the API answer is printed. A failed lookup and a completed lookup with no answer both print "Vendor information not found." and exit 0, so a script cannot tell a dead API from an unknown vendor without reading the log lines.

## License
See LICENSE.
