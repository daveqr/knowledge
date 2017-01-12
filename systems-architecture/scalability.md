# Scalability

## General

* with any system, there are at least two things to think about
 * amount of traffic (usage per second)
 * amount of data
* will want to know per/second usage (though it's sometimes easier to think about per month)
- bottlenecks
    - handling a lot of users
    - handling a lot of data
    - writing to a database is slow
- hosting options
    - shared hosting
    - VPS
        - virtual private server
        - get your own copy of the OS
        - data more private from other customers but not hosting company
    - Amazon Web Services — ECS
        - can spawn your own servers
        - can set up automated spawning and have those servers power off as traffic declines