# CFScanner - Python

The script is designed to scan Cloudflare's edge IPs and locate ones that are viable for use with v2ray/xray. It aims to identify edge IPs that are accessible and not blocked.

<!-- ## Description

An in-depth paragraph about your project and overview of use. -->

# Dependencies

* Linux
* Python (>=3.6)
* Libraries 
    - requests
    - pysocks

# Installing

* Install prerequisites
```bash
sudo apt update && sudo apt install python3-pip python3-venv git -y
```
* Clone the project
```bash
git clone https://github.com/MortezaBashsiz/CFScanner.git
```
* Change directory
```bash
cd CFScanner
```
* Install required packages
```bash
pip install -r ./requirements.txt
```
* create a config json file (e.g., myconfig.json) with the following content. replace the values with your own!
```json
{
	"id": "User's UUID",
	"Host": "Host address which is behind Cloudflare",
	"Port": "Port which you are using behind Cloudflare on your origin server",
	"path": "Websocket endpoint like api20",
	"serverName": "SNI",
   	"subnetsList": "https://raw.githubusercontent.com/MortezaBashsiz/CFScanner/main/bash/cf.local.iplist"
}
```

# Executing program

## **How to run**
* To run without providing a subnets (CIDRs) file and using 8 threads: 
```bash
python3 cfFindIP.py --threads 8 --config ./myconfig.json
```
* To run on a list of subnets (recommended). Each line
```bash
python3 cfFindIP.py --threads 8 --config ./myconfig.json --subnets ./mysubnets.selection
```
* To run with a minimum acceptable download speed (in KBps)
```bash
python3 cfFindIP.py --threads 8 --config ./myconfig.json --subnets ./mysubnets.selection --download-speed 100
```
* To run with a minimum acceptable download and upload speed (in KBps)
```bash
python3 cfFindIP.py --upload-test --threads 8 --config ./myconfig.json --subnets ./mysubnets.selection --download-speed 100 --upload-speed 25
```
* To run and try each IP multiple (3 in this case) times. An IP is marked ok if it passes all the tests.
```bash
python3 cfFindIP.py --upload-test --threads 8 --config ./myconfig.json --subnets ./mysubnets.selection --download-speed 100 --upload-speed 25 --tries 3
```


Each line of the subnets file must be a Cloudflare subnets in CIDR notation or a single IP:
```
1.0.0.0/24
108.162.218.0/24
108.162.236.0/22
162.158.8.0/21
162.158.60.0/24
162.158.82.12
...
```

<!-- ## **positional arguments:**
* **threads**: Number of threads to use for parallel computing
* **config-path**: The path to the config file. For confg file example, see [config.sample](https://github.com/tempookian/CFScanner/blob/python/python/config.sample)
* **subnets-path**: (optional) The path to the custom subnets file. each line should be in the form of ip.ip.ip.ip/subnet_mask. If not provided, the program will read the cidrs from asn lookup

## **keyword arguments:**
* **--min-dl-speed**: Minimum acceptable download speed in KBps (default = 50)

---

## **Results:**
The results will be stored in the results directory. Each line of the results files includes a Cloudflare edge ip together with the respective response time in milliseconds, e.g., 

```
153 104.16.126.37
154 104.21.47.40
154 104.18.38.111
157 104.18.38.38
159 104.16.126.42
159 104.17.223.179
...
```

Two files are stored for each (complete) run of the script
* interim results file (e.g., ``20230226_180502_interim_result.txt``)
    - Includes the unsorted intermediate results. Useful in case the run is not complete.  
* final results file (e.g., ``20230226_180502_final_result.txt``)
  * Includes the final sorted results. The results are sorted ascendingly based on the response time of the edge ips.  -->


<!-- ## Help

Any advise for common problems or issues.
```
command to run if program contains helper info
``` -->

# Authors

Contributors names and contact info

* [Tempookian](https://github.com/tempookian)  
* [Morteza Bashsiz](https://github.com/MortezaBashsiz/)

# Version History

* 0.1
    * Initial Release

# License


<!-- ## Acknowledgments

Inspiration, code snippets, etc.
* [awesome-readme](https://github.com/matiassingers/awesome-readme)
* [PurpleBooth](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
* [dbader](https://github.com/dbader/readme-template)
* [zenorocha](https://gist.github.com/zenorocha/4526327)
* [fvcproductions](https://gist.github.com/fvcproductions/1bfc2d4aecb01a834b46) -->
