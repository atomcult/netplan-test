```sh
# Note: This should be performed within a 20.04 LXD container

# Verify initial state
netplan get all
cat /run/systemd/network/*

# Generate the snap
snapcraft

# Install
snap install --dangerous *.snap

# Setup the connection
snap connect netplan-test:network-setup-control

# Install again to trigger the post-refresh hook
snap install --dangerous *.snap

# Verify changes (you should see 8.8.8.8 in the DNS section)
netplan get all
cat /run/systemd/network/*
```
