![[Pasted image 20240817120918.png]]

Package
- collection of files needed to install an application
- prior to packages, applications were installed using the source code
	- then the binaries were compiled on the host
	- or a host of the same architecture and moved over
	- sometimes the applications did not compile properly or the needed additional libraries or files to be able to function

Package Managers
- types
	- dkpg (Debian Package)
		- apt-get (Advanced Package Tool)
		- .deb
	- rpm (Red Hat Package Manager)
		- yum (Yellowdog Updater, Modified)
		- .rpm
		- most rpms are binary rpms containing the compiled version of the software to install
		- however home use SRPMs (Source RPMs) containing the source code for local compilation
		- `dnf` 
			- rewrite of yum
			- default package manager of fedora systems
			- created to improve upon yum in serveral ways
				- better performance
				- better dependency resolution
				- easier integration with other applications
- you cannot mix and match .deb and .rpm binaries
- these package managers will keep up with that is installed in the system
	- also makes use of repositories to pull software from
- makes it so that `dependencies` of the packages you are installing are also installed
- you can make your package manager look at different repositories to get the packages it needs
	- you can configure where it gets the packages from
- these packages include:
	- package installation files
	- meta-data containing dependencies
	- and installation paths


Repositories
- repositories is a collection of packages

Fedora
- cutting edge, consumer version of red hat