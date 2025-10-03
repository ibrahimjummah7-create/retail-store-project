# CloudPros Web Store (local, AWS-free)

Minimal store composed of services: products (SQLite, seeded from FakeStore), carts (Redis),
orders (checkout + cart clear), users (JWT auth with SQLite), and a static web UI proxied via Nginx.

## Run
```bash
docker compose up --build
open http://localhost:8080
```

## Notes
- First start will fetch products from https://fakestoreapi.com/ and cache them locally (SQLite).
- Cart is stored in Redis, keyed by `userId` (guest or auth user id).
- Sign in / Sign up are local only; token stored in localStorage.
- To reset (and reseed), run: `docker compose down -v` and then `docker compose up --build`.
