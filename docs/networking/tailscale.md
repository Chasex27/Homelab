# Tailscale

## Overview and Reasoning
Tailscale is how I securely access my homelab from anywhere without exposing services directly to the internet.
Instead of opening ports on my home network, Tailscale creates an encrypted mesh VPN between my trusted devices.

## Purpose

### My main goals of implementing Tailscale are:

#### Secure remote access to my homelab
#### Eliminate unnecessary port forwarding
#### Access internal services from anywhere
#### Exploring Zero Trust networking concepts

## Why I Chose Tailscale

I wanted a simple and secure way to manage my homelab remotely without relying on port forwarding or exposing management interfaces to the public internet.
As my lab grows, I plan to use Tailscale and OPNsense to separate network security from remote access.

### Tailscale gives me:

#### Secure remote access to my entire lab
#### Encrypted communication between devices
#### Easy access from my laptop and phone
#### A foundation for learning Zero Trust networking
#### It also has a nice UI for me to interact with 
#### Supports up to 3 users and 100 devices which is plenty for me



## Learning Objectives

### This project gave me hands-on experience with:

#### Zero Trust networking
#### WireGuard VPNs
#### Secure remote administration
#### Access control through identity 
#### Remote infrastructure management

## Installation

Installation was very simple. I ran this command: curl -fsSL https://tailscale.com/install.sh | sh
Once complete I authenticated using the Tailscale web UI 

## Current Status

#### ✅ Tailscale selected for remote access
#### ✅ Installed Tailscale on my primary devices
#### ⏳ Configure a subnet router
#### ⏳ Enable MagicDNS
#### ⏳ Create access control policies
