---
title: "Installing Hugo in WSL (Ubuntu)"
draft: false
cover:
    image: img/hugologo.jpg
    alt: "This is a post image"
    caption: "Hugo Installation"
tags: ["html", "css"]
categories: ["tech"]
---

## Installing Hugo
### Steps learnt in Installing Hugo
---
In WSL, install the latest version by the using the following command:

wget https://github.com/gohugoio/hugo/releases/download/v0.130.0/hugo_0.130.0_Linux-64bit.tar.gz

### Extract Hugo Binary:
tar -xzvf hugo_0.130.0_Linux-64bit.tar.gz

### Move Hugo Binary to /usr/local/bin:
sudo mv /root/hugo /usr/local/bin/

### Ensure Hugo Binary is Executable:
sudo chmod +x /usr/local/bin/hugo

### Verify PATH includes /usr/local/bin:
echo $PATH | grep /usr/local/bin

### Check Hugo Version Directly from /usr/local/bin:
/usr/local/bin/hugo version

### Create Symlink in /usr/bin (if needed):
sudo ln -s /usr/local/bin/hugo /usr/bin/hugo

### Verify Hugo Installation:
hugo version

