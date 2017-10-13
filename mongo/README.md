## 参考：
- https://github.com/docker-library/docs/tree/master/mongo
- https://github.com/docker-library/mongo/blob/master/3.0/Dockerfile

## 设置密码

```
docker exec -it some-mongo mongo admin
connecting to: admin
> db.createUser({ user: 'jsmith', pwd: 'some-initial-password', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });
Successfully added user: {
	"user" : "jsmith",
	"roles" : [
		{
			"role" : "userAdminAnyDatabase",
			"db" : "admin"
		}
	]
}
```