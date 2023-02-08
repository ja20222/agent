clean: ## Remove docker containers and agent package
	docker-compose down
	rm -rf ../../build

build: clean ## Build agent package
	mkdir ../../build
	cd ../../ && GOWORK=off CGO_ENABLED=0 GOARCH=amd64 GOOS=linux go build -o ./build/nginx-agent
	cd ../../ && nfpm pkg --config ./scripts/.local-nfpm.yaml --packager deb --target ./build/nginx-agent.deb

run: build ## Start docker containers
	docker-compose up --build
