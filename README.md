Tweet Cremator 🔥

A script that reads your embarrassing tweet history from your X archive and yeets it into the void, one `DeleteTweet` API call at a time. Because apparently you said a lot of things.

## How it works
1. You give it your login token and CSRF cookie (basically your house keys).
2. It reads `tweets.js` from your data archive so it doesn't have to beg X's flaky internal API for a list.
3. It deletes everything that matches your filters, politely waiting out rate limits like a well-behaved stalker.
4. If X says "401 Unauthorized" three times in a row, it gives up instead of screaming into the void forever — you're welcome.

## Setup
   1. X -> Settings -> Your Account -> Download an archive of your
      data. Wait for the email (can take hours).
   2. Unzip it, locate data/tweets.js (sometimes tweet.js).
   3. Post one throwaway test tweet, delete it manually via the
      normal UI, and in DevTools Network tab (filter: DeleteTweet)
      copy its x-client-transaction-id into delete_tid below, and
      confirm the query ID in the request URL still matches the
      one hardcoded in delete_tweets() further down. Update if not.
   4. Fill in authorization, client_tid, username below.
      csrf_token and user_id are read automatically from cookies.
   5. Paste this whole script into console (type "allow pasting"
      first if prompted), then drag tweets.js into the box that
      pops up and click Confirm.

## Warnings
- **Permanent.** No undo button. No regrets… well, fewer regrets.
- **Not an official API.** X can and will break this out of spite.
- **Your bearer token = your password.** Don't paste it in Discord. Or here, ideally, but too late now.
- **Might annoy X's automation police.** Use responsibly-ish.

Enjoy your clean slate. Or don't — you did this to yourself.
