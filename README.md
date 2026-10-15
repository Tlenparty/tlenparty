## Hello!

Android developer: Kotlin, Java, Jetpack Compose, Kotlin Multiplatform.

## Featured: live delivery ETA for YamiYami

**Business problem.** Once a food order was "On the way", the customer saw only a static planned time
("Delivered today by 14:18"), with no idea where they were in the courier's route or when the courier would actually arrive.

**What I did, end to end**: from idea to working MVP to production architecture, across three codebases.

- **Customer app (YamiYami, Android):** a live countdown in the order card, refreshed every 10 s:
  "Arriving in N min", "The courier is at your door", "You're second in the route, by HH:MM". Any failure falls back
  to the planned time, so the screen is never worse than before. The courier pin on the map now moves smoothly
  instead of flickering.
- **Courier app (Android):** sends the courier's ordered route and location heartbeats; the service is optional
  and never blocks the courier.
- **[route-service](https://github.com/Tlenparty/route-service) MVP (private):** Node.js + Fastify with a self-hosted
  OSRM road graph of St. Petersburg. The ETA follows roads, bridges and one-way streets rather than a straight line,
  plus calibrated handover and last-leg time. It reuses the apps' existing auth with no tokens of its own, and filters
  implausible GPS fixes (jumps, points far from any road, a courier "teleported" to another city). A courier
  simulator drives real roads, including injected GPS glitches. Verified end to end on a real staging order.
- **System design for production:** moved the calculation into the company's existing Go backend, where courier
  locations and order data already flow, so phase 1 needs no courier-app release. Also designed per-courier ETA
  caching, order ownership checks, a three-level kill switch (single response, server toggle, client feature flag)
  and "promised vs delivered" calibration. Wrote the backend spec and shared reference test cases so the Go
  implementation matches the prototype exactly.

**Stack:** Kotlin, Jetpack Compose, Node.js, Fastify, OSRM, Docker Compose, system design for a Go + Kafka backend.

## Projects

### Android · Kotlin

| Project | Description | Stack |
|---|---|---|
| [Dictionary](https://github.com/Tlenparty/Dictionary) | English-Russian dictionary: search via the Skyeng API, favorites and history | MVVM, Koin, Coroutines, Retrofit, Room |
| [GithubUsers](https://github.com/Tlenparty/GithubUsers) | GitHub API client: users and repositories, offline cache | MVP (Moxy), RxJava 2, Dagger 2, Retrofit, Room, Cicerone |
| [PictureOfTheDay](https://github.com/Tlenparty/PictureOfTheDay) | NASA APOD Astronomy Picture of the Day | MVVM, Retrofit, Coil, Material Components |
| [WeatherApp](https://github.com/Tlenparty/WeatherApp) | Weather app on the Yandex Weather API with a map | MVVM, Koin, Coroutines, Retrofit, Room, Google Maps |
| [Translator](https://github.com/Tlenparty/Translator) | Dictionary on the Skyeng API with search history | MVVM, Koin, Coroutines, Retrofit, Room, Coil |
| [KodeTraineeDev](https://github.com/Tlenparty/KodeTraineeDev) | KODE take-home assignment: employee directory | MVP (Moxy), Cicerone, RxJava, Retrofit, Glide |
| [Stopwatch](https://github.com/Tlenparty/Stopwatch) | Stopwatch with two timers | MVVM, Coroutines/Flow, LiveData |

### Compose · Multiplatform

| Project | Description | Stack |
|---|---|---|
| [MyKMM](https://github.com/Tlenparty/MyKMM) | Kotlin Multiplatform starter project: Android and iOS | KMM, Compose, SwiftUI |
| [MyJetpackComposeProject](https://github.com/Tlenparty/MyJetpackComposeProject) | Profile card in Jetpack Compose | Jetpack Compose |

### Android · Java

| Project | Description | Stack |
|---|---|---|
| [Calculator](https://github.com/Tlenparty/Calculator) | Calculator with parentheses and percentages, reverse Polish notation, dark theme | Java, Material |
| [Notes](https://github.com/Tlenparty/Notes) | Notes: list, add and edit | Java, SQLite |

### Experiments & sandboxes

- [GlideCoilPicassoRoom](https://github.com/Tlenparty/GlideCoilPicassoRoom) — comparison of Glide, Coil and Picasso, Room database
- [AndroidBuildVariants](https://github.com/Tlenparty/AndroidBuildVariants) — build types, product flavors and source sets
- [Covid19DailyReport](https://github.com/Tlenparty/Covid19DailyReport) — app skeleton on MVP, Dagger 2 and Cicerone
- [NotesFirestore](https://github.com/Tlenparty/NotesFirestore) — prototype of card-style notes on Cloud Firestore
- [GeoQuiz](https://github.com/Tlenparty/GeoQuiz) — a mini "True / False" quiz
- [AndroidWidgetsDemo](https://github.com/Tlenparty/AndroidWidgetsDemo) — demo of standard Android widgets

### Java

- [Algorithms](https://github.com/Tlenparty/Algorithms) — own implementations of data structures and algorithms: lists, stacks, queues, trees, graphs, sorting
- [java-socket-chat](https://github.com/Tlenparty/java-socket-chat) — client-server network chat on sockets and JavaFX, Java Core exercises
- [Smokertelegram](https://github.com/Tlenparty/Smokertelegram) — multi-user chat: socket server, JavaFX client, SQLite, Log4j 2
- [java-concurrency-samples](https://github.com/Tlenparty/java-concurrency-samples) — multithreading (wait/notify, java.util.concurrent), JUnit 5, a mini annotation-based test framework
- [java-generics](https://github.com/Tlenparty/java-generics) — generic type examples
- [java-basics](https://github.com/Tlenparty/java-basics) — console programs: arrays, games, OOP basics
- [tic-tac-toe](https://github.com/Tlenparty/tic-tac-toe) — 5×5 tic-tac-toe against the computer
- [guess-games](https://github.com/Tlenparty/guess-games) — console games "Guess the Word" and "Guess the Number"

## Languages and Tools

![Kotlin](https://img.shields.io/badge/-Kotlin-090909?style=for-the-badge&logo=kotlin)
![Java](https://img.shields.io/badge/-Java-090909?style=for-the-badge&logo=openjdk)
![Android](https://img.shields.io/badge/-Android-090909?style=for-the-badge&logo=android)
![Jetpack Compose](https://img.shields.io/badge/-Jetpack%20Compose-090909?style=for-the-badge&logo=jetpackcompose)
![Kotlin Multiplatform](https://img.shields.io/badge/-Kotlin%20Multiplatform-090909?style=for-the-badge&logo=kotlin)
![Gradle](https://img.shields.io/badge/-Gradle-090909?style=for-the-badge&logo=gradle)
