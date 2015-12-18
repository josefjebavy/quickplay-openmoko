NAME=quickplay
ICON=$(NAME).png
FILES=$(NAME)

cilovyAdresar=/home/root/card/python/quickplay


LASTVERSION=1.5-r3-touchbook
IPKLAST=$(NAME)_$(LASTVERSION)_all.ipk
DEPENDS="python-core  python-pygtk python-netclient"



install:
	scp $(IPKLAST)  192.168.0.202:$(cilovyAdresar)/
	ssh root@192.168.0.202 'opkg install $(cilovyAdresar)/$(IPKLAST)'

ipk:	package
pk:	package
package:
	mkdir -p package-ipkg/CONTROL package-ipkg/usr/bin package-ipkg/usr/share/applications package-ipkg/usr/share/pixmaps
	cp $(ICON) package-ipkg/usr/share/pixmaps/
	cp $(FILES) package-ipkg/usr/bin/
	echo -e Package: quickplay  \\n\
	Section: extras \\n\
	Priority: optional \\n\
	Version: $(LASTVERSION) \\n\
	Architecture: all \\n\
	Source: http://quickplay.ampache.org \\n\
	"Maintainer: Josef Jebavy <josef.jebavy[at]gmail.com>" \\n\
	Depends: $(DEPENDS) \\n\
	Description: A light weight mp3 player/frontend for Ampache. \\n > package-ipkg/CONTROL/control
	cp $(NAME).desktop package-ipkg/usr/share/applications/
	ipkg-build  -o root -g root ./package-ipkg/ ./
	rm -rf ./package-ipkg/
