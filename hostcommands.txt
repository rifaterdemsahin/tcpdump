#!/bin/bash

# Register the system with Red Hat Subscription Manager
echo "Registering the system with Red Hat Subscription Manager..."
echo 'subscription-manager register --username rifaterdemsahin --password XXX' > register.sh
chmod +x register.sh
./register.sh

# Check if the registration was successful
if [ $? -ne 0 ]; then
  echo "Registration failed. Please check your credentials and try again."
  exit 1
fi

# Enable necessary repositories for RHEL 9
echo "Enabling RHEL 9 repositories..."
subscription-manager repos --list
subscription-manager repos --enable=rhel-9-for-x86_64-baseos-rpms
subscription-manager repos --enable=rhel-9-for-x86_64-appstream-rpms

# Update CA certificates
echo "Updating CA certificates..."
dnf update -y ca-certificates

# Clean and rebuild the DNF cache
echo "Cleaning and rebuilding the DNF cache..."
dnf clean all
dnf makecache

# Capture network traffic with tcpdump
echo "Capturing network traffic..."
tcpdump -i 42 -w /host/var/tmp/mydebug.pcap

# Copy the captured pcap file from the node to the local system
echo "Copying captured network traffic to local system..."
oc debug node/crc -- bash -c 'cat /host/var/tmp/mydebug.pcap' > /tmp/mydebug.pcap

# Enter chroot environment on the host
echo "Entering chroot environment on the host..."
chroot /host
