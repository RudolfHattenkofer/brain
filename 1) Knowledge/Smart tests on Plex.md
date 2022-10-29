- Check whether our drive is a smart type or not.

sudo smartctl -i /dev/sda

![image-107.png](image-107.png)

* 	To e**nable** the smartctl so that smartctl always starts whenever the system reboots, run this command below

sudo smartctl -s on /dev/sda

**Note**: smartctl can perform different hard drive tests and can analyze a problem with our drive so first let us go with checking our hard drive health by executing the command below

smartctl -H /dev/sda

![image-109.png](image-109.png)

* 	To verify the test mode on hard drive

smartctl -H /dev/vda

- To run a short test on the HDD

smartctl -test=short /dev/vda

- Also To run a long test on our HDD

smartctl -test=long /dev/vda

- Display Error logs of the disk

smartctl -l error /dev/sda

- make sure that the drive supports self-tests

smartctl -c /dev/sda

- You can run to self test check results

smartctl -l selftest /dev/sda

- If you want to uninstall smartctl utility, run this command

sudo apt remove smartmontools

Devices are:

/dev/sda SSD

/dev/sdb sdc sdd HDDs

e.g.

usr/local/sbin/smartctl -H /dev/sdd



