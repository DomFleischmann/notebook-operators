TAG ?= $(shell git describe --tags --always --dirty)
REGISTRY ?= charmedkubeflow

docker-build-all:
	@echo "\nBuilding base image...\n"
	make docker-build -C base TAG=${TAG}

	@echo "\nBuilding jupyter image...\n"
	make docker-build -C jupyter TAG=${TAG} 

	@echo "\nBuilding jupyter-scipy image...\n"
	make docker-build -C jupyter-scipy TAG=${TAG} 

	@echo "\nBuilding jupyter-pytorch image...\n"
	make docker-build-cpu -C jupyter-pytorch TAG=${TAG} 

	@echo "\nBuilding jupyter-pytorch-cuda image...\n"
	make docker-build-cuda -C jupyter-pytorch TAG=${TAG} 

	@echo "\nBuilding jupyter-pytorch-full image...\n"
	make docker-build-cpu -C jupyter-pytorch-full TAG=${TAG}

	@echo "\nBuilding jupyter-pytorch-cuda-full image...\n"
	make docker-build-cuda -C jupyter-pytorch-full TAG=${TAG} 

	@echo "\nBuilding jupyter-tensorflow image...\n"
	make docker-build-cpu -C jupyter-tensorflow TAG=${TAG} 

	@echo "\nBuilding jupyter-tensorflow-cuda image...\n"
	make docker-build-cuda -C jupyter-tensorflow TAG=${TAG} 

	@echo "\nBuilding jupyter-tensorflow-full image...\n"
	make docker-build-cpu -C jupyter-tensorflow-full TAG=${TAG} 

	@echo "\nBuilding jupyter-tensorflow-cuda-full image...\n"
	make docker-build-cuda -C jupyter-tensorflow-full TAG=${TAG} 

	@echo "\nAll notebook-server images have been successfully built...\n"

docker-push-all:
	for img in base jupyter jupyter-scipy jupyter-pytorch-full jupyter-pytorch-cuda-full jupyter-tensorflow-full \
	jupyter-tensorflow-cuda-full jupyter-tensorflow; do \
		docker tag $$img:${TAG} ${REGISTRY}/$$img:${TAG} ; \
		docker push ${REGISTRY}/$$img:${TAG} ; \
	done

	

	
