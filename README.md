# twitter-timeline-bug

### Embedding the Twitter Timeline breaks site layout in Safari iPhone under some circumstances.

#### Twitter Names that are long and contain emoji (this does not seem to happen when the name is long but does not contain emoji)


| Safari iPhone | Chrome Android | "Fix" for Safari iPhone |
| --- | --- | --- |
| <img src="files/broken-long-names-with-emoji.png" width="250" alt="broken-long-names-with-emoji"/> | <img src="files/long-names-chrome-android.png" width="250" alt="long-names-chrome-android"/> | <img src="files/fixed-long-names-with-emoji.png" width="250" alt="fixed-long-names-with-emoji"/> |

The bug in action can be seen here: https://jordinl83.github.io/twitter-timeline-bug/?user=BugLongNames
<br/>
And the fix here: https://jordinl83.github.io/twitter-timeline-bug/?user=BugLongNames&fix=1

#### Tweets that link to other tweets

| Safari iPhone | Chrome Android | "Fix" for Safari iPhone |
| --- | --- | --- |
| <img src="files/broken-tweet-urls.png" width="250" alt="broken-tweet-urls"/> | <img src="files/tweet-urls-chrome-android.png" width="250" alt="long-names-chrome-android"/> | <img src="files/fixed-tweet-urls.png" width="250" alt="fixed-tweet-urls"/> |

Note that there's another issue when quoting another tweet, the tweet URL appears twice...

The bug in action can be seen here: https://jordinl83.github.io/twitter-timeline-bug/?user=BugTweetURLs
<br/>And the fix here: https://jordinl83.github.io/twitter-timeline-bug/?user=BugTweetURLs&fix=1

### FIX

This is more a hack than a fix, but a way around this issue would be to add the following style to the embedded tweets iframe:

```css
.TweetAuthor { max-width: 300px; text-overflow: ellipsis; }
.timeline-Tweet-text a:not(.customisable) { word-break: break-all; }
```

This needs to be done with JS, see [here](https://github.com/jordinl83/twitter-timeline-bug/blob/master/index.html#L37-L52) for how it can be accomplished.
