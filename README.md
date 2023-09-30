# CodesOnBytestask-2
import re

def validate_ipv4(ip):
    # Regular expression pattern for a valid IPv4 address
    ipv4_pattern = r'^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}$'
    
    # Check if the IP address matches the pattern
    if not re.match(ipv4_pattern, ip):
        return False
    
    # Split the IP address into octets
    octets = ip.split('.')
    
    # Check if each octet is a valid number in the range [0, 255]
    for octet in octets:
        try:
            octet_int = int(octet)
            if octet_int < 0 or octet_int > 255:
                return False
        except ValueError:
            return False
    
    return True

# Input an IP address to validate
ip_address = input("Enter an IPv4 address: ")

if validate_ipv4(ip_address):
    print(f"{ip_address} is a valid IPv4 address.")
else:
    print(f"{ip_address} is not a valid IPv4 address.")
