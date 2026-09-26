# Postman API Checks

Import `Stockroom.postman_collection.json` into Postman. Optionally import and select `Stockroom-Local.postman_environment.json`.

The collection is ordered as an end-to-end demo: signup/login, profile and password reset, category/warehouse/location/product setup, stock movements, receipts/deliveries/transfers/adjustments, dashboard reads, then product cleanup. It captures the bearer token and created resource IDs as it runs.

## Local Demo Server

From `backend/`, start the API on the H2 test database:

```powershell
.\gradlew.bat bootTestRun
```

The test configuration enables `app.auth.otp.expose-code` so the OTP request response includes `debug_otp`, which the collection captures for the reset flow. This setting is only for local demos. Do not enable it in a shared or production environment; configure an email delivery provider for real password reset.

The application uses an ephemeral JWT signing key when `JWT_SECRET` is unset. Tokens are valid only until the API process restarts. Configure a stable secret of at least 32 bytes for longer sessions.

## cURL Import Example

To import one request from cURL in Postman, use **Import > Raw text** and paste:

```sh
curl --request GET \
  --url http://localhost:8080/api/health \
  --header 'Accept: application/json'
```

For the full endpoint suite, import the collection JSON instead of importing requests one at a time.