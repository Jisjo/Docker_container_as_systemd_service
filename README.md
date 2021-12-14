# Docker_container_as_systemd_service

```bash
[root@ip-172-31-3-64 www]# docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@ip-172-31-3-64 www]# service docker.httpd.service start
Redirecting to /bin/systemctl start docker.httpd.service
[root@ip-172-31-3-64 www]# service docker.httpd.service status
Redirecting to /bin/systemctl status docker.httpd.service
● docker.httpd.service - httpd Service
   Loaded: loaded (/etc/systemd/system/docker.httpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2021-12-14 15:45:34 UTC; 3s ago
  Process: 23862 ExecStartPre=/usr/bin/docker pull httpd:2.4 (code=exited, status=0/SUCCESS)
  Process: 23854 ExecStartPre=/usr/bin/docker rm httpd:2.4 (code=exited, status=1/FAILURE)
  Process: 23849 ExecStartPre=/usr/bin/docker stop httpd:2.4 (code=exited, status=1/FAILURE)
 Main PID: 23874 (docker)
    Tasks: 5
   Memory: 23.9M
   CGroup: /system.slice/docker.httpd.service
           └─23874 /usr/bin/docker run --name httpd-server --rm httpd:2.4

Dec 14 15:45:31 ip-172-31-3-64.ap-south-1.compute.internal docker[23854]: Error: No such container: httpd:2.4
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23862]: 2.4: Pulling from library/httpd
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23862]: Digest: sha256:fba8a9f4290180ceee5c74638bb85ff21fd15961e6fdfa4def48e18820512bb1
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23862]: Status: Image is up to date for httpd:2.4
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23862]: docker.io/library/httpd:2.4
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal systemd[1]: Started httpd Service.
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23874]: AH00558: httpd: Could not reliably determine the server's fully qualified domain name,...message
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23874]: AH00558: httpd: Could not reliably determine the server's fully qualified domain name,...message
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23874]: [Tue Dec 14 15:45:34.913439 2021] [mpm_event:notice] [pid 1:tid 139988683423040] AH004...rations
Dec 14 15:45:34 ip-172-31-3-64.ap-south-1.compute.internal docker[23874]: [Tue Dec 14 15:45:34.914062 2021] [core:notice] [pid 1:tid 139988683423040] AH00094: C...GROUND'
Hint: Some lines were ellipsized, use -l to show in full.
[root@ip-172-31-3-64 www]# docker container ls -a
CONTAINER ID   IMAGE       COMMAND              CREATED          STATUS          PORTS     NAMES
c0d6412da7b8   httpd:2.4   "httpd-foreground"   17 seconds ago   Up 16 seconds   80/tcp    httpd-server
[root@ip-172-31-3-64 www]# 

```
