# Caching Intermediate Result

In the case of serving web content, caching is important as most of the content tend to be similar. However, for dynamic website such as amazon, netflix the website have archive  personalization. The goal here is to reduce computation power. 

# Idea
Imagine 100 identical request incoming to server. Since at `time=0` there is nothing cached yet. Hence this 100 requests will be directly processed by server which proceed to crash itself.

The solution is elect 1 request as `sentry` while the rest go into `sleep`. `sentry` will cache the result into disk and return to the client. The rest 99 request is awake and return with cached content.

If no contents found after awoken, error can be promptly returned. 

## Main Issue to Solve
1. Repeative processing same request is wasteful. 
2. Caching mechanism must expect burst request. 
3. Making sure cache content is always needed. (In the case of `pre-cache`)

## Caveat
1. Such caching mechanism will not reflect realtime change.  
 - If database is updated, caching will continue to use outdated information until it is expired. 
 - If database does not updating during cache expiration, then refreshing cache is wasteful processing. 

## Implementation detail 
1. Design a `lock`, for every `request` there is two key. 
 - lock key
 - cache key.
2. When request `miss` cache, it will obtain the `lock` and designated as `sentry`
 - rest of the request will `sleep` in the case of `miss` and failure to obtain lock. 