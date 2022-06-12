.text_install:
	virt-install \
        --name test1 \
        --ram 1024 \
        --vcpus 1 \
        --location http://deb.debian.org/debian/dists/stable/main/installer-amd64/ \
        --os-variant debian10 \
        --virt-type kvm \
        --disk ${PWD}/test1.img,size=4 \
        --initrd-inject ${PWD}/preseed.cfg \
        --extra-args 'console=ttyS0 auto=true'\
        --graphics none \
        --noautoconsole

all:
	make .text_install

clean:
	virsh destroy test1
	virsh undefine test1
	virsh vol-delete --pool preseed test1.img
