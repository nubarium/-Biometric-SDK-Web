# Create JWT Token

Create a JWT Token for the given credentials

**URL** : `https://api.sdk.nubarium.com/jwt/v1/generate`

**Method** : `POST`

**Auth required** : YES

**Auth type** : Basic (User your Nubarium Credentials)

## Success Response

**Condition** : If everything is OK and an Account didn't exist for this User.

**Code** : `200 OK`

**Content example**

```json
{
    "username": "nubarium",
    "uuid": "abf8ede0-5979-4be8-8bac-0a6de8b195be",
    "name": "nubarium",
    "is_admin": false,
    "bearer_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Im51YmFyaXVtIiwidXVpZCI6IjQ3M2MyYWM3LWVlMmQtNDFhNi04YWYwLTg0ZTQxZDVkOTI4MyIsIm5hbWUiOiJudWJhcml1bSIsImlzX2FkbWluIjpmYWxzZX0.tGY80y9q_Gb-fIxv6RMFzpNQwWd5uGZ_H8u5-RyFkSk"
}
```

## Error Responses

**Condition** : If enter bad credentials.

**Code** : `401 Unauthorized`

