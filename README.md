# Small tweaks to a ThinkPad x60(s) running Linux
## Features
- undervolt CPU to 1.000 volts (~10 degrees C cooler)
- enable volume keys

# Undervolting
## Kernel
To undervolt your CPU, you need a phc-enabled kernel:
- `sudo add-apt-repostiory ppa:linux-phc/ppa`
- `sudo apt-get update`
- `sudo apt-get install linux-generic-phc linux-headers-generic-phc`

## Blacklist default acpi modules
`sudo echo blacklist acpi_cpufreq\nblacklist cpufreq_stats >> /etc/modprobe.d/blacklist.conf`

## Install phc-intel kernel module
The .deb is in the repo, all you need to do is `sudo dpkg -i phc-intel-dkms_0.3.2_all.deb`

## Load the module on startup, apply undervolt
Copy the rc.local file from the report to /etc

    sudo cp rc.local /etc/

## Load undervolt setting after resuming from sleep
If the laptop sleeps, the undervolt settings will be reset, so you need to apply them on resume. Copy the `9999_phc_vids` script to /etc/pm/sleep.d/

    sudo cp 9999_phc_vids /etc/pm/sleep.d/

## Enjoy
Enjoy a cool, working, awesome and linux laptop
