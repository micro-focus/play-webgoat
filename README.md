# play-webgoat

[![Twitter Follow](https://img.shields.io/twitter/follow/playframework?label=follow&style=flat&logo=twitter&color=brightgreen)](https://twitter.com/playframework)
[![Discord](https://img.shields.io/discord/931647755942776882?logo=discord&logoColor=white)](https://discord.gg/g5s2vtZ4Fa)
[![GitHub Discussions](https://img.shields.io/github/discussions/playframework/playframework?&logo=github&color=brightgreen)](https://github.com/playframework/playframework/discussions)
[![StackOverflow](https://img.shields.io/static/v1?label=stackoverflow&logo=stackoverflow&logoColor=fe7a16&color=brightgreen&message=playframework)](https://stackoverflow.com/tags/playframework)
[![YouTube](https://img.shields.io/youtube/channel/views/UCRp6QDm5SDjbIuisUpxV9cg?label=watch&logo=youtube&style=flat&color=brightgreen&logoColor=ff0000)](https://www.youtube.com/channel/UCRp6QDm5SDjbIuisUpxV9cg)

[![Build Status](https://github.com/playframework/play-webgoat/actions/workflows/build-test.yml/badge.svg)](https://github.com/playframework/play-webgoat/actions/workflows/build-test.yml)
[![Repository size](https://img.shields.io/github/repo-size/micro-focus/play-webgoat.svg?logo=git)](https://github.com/micro-focus/play-webgoat)
[![Scala Steward badge](https://img.shields.io/badge/Scala_Steward-helping-blue.svg?style=flat&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAQCAMAAAARSr4IAAAAVFBMVEUAAACHjojlOy5NWlrKzcYRKjGFjIbp293YycuLa3pYY2LSqql4f3pCUFTgSjNodYRmcXUsPD/NTTbjRS+2jomhgnzNc223cGvZS0HaSD0XLjbaSjElhIr+AAAAAXRSTlMAQObYZgAAAHlJREFUCNdNyosOwyAIhWHAQS1Vt7a77/3fcxxdmv0xwmckutAR1nkm4ggbyEcg/wWmlGLDAA3oL50xi6fk5ffZ3E2E3QfZDCcCN2YtbEWZt+Drc6u6rlqv7Uk0LdKqqr5rk2UCRXOk0vmQKGfc94nOJyQjouF9H/wCc9gECEYfONoAAAAASUVORK5CYII=)](https://scala-steward.org)
[![Mergify Status](https://img.shields.io/endpoint.svg?url=https://api.mergify.com/v1/badges/playframework/play-webgoat&style=flat)](https://mergify.com)

A vulnerable Play application for attackers.

For example, this shows where unvalidated input from the client can be improperly trusted by the application and included in the response. There is also a sample cross-site scripting vulnerability.

## Fortify SCA

The `main` branch of the repository configures sbt to translate the code for static analysis by Fortify SCA. The Fortify build ID is set to `play-webgoat` and the SCA version is set to `22.1` in `fortify.sbt`. If you have Fortify SCA on your machine, here are the commands to translate and scan the project:

```
sourceanalyzer -b play-webgoat -clean
sbt clean compile
sourceanalyzer -b play-webgoat -debug -logfile scan.log -scan -f play-webgoat.fpr
```

Once the scan is complete, you can either open the resulting FPR file in Audit Workbench (`auditworkbench play-webgoat.fpr`) or upload it to Fortify SSC Server.

The list of vulnerabilites Fortify finds is in [vulnerabilities.txt](https://github.com/playframework/play-webgoat/blob/fortify/vulnerabilities.txt).

For more information on Fortify SCA, see
[https://software.microfocus.com/en-us/products/static-code-analysis-sast/overview](https://software.microfocus.com/en-us/products/static-code-analysis-sast/overview).
Fortify's Scala support is documented at
[https://developer.lightbend.com/docs/fortify/latest/](https://developer.lightbend.com/docs/fortify/latest/).

## Running

```
sbt run
```

Then go to http://localhost:9000.

## Scala versions

Cross-building to Scala 2.12 and 2.13 is supported.
