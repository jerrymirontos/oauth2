Oauth 2 Demo
==================

Spring OAuth 2.0 Demo
----------------------
http://blog.rajithdelantha.com/2015/09/secure-your-rest-api-with-spring.html

1st step, create access_token and refresh_token.
----------------------------
```java
http://localhost:8080/oauth2/oauth/token?grant_type=password&client_id=jml-client-id&client_secret=12345&username=jml&password=password
```

```java
{
 access_token: "f833a754-0d6c-4595-92c8-99b202ea6dd4"
 token_type: "bearer"
 refresh_token: "967068eb-13d1-4d18-8dd8-b89b2124d5d6"
 expires_in: 4
 scope: "read trust write"
}
```

2nd step, create new access_token using the 1st step refresh_token when access_token expired
---------------------------
```java
http://localhost:8080/oauth2/oauth/token?grant_type=refresh_token&client_id=jml-client-id&refresh_token=967068eb-13d1-4d18-8dd8-b89b2124d5d6&client_secret=12345
```
```java
{
access_token: "d78dd4c7-41c3-443d-a85e-3716ceefc66f"
token_type: "bearer"
refresh_token: "967068eb-13d1-4d18-8dd8-b89b2124d5d6"
expires_in: 4
scope: "read trust write"
}
```

Protected Resource
------------------
http://localhost:8080/oauth2/test/ateam?access_token=d78dd4c7-41c3-443d-a85e-3716ceefc66f