**Core API** — collection of wrappers around Digital Ocean API. It's widely used by this gem (User API is just a shortcuts to Core API), and can be used by application developers too. Sometimes it have some extended features, not seen in User API, but it they exists, they're very unstable and probably buggy.

**WARNING: Core API is unstable. No one guarantees that in next version it's behaviour will be the same. We strongly recommends you to use User API instead!**

It may be changed in any minor or patch release — if Digital Ocean updates their API, Core API updates too as soon as possible. Core API changes will not affect User API in current release cycle (0.x.x User API will always work as expected before).

## Why Core API undocumented?

See the Core API description above.

We, authors of this gem, think that there's no reason to cover Core API in documentation, because:

1. Source code is my best friend. If you ready to use Core API, you will read the source code. We wrote Oceanarium simple and sources are simple too.
2. Unstability. Tomorrow Digital Ocean will update API and what? Core API will be changed, User API will be the same. Because of this we will not cover Core API in documentation — so, documentation will be always up-to-date.
3. Buggy. Some extended features may be buggy. We don't want to support it.
4. Read the above text, please.
