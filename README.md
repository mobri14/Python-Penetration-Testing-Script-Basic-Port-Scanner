# Python-Penetration-Testing-Script-Basic-Port-Scanner
Python Penetration Testing Script: Basic Port Scanner
```pyhton
import socket
from datetime import datetime

def scan_ports(target, start_port=1, end_port=1024):
    """
    Perform a basic port scan on a target host.

    Args:
        target (str): The target hostname or IP address.
        start_port (int): The starting port for scanning.
        end_port (int): The ending port for scanning.
    """
    print(f"Starting scan on {target} from port {start_port} to {end_port}")
    print(f"Scan started at {datetime.now()}\n")

    for port in range(start_port, end_port + 1):
        try:
            # Create a socket for the scan
            with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
                s.settimeout(0.5)  # Set a timeout for the connection
                result = s.connect_ex((target, port))  # Attempt to connect to the port

                if result == 0:
                    print(f"Port {port}: OPEN")
        except Exception as e:
            print(f"Error scanning port {port}: {e}")

    print(f"\nScan completed at {datetime.now()}")


if __name__ == "__main__":
    # Input the target and ports to scan
    target_host = input("Enter the target IP or hostname: ").strip()
    start = int(input("Enter the starting port (default: 1): ") or 1)
    end = int(input("Enter the ending port (default: 1024): ") or 1024)

    # Perform the scan
    scan_ports(target_host, start, end)
```
