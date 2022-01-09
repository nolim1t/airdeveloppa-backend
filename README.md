# AirDeveloppa Backend

## Running (Docker)

```
# First two steps may no longer be needed

# Login as user nolim1t
docker login registry.gitlab.com -u nolim1t
# Enter personal access token as password
docker pull registry.gitlab.com/nolim1t/airdeveloppa-backend:latest

# Pull specific version
docker pull registry.gitlab.com/nolim1t/airdeveloppa-backend:v0.1.3
```

## Sample endpoints

### Register

**Endpoint:** https://backend.airdeveloppa.services/1/register

This endpoint automatically creates an authentication token for a device or checks to see if the authentication token exists. The purpose of this is to identify users in the system

This endpoint also lets an existing device re-validate an authentication token.


#### POST Parameters

- `device_id` (required. This should be a uuid generated by the device)
- `token` (not required if the uuid generated by the device exists, it should be kept private)

### List

**Endpoint:** https://backend.airdeveloppa.services/1/list

#### GET Parameters

- `lat` (not required or implemented)
- `lng` (not required or implemented)

### Verify

**Endpoint:** https://backend.airdeveloppa.services/1/verify

#### POST Parameters

- `token` (required. This is the authentication token. You should keep this safe)
- `id` (required. This is the device UUID)
- `fakeVerify` (for testing. If you set this to false this will simulate a fail response)

## Maintainer Notes

- Copy `env-dist` to `.env` before starting `docker-compose.yml`
- Have a `PERSONALTOKEN` variable set up in gitlab
- When releasing push a tag
