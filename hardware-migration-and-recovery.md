# Proxmox Recovery After Hardware Failure
## Overview

The original Proxmox server suddenly stopped working and would no longer boot. My goal was to figure out what failed and get the server back online.

## Diagnosing the Hardware

The first thing I suspected was the power button, so I tested that beacuse it was in a state of always being depressed. I repalced the powerbutton with an external one still with no sucess.

Next, I replaced the power supply with a known working one from another machine. The system still wouldn't boot, so I ruled out the power supply as well.

At that point, the most likely cause was either the motherboard or the CPU.

Instead of replacing multiple components, I moved the Proxmox boot drive into another compatible computer to see if I could recover the existing installation.

Replacement hardware: (Specs will be added later.)

## Problem After the Hardware Swap

The replacement computer booted Proxmox, but I couldn't access the web interface.

## Symptoms
Server powered on normally.
Server responded to ping requests.
Proxmox web interface was unavailable.
SSH connection failed.

## Troubleshooting

### Step 1: Verify Network Connectivity

From another computer on the network, I first checked whether the server was reachable.

ping <proxmox-ip-address>

The server replied successfully, so I knew it was powered on and connected to the network.

Since the server responded to ping, I knew the issue wasn't a complete network failure.

### Step 2: Test SSH

Next, I tried connecting over SSH.

ssh root@<proxmox-ip-address>

The connection failed, so I connected a monitor and keyboard directly to the Proxmox machine to troubleshoot locally.

### Step 3: Check System Services

Once logged in, I checked that SSH was running.

systemctl status ssh

SSH was active.

Next, I checked the networking service.

systemctl status networking

While checking the logs, I found this error:

vmbr0: bridge port nic1 does not exist

That pointed me toward the network bridge configuration.

###Step 4: Find the Correct Network Interface

I listed the available network interfaces.

ip link

The output showed:

lo
eno1

The replacement motherboard named the network interface eno1, but my Proxmox configuration was still trying to use nic1.

Because nic1 didn't exist anymore, the vmbr0 bridge couldn't start.

###Step 5: Fix the Configuration

I edited the network configuration.

nano /etc/network/interfaces

I changed:

bridge-ports nic1

to:

bridge-ports eno1

Then I restarted networking using:

systemctl restart networking

After that, both SSH and the Proxmox web interface started working again.

## Root Cause

Moving the Proxmox installation to different hardware caused Linux to rename the network interface.

The Proxmox bridge configuration was still calling the old interface name (nic1), so the network bridge failed to initialize.

Updating the bridge to use (eno1) restored network connectivity.

## What I Learned
Don't assume the network interface name will stay the same after moving drives to different hardware.
A server can still respond to ping while other services like SSH and web interfaces are unavailable.
Running ip link is a quick way to verify the current interface names.
Keeping documentation of fixes makes future troubleshooting much easier.
