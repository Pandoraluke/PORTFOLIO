# Investigating a Printer Connectivity Problem

**Date:** 22 September 2026
**Environment:** Windows PC, Epson printer, Fritz!Box home network

## Problem

My Windows PC could not communicate with or print to an Epson printer connected to my home network. I investigated whether the PC could reach the printer over the network.

## Tools used

* `ipconfig` — checked the PC’s IP configuration and default gateway
* `ping` — tested whether the printer responded at its IP address
* `tracert` — checked the path toward the printer
* `arp -a` — inspected the PC’s address resolution table
* Fritz!Box interface — checked whether the router showed the printer as connected

## Investigation

My PC had the address `192.168.178.20` and used `192.168.178.1` as its default gateway. The printer appeared with an address in the `192.168.178.x` range.

The `ping` test did not receive a reply from the printer. I also saw a “Destination host unreachable” message from the PC. `tracert` did not establish a working path to the printer.

In the Fritz!Box interface, the printer appeared under idle connections. When a phone connected to the printer, it appeared as active. This showed that the printer’s connection state changed, but it did not by itself explain why the PC could not reach it.

## Findings

The addresses I observed appeared to be in the same IP range. I therefore could **not confirm** my initial theory that the printer and PC were on different subnets. The failed connection could have had another cause, or the printer’s address or network settings could have changed during troubleshooting.

## Outcome and next steps

I identified that the PC could not reach the printer at the address I tested, but I have not yet confirmed the root cause. My next step is to print or view the printer’s network configuration and compare its current IP address, subnet mask, and gateway with the PC’s settings. I would then check whether the PC can reach that current address.

## What I learned

This investigation gave me practice using Windows network commands together rather than relying on one result. It also taught me to distinguish an observation—such as a failed ping—from a confirmed explanation of *why* it failed.
