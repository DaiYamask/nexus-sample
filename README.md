# nexus-sample 📦

## Run with docker 

```
$ docker volume create --name nexus-data
$ docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
```

show logs

```
$ docker logs -f nexus
```

access your local nuxus http://localhost:8081

## login as admin
Username: admin  
Password: ????

you can find admin password in admin.password file inside your volume.

## How to find `admin.password`

### docker volume inspect
```
$ docker volume inspect nexus-data
[
    {
        "CreatedAt": "2020-01-30T02:18:38Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/nexus-data/_data",
        "Name": "nexus-data",
        "Options": {},
        "Scope": "local"
    }
]
```
access to Mountpoint in docker desktop (vm)

```
docker-desktop:~# cat /var/lib/docker/volumes/nexus-data/_data/admin.password
```

## Configuration Nuxus as npm repo
Read the blog post 👀  
https://blog.sonatype.com/using-nexus-3-as-your-repository-part-2-npm-packages

## How to publish to npm repo

1. login
2. setting realm
3. publish

```
$ npm publish
npm notice
npm notice 📦  nexus-sample@1.0.0
npm notice === Tarball Contents ===
npm notice 552B  package.json
npm notice 230B  index.js
npm notice 1.0kB README.md
npm notice === Tarball Details ===
npm notice name:          nexus-sample
npm notice version:       1.0.0
npm notice package size:  1.0 kB
npm notice unpacked size: 1.8 kB
npm notice shasum:        4e790fa384f3ce9c5f41a595a0defb52754c1489
npm notice integrity:     sha512-skhNKIPEXY/5n[...]k9DKXAAXHn4/A==
npm notice total files:   3
npm notice
+ nexus-sample@1.0.0
```