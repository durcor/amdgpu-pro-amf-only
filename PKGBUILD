# Maintainer durcor <durcor@disroot.org>
#
# Based off of
# Tk-Glitch <ti3nou at gmail dot com>'s
# AMDVLK-PRO PKGBUILD

plain '       .---.`               `.---.'
plain '    `/syhhhyso-           -osyhhhys/`'
plain '   .syNMdhNNhss/``.---.``/sshNNhdMNys.'
plain '   +sdMh.`+MNsssssssssssssssNM+`.hMds+'
plain '   :syNNdhNNhssssssssssssssshNNhdNNys:'
plain '    /ssyhhhysssssssssssssssssyhhhyss/'
plain '    .ossssssssssssssssssssssssssssso.'
plain '   :sssssssssssssssssssssssssssssssss:'
plain '  /sssssssssssssssssssssssssssssssssss/'
plain ' :sssssssssssssoosssssssoosssssssssssss:'
plain ' osssssssssssssoosssssssoossssssssssssso'
plain ' osssssssssssyyyyhhhhhhhyyyyssssssssssso'
plain ' /yyyyyyhhdmmmmNNNNNNNNNNNmmmmdhhyyyyyy/'
plain '  smmmNNNNNNNNNNNNNNNNNNNNNNNNNNNNNmmms'
plain '   /dNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNd/'
plain '    `:sdNNNNNNNNNNNNNNNNNNNNNNNNNds:`'
plain '       `-+shdNNNNNNNNNNNNNNNdhs+-`'
plain '             `.-:///////:-.`'

pkgname=amdgpu-pro-amf-only
pkgver=21.30.1290604
_pkgveramd=21.30-1290604
pkgrel=1
arch=('x86_64')
url='http://www.amd.com'
license=('custom:AMD')
makedepends=('wget')
depends=('amdgpu-pro-vulkan-only' 'ffmpeg-amd-full-git')

DLAGENTS='https::/usr/bin/wget --referer https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux.aspx -N %u'

source=(https://drivers.amd.com/drivers/linux/amdgpu-pro-${_pkgveramd}-ubuntu-20.04.tar.xz)
sha256sums=('5840aac63a3658b3f790c59e57226062e7e4bc74f3c066a3e7bc9e3065e24382')

# extracts a debian package
# $1: deb file to extract
extract_deb() {
	local tmpdir="$(basename "${1%.deb}")"
	rm -Rf "$tmpdir"
	mkdir "$tmpdir"
	cd "$tmpdir"
	ar x "$1"
	tar -C "${pkgdir}" -xf data.tar.xz
}

package_amdgpu-pro-amf-only () {
	pkgdesc="The AMDGPU Pro AMF driver, without everything else"
	arch=('x86_64')

	extract_deb "${srcdir}"/amdgpu-pro-${_pkgveramd}-ubuntu-20.04/./amf-amdgpu-pro_${_pkgveramd}_amd64.deb

	rm -rf "${pkgdir}"/etc

    sudo ln -s /opt/amdgpu-pro/lib/x86_64-linux-gnu/libamfrt64.so.0.0.0 /lib/libamfrt64.so.1

	msg2 "#################################################################"
	msg2 ""
	msg2 "64-bit lib in /opt/amdgpu-pro/lib/x86_64-linux-gnu/libamfrt64.so"
	msg2 ""
	msg2 "changelog and copyright in /usr/share/doc/amf-amdgpu-pro"
	msg2 ""
	msg2 "#################################################################"
}
