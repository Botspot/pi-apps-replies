# pi-apps-replies
This repository hosts messages to send back to Pi-Apps users who reported an error.

Over the past year, we've worked hard to improve the Pi-Apps error reporting system. Most installation failures are now diagnosed client-side and explained in simple terms to the user. Only a few errors still get through, but many of them are unique and can't be reproduced. Without a way to contact affected users, we have no way of solving these issues. Users are encouraged to reach out for help, but not everybody has a Github/Discord account.

That leaves us with only one option: **to make our own chat client.**

Pi-Apps error reports will soon be sent to https://paste.ee.
Replying to an error report will work like this:
- Someone from the Pi-Apps team (who has write access to this repository) will run a script to list recent error report logfiles.
- To reply, the script will do two things:
  - It will add a new line to a special file in this repository. Said line will be the sha256 hash of the original logfile.
  - It will also upload a new file to this repository that contains the reply text.

How Pi-Apps users will receive our replies:
- All Pi-Apps clients will periodically compare the sha256 sums of their local logfiles with the hashes found in this repository's list of hashes.
- If a match is found, a notification will appear to display the reply.

How will Pi-Apps users send a reply back?
- I haven't thought that far ahead. Feel free to contact me if you have an idea for how this can work.

To list all received error reports:
```bash
sudo apt install jq curl
curl "https://api.paste.ee/v1/pastes?perpage=200000" -H "X-Auth-Token: uaEcotUfhtDjVC1RoIW7YQuqZhCb7BchwFtIEfiSC" | jq
```
