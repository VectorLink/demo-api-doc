export PATH := $(shell pwd)/node_modules/.bin:$(PATH)
SHELL := /bin/bash

.PHONY: init dev build genEntry genServices publish

# 初始化项目
init:
	yarn
	mkdir -p dist

# 开发模式
dev:
	yarn run start

publish:
	yarn
	yarn run publish

# 打包代码结果
build:
	yarn run build

genEntry:
	./tool/genEntry

updateAntd:
	node ./tool/updateAntd
# 建议每次只生成自己的服务
# 多个 service 文件以空格隔开
#apidoc
protobufServices = \
apidoc/proto/provider/V3User.proto\
apidoc/proto/consumer/User.proto\

genservices:
	protoc --plugin=protoc-gen-json-ts.cmd=./node_modules/.bin/protoc-gen-json-ts --json-ts_out=:src/genServices -I ./apidoc/proto $(protobufServices)
