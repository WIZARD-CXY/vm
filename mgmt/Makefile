NAME = rancher/ranchervm
VERSION = 0.0.1
NOVNC_VERSION = 0.0.2

.PHONY : all clean build

all: build tag_latest

build: noVNC-$(NOVNC_VERSION).tar.gz
	docker build -t $(NAME):$(VERSION) .

noVNC-$(NOVNC_VERSION).tar.gz:
	wget -O noVNC-$(NOVNC_VERSION).tar.gz https://github.com/rancherio/noVNC/archive/v$(NOVNC_VERSION).tar.gz

clean:
	rm -f noVNC-$(NOVNC_VERSION).tar.gz

tag_latest:
	docker tag -f $(NAME):$(VERSION) $(NAME):latest

run:
	docker run -v /var/run/docker.sock:/var/run/docker.sock \
	-p 8080:80 -v /tmp/ranchervm:/ranchervm \
	$(NAME):$(VERSION)
