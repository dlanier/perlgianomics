[Install Docker](https://docs.docker.com/install/) <br>
(note that some windows versions may not be supported) <br>
[get docker image on dockerhub](https://hub.docker.com/r/aka1spanky/ncsa) <br>

Running cromwell and womtools from a container.

Pull and start the current docker image built from this directory's Dockerfile: <br>
`docker pull aka1spanky/ncsa:devwdlV04`

Create a container from the image in your current director: <br>
```docker create --name=cromwell_container -p 8888:8888 -v `pwd`:/home/tmp_usr/run_dir -i aka1spanky/ncsa:devwdlV02```

Start the container: <br>
`docker start cromwell_container`

You may run commands within the container by preceeding them with "docker exec -it container_name": <br>
`docker exec -it cromwell_container whoami` <br>
>$ ncsauser <br>
`docker exec -it cromwell_container pwd` <br>
>$ /home <br> <br>
