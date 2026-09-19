BULK DELETE ALL TWEETS & REPLIES — archive-based

WHY ARCHIVE MODE: X's live timeline-fetch endpoints (UserTweetsAndReplies / UserTweets) use versioned query IDs + feature-flag blobs that X rotates often, and they've already 
broken once in this session. Archive mode skips that fetch entirely and only relies on the DeleteTweet endpoint, which is far more stable. This is why from_archive defaults to true below.

SETUP (do this first):

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

THIS IS IRREVERSIBLE. Test with a couple of IDs via delete_specific_ids_only first if you want to sanity-check before running it against your whole history.
