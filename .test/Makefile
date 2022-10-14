IMAGE_REPO ?= $(CI_REGISTRY_IMAGE)/testcase
IMAGE_BUILD_FROM ?= registry.gitlab.com/modioab/base-image/fedora-${FEDORA_ROOT_RELEASE}/python:master

IMAGE_TEST_ARGS = -t --rm=true
IMAGE_TEST_CMD = /usr/bin/python3 -c True

include build.mk
