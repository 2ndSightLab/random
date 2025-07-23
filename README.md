# random

Random commands that might come in handy.

# Get all the subdomains for a domain

'''
domain='2ndsightlab.com'
curl -s "https://crt.sh/?q=%.$domain&output=json" | jq -r '.[].common_name’. | sort | uniq > domains.txt
'''

# Get all the IP addresses for a list of domains in a text file

'''
xargs -a domains.txt dig +short A
'''
