[Install Docker](https://docs.docker.com/install/) <br>
(note that some windows versions may not be supported) <br>
[get docker image on dockerhub](https://hub.docker.com/r/aka1spanky/ncsa) <br>

Running cromwell and womtools from a container.

Pull and start the current docker image built from this directory's Dockerfile: <br>
>$ `docker pull aka1spanky/ncsa:devwdlV04`

Create a container from the image with your current directory mounted and port 8888 connected: <br>
>$ ```docker create --name=cromwell_container -p 8888:8888 -v `pwd`:/home/tmp_usr/run_dir -i aka1spanky/ncsa:devwdlV04``` <br>

Start the container: <br>
>$ `docker start cromwell_container`

You may run commands within the container by preceeding them with "docker exec -it container_name": <br>

>$ `docker exec -it cromwell_container whoami` <br>
>$ ncsauser <br>
>$ `docker exec -it cromwell_container pwd` <br>
>$ /home <br> <br>
>$ `docker exec -it cromwell_container ls /home/tmp_usr/run_dir` <br>
>$ (Your local directory contents - files mounted in - /home/tmp_usr/run_dir/ ) <br> 
>$ `docker exec -t cromwell_container ls /usr/local/etc` <br>
>$ cromwell-36.jar  jupyter  womtool-36.jar  <br>

This setup allows one to run and test wdl code using Cromwell and Womtools from the command line.

See the wiki for detailed notebook directions, or start the jupyter notebook private server in the container.

>$ `docker exec -it cromwell_container jupyter notebook --generate-config` <br>
>$ `docker exec -it cromwell_container jupyter notebook password` <br>

You will be prompted for a password, after setting it start the jupyter notebook server. <br>
>$ `docker exec -it cromwell_container jupyter notebook --no-browser --port=8888 --ip=0.0.0.0` <br>
paste this into your browser window: <br>
```http://localhost:8888``` <br>
Enter your password in the login page and the container home directory appears in the jupyter file browser in your web browser. <br>
