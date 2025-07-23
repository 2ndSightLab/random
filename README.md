# random

Random commands that might come in handy.

# Tip: Use AI for sed commands, etc.

I had some posts on useful sed commands and such but you're better off just using AI to formulate those commands. You have to get the prompt just right but generally you can get what you're seeking.

# Get all the subdomains for a domain

```
domain='2ndsightlab.com'
curl -s "https://crt.sh/?q=%.$domain&output=json" | jq -r '.[].common_name’. | sort | uniq > domains.txt
```

# Get all the IP addresses for a list of domains in a text file

```
xargs -a domains.txt dig +short A
```
