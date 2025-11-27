# DIME-Zenith.Docker
Running DIME Zenith in Docker

## General

```
cd ~

# run container
docker run \
  -p 8080:8080 \
  -e MongoDb__ConnectionString="mongodb://username:password@mongodb:27017" \
  -e MongoDb__DatabaseName="dime_zenith" \
  -e Zenith__TaskGenerationThresholdSeconds=60 \
  --rm
  datainmotionenterprise/zenith:latest
```

## Full Compose

```
cd ~

# clone repository
git clone https://github.com/DataInMotionEnterprise/DIME-Zenith.Docker

cd DIME-Zenith.Docker

# configure environment
cp .env.example .env
nano .env  # set ZENITH_DOMAIN and LETSENCRYPT_EMAIL

docker compose up -d
```

**Prerequisites:**
- DNS A record for your subdomain (e.g., `zenith.your-domain.com`) pointing to your server's IP
- Ports 80 and 443 open on your firewall

**Environment Variables (.env):**
- `ZENITH_DOMAIN` - Your subdomain (e.g., `zenith.your-domain.com`)
- `LETSENCRYPT_EMAIL` - Email for Let's Encrypt certificate notifications

**Access:**
- `https://zenith.your-domain.com`