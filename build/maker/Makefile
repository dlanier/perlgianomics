CUR_DATE=`date + '%m_%d_%Y'`


build_docker_image:
	docker build --no-cache -t aka1spanky/ncsa:'maker_'$(CUR_DATE) .

login_to_dockerhub:
	docker login --username=$(username) --password=$(password)

push_to_dockerhub:
	docker push aka1spanky/ncsa:'maker_'$(CUR_DATE)

# push only if it works eh?
