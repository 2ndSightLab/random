# random

Random commands that might come in handy.

# Tip: Use AI for sed commands, etc.

I had some posts on useful sed commands and such but you're better off just using AI to formulate those commands. You have to get the prompt just right but generally you can get what you're seeking. Want to know how?

https://medium.com/cloud-security/artificial-intelligence-2e97415216c0

I got many of these commands using AI but the results are not consistent so adding here for future reference.

# Get all the subdomains for a domain

```
domain='2ndsightlab.com'
curl -s "https://crt.sh/?q=%.$domain&output=json" | jq -r '.[].common_name’. | sort | uniq > domains.txt
```

# Get all the IP addresses for a list of domains in a text file

```
xargs -a domains.txt dig +short A
```

# Install dig in AWS CloudShell

```
sudo yum install bind-utils
```

# Wipe out git history (dangerous)
```
git checkout --orphan new_master
git add -A
git commit -m "Initial commit"
git branch -D main
git branch -m main
git push -f origin main
```

# Test if xrdp has access to certificate you want to use
```
sudo -u xrdp cat /etc/xrdp/ssl/certificate.pem > /dev/null && echo "Certificate readable" || echo "Certificate NOT readable"
sudo -u xrdp cat /etc/xrdp/ssl/private-nopass.pem > /dev/null && echo "Key readable" || echo "Key NOT readable"
```

# Securely delete a file on linux
```
sudo shred -u /file.txt
```

# Look at the top 4 rows of hex in a file
```
hexdump -C file.txt | head -n 5
```

# View a live stream of ALL commits to ANY public git repo. Yes really.
```
curl https://api.github.com/events
```
# Create an Open API spec

```
create a valid 3.0 open api spec with correct syntax and formatting, no other errors, and no missing or extra elements. Use [ ] for the base URL. Use [value] as the example for the [field]. Do not add content node to 200. Do not use any prior prompts only base it on this description:
```

# xrdp install - add repo (except I don't think I actually used this. The AWS repo worked fine.)
```
sudo add-apt-repository ppa:xrdp/xrdp
sudo apt update
sudo apt install xrdp
```

# Loop through lines of file in bash
```
while read p; do
  echo "$p"
done <file.txt
```

# netcat listener one port
```
nc -l <port>
```

# netcat listender on port 80 and 443
```
for p in 80 443; do sudo nc -lvnp $p & done
```

# tcpdump listen to port 443 and 80
```
sudo tcpdump 'port 80 or port 443' -nvt
```
