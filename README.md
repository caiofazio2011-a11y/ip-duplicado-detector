# ip-duplicado-detector
ip-duplicado-detector
import subprocess
import re
from collections import Counter

print("Escaneando dispositivos da rede...")

arp_output = subprocess.check_output("arp -a", shell=True).decode()
ips = re.findall(r'\d+\.\d+\.\d+\.\d+', arp_output)

ip_count = Counter(ips)

print("\nResultado:")
for ip, count in ip_count.items():
    if count > 1:
        print(f"IP duplicado encontrado: {ip} ({count} vezes)")
