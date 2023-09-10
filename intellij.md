# Intellij

## Changing project SDK

1. Go to Project Structure by pressing Cmd-; or by navigating to File > Project Structure.

1. Under Project Settings > Project, choose the SDK from the SDK dropdown.

1. If the desired SDK is not listed, you can add it by clicking on Add SDK and then selecting Download SDK.

1. Choose the desired version of the SDK you want to add and click Download.

## Internal caches problems

Clearing and rebuilding internal caches can resolve issues caused by corrupted caches or unexpected behavior. For instance, if you are unable to download or load project dependencies, invalidating the cache can often resolve the problem.

```
File -> Invalidate Caches -> Invalidate and Restart
```