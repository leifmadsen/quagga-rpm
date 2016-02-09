# Cumulus Quagga RPM

**Not supported by Cumulus Networks**

Build source rpm for cumulus quagga  from cumulus networks github.

Original Source RPM was the Quagga Fedora 23 Source RPM. Changed the source file location and the build config parameters.

## Building RPMs with Mock
First install Mock and rpmbuild

```
sudo yum install mock rpm-build
```

Then create a new `mock` user and add them to the `mock` group:

```
sudo adduser mock
sudo usermod -a -G mock
```

Switch to the `mock` user and check out this repository:

```
git clone https://github.com/skamithi/quagga-rpm.git rpmbuild
```

Then you can rebuild the SRPM and RPMs with Mock:

```
cd rpmbuild/SPECS
rpmbuild -bs quagga.spec
cd ../SRPMS
mock -r <config_file> rebuild <SRPM_file>
```

Replace `<config_file>` with something like `epel-7-x86_64` or `fedora-23-x86_64`. Available chroot config files
are available in `/etc/mock/`. Replace `<SRPM_file>` with the resulting SRPM from your `rpmbuild` command.
