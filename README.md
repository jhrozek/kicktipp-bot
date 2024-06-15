# kicktipp-bot

This script can automatically enter tips into Kicktipp based on the quotes of the bookmakers. It is written in Python and uses Selenium to interact with the website.

## Run

Copy the contents of the `.env.example` file into a new file called `.env` and fill in the values.

Execute the commands below in the `Terminal`-Program. Pre-requisites are `Python`, `pip` and `Docker`.

```bash
# Get Image
docker pull ghcr.io/antonengelhardt/kicktipp-bot:amd64

# Run Container and set your env variables
docker run \
-it \
--name kicktipp-bot \
--platform linux/amd64 \
--env-file .env \
ghcr.io/antonengelhardt/kicktipp-bot:amd64
```

## Environment Variables

| Variable | Description | Example | Required |
| --- | --- | --- | --- |
| `KICKTIPP_EMAIL` | Your Kicktipp email | `email@example.com` | Yes |
| `KICKTIPP_PASSWORD` | Your Kicktipp password | `password` | Yes |
| `KICKTIPP_NAME_OF_COMPETITION` | The name of the competition you want to tip for | `mycoolfriendgroup` | Yes |
| `KICKTIPP_HOURS_UNTIL_GAME` | The script will tip games which start in the next x hours | `24` | No |
| `CHROMEDRIVER_PATH` | The path to the chromedriver binary | `/usr/bin/chromedriver` | No |
| `ZAPIER_URL` | The URL of your Zapier Webhook | `https://hooks.zapier.com/hooks/catch/123456/abcdef/` | No |

## Zapier Integration

If you want to receive a notification when the script tips for a match, you can use the Zapier integration. Please create a Zapier Account and set up the following Trigger: Custom Webhook. Please also make sure you set the ENV Variable `ZAPIER_URL` to the URL of your custom webhook. Then you can set up actions like sending an email or a push notification.
