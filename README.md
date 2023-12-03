# Kamal static site template

This is a template for a static site that can easily be deployed to a single server together with other static sites with [Kamal](https://kamal-deploy.org/).

The site is automatically configured with SSL certificates from [Let's Encrypt](https://letsencrypt.org/), and is served via [nginx](https://nginx.org/).

## First setup

On a freshly created server, run:

```sh
ssh root@SERVER_IP_ADDRESS -- mkdir -p /letsencrypt && touch /letsencrypt/acme.json && chmod 600 /letsencrypt/acme.json
```

Than edit the `.env` file and `config/deploy.yml` and enter your configuration.

First ensure that you've set `GIT_URL` to a repository address with a valid access token embedded in the `.env` file. This access token must have access to pull from the git repository in question (see [personal access tokens for GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) for an example).

Then you must also setup an access token for your Docker image repository (see [Create and manage access tokens for Docker Hub](https://docs.docker.com/security/for-developers/access-tokens/) for an example).

Finally, you must add the server address into `config/deploy.yml`, and ensure that the image and repository configurations are correct.

Than run `kamal setup` to setup the server for the first time.

## Adding a new site to the server

1. Create a new git repository for the project
2. Edit `.env` and `config/deploy.yml`
3. Push the changes to git
4. Run: `kamal env push`
5. Run `kamal deploy`

## Deploying configuration changes

If you change the configuration, run `kamal deploy` to deploy the changes to the server. It takes about 60 seconds.

## Deploying site changes

Changes checked into git are automatically pulled onto the Kamal server every 10 seconds. So all you have to do is checkin your changes and push them.
