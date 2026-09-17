# Book Review Backend

Complete Express REST API based on the uploaded Book Review Application specification.

## Run

```bash
npm install
npm run dev
```

Server:

```text
http://localhost:5000
```

## Main endpoints

### Public
- `GET /`
- `GET /isbn/:isbn`
- `GET /author/:author`
- `GET /title/:title`
- `GET /review/:isbn`
- `POST /register`

### Authenticated
- `POST /customer/login`
- `PUT /customer/auth/review/:isbn`
- `DELETE /customer/auth/review/:isbn`

Authentication uses a JWT stored in the Express session, matching the project's session-level JWT requirement.

## Example requests

Register:

```bash
curl -X POST http://localhost:5000/register ^
  -H "Content-Type: application/json" ^
  -d "{\"username\":\"jawad\",\"password\":\"12345\"}"
```

Login:

```bash
curl -X POST http://localhost:5000/customer/login ^
  -H "Content-Type: application/json" ^
  -c cookies.txt ^
  -d "{\"username\":\"jawad\",\"password\":\"12345\"}"
```

Add/update review:

```bash
curl -X PUT http://localhost:5000/customer/auth/review/1 ^
  -H "Content-Type: application/json" ^
  -b cookies.txt ^
  -d "{\"review\":\"Excellent book!\"}"
```

Get review:

```bash
curl http://localhost:5000/review/1
```

Delete your review:

```bash
curl -X DELETE http://localhost:5000/customer/auth/review/1 ^
  -b cookies.txt
```

## Notes

The original lab uses an in-memory `books` object and an in-memory users array, so this project intentionally does not require MongoDB.
