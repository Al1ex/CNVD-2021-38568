## Information
```javascript
Exploit Title:Novel-plus-install-v3.5.3-Druid Unauthorized access
Exploit date:01.06.2021
Exploit Author:Al1ex@Heptagram
Vendor Homepage:https://github.com/201206030/novel-plus
Affect Version:novel-plus-install-v3.5.3
Description:Novell plus system carries Druid component, and the permission check is verified by Shiro. However, Shiro has wrong configuration when checking permission, which leads to unauthorized access of Druid in Novell plus. Attackers can use this vulnerability to obtain sensitive information, such as database link address, database user name, valid session information, etc.
```

## How to Exploit

**Step 1：After setting up the Novell plus environment, visit the following connections**
http://192.168.174.1:8088/druid/index.html
![image](https://user-images.githubusercontent.com/38161463/120259784-22058680-c2c7-11eb-8231-7af75e3430af.png)
![image](https://user-images.githubusercontent.com/38161463/120259824-38abdd80-c2c7-11eb-823d-a521c6009464.png)
![image](https://user-images.githubusercontent.com/38161463/120259794-2af65800-c2c7-11eb-9f79-c08d48c537fe.png)
![image](https://user-images.githubusercontent.com/38161463/120259806-32b5fc80-c2c7-11eb-872b-6e9d1e48dea9.png)

## Code Analysis
https://github.com/201206030/novel-plus/blob/develop_xxy/novel-admin/src/main/java/com/java2nb/common/config/ShiroConfig.java#L78
Anon here means to allow any user to access, while authc needs to check the permissions. You can see that Druid has unauthorized access.
![image](https://user-images.githubusercontent.com/38161463/120259901-65f88b80-c2c7-11eb-9274-04d675c4ed9a.png)

## Suggestion
Change anon to authc for permission checking