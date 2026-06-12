# lift-persistence

A maintenance fork of the [Lift Framework](https://github.com/lift/framework)'s persistence layer, stripped down to a single artifact.

Upstream Lift 4.0.0 removed all persistence modules (`lift-mapper`, `lift-db`, `lift-proto`). This fork keeps them alive — without the web framework — for projects that still rely on Mapper as their ORM.

## What's in the artifact

One module, `lift-persistence`, merging the former:

- `lift-common` — `Box`, `Logging`, and core abstractions
- `lift-util` — helpers, props, security utilities
- `lift-db` — JDBC abstraction and connection management
- `lift-proto` — `ProtoUser` and friends
- `lift-mapper` — the Mapper ORM

## What was removed

- All web modules (`lift-webkit`, templating, Comet, SiteMap, …)
- `lift-json` — consumers should migrate to [json4s](https://github.com/json4s/json4s)
- `lift-actor` and `LAFuture`
- `lift-markdown`

## Usage

Via [JitPack](https://jitpack.io):

```xml
<repositories>
  <repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
  </repository>
</repositories>

<dependency>
  <groupId>com.github.hongwei1.lift-persistence</groupId>
  <artifactId>lift-persistence_2.12</artifactId>
  <version>v1.0.0</version>
</dependency>
```

Cross-built for Scala 2.12 and 2.13.

## Project layout

The library lives in the `lift-persistence/` subproject on purpose: JitPack
names sbt artifacts by module, so the named subproject publishes as
`com.github.hongwei1.lift-persistence:lift-persistence_<scalaVersion>`.
A flattened root project would publish under the repository name without
the Scala version suffix. Do not flatten.

## Building

```
sbt clean +test +publishM2
```

Requires JDK 8+ (CI runs JDK 11).

## License

Apache License 2.0 — see [LICENSE.txt](LICENSE.txt). Original code copyright WorldWide Conferencing, LLC.
