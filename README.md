# minecraft-modpack-rosecake

[![Build Status](https://img.shields.io/travis/rremer/minecraft-modpack-rosecake/master)](https://travis-ci.org/github/rremer/minecraft-modpack-rosecake)
[![Maven Central](https://img.shields.io/maven-central/v/com.github.rremer/minecraft-modpack-rosecake?versionPrefix=1.20.6-1)](https://search.maven.org/artifact/com.github.rremer/minecraft-modpack-rosecake-client/1.20.6-1/jar)
[![Docker Tag](https://img.shields.io/docker/v/rremer/minecraft-modpack-rosecake/1.20.6-1?label=docker)](https://hub.docker.com/repository/docker/rremer/minecraft-modpack-rosecake/general)
[![License](https://img.shields.io/github/license/rremer/minecraft-modpack-rosecake)](https://opensource.org/licenses/MIT)
[![Keybase PGP](https://img.shields.io/keybase/pgp/rremer)](https://keybase.io/rremer/pgp_keys.asc)

A Fabric/datapack vanilla-substitute for Minecraft.

## Usage

Currently, this modpack is distributed as a [MultiMC] zip.

1. If you don't have Java 17+, install it. Here's a recent build for [Windows](https://cdn.azul.com/zulu/bin/zulu17.32.13-ca-jdk17.0.2-win_x64.msi), [MacOs](https://www.azul.com/downloads/?version=java-17-lts&os=macos&architecture=x86-64-bit&package=jdk), [Linux](https://www.azul.com/downloads/?version=java-17-lts&os=linux&architecture=x86-64-bit&package=jdk)
2. [Download MultiMC] and install.
3. Open MultiMC and and add login credentials
4. Click "Add Instance" and select "Import from zip" on the left-hand side.
5. Paste in this URL: [MMC client release 1.20.6-1] and hit <Enter> 
6. When the download finishes, double-click 'minecraft-modpack-rosecake-client-1.20.6-1.zip'
7. If you are not signed into a Mojang account, you will be promted for credentials

## Features

This modpack aims to be 'Vanilla+', so primarily quality-of-life features have been added, but also some gameplay additions which are in keeping with Minecraft lore.

### Quality of Life

Here' a summary of the quality-of-life features provided by this modpack.

#### Recipe and Loot Table Fixes

Wither skeletons have a much higher chance of dropping a wither skull.

#### Just Enough Items (JEI), Just Enough Resources (JER)

Open your inventory to get a sidebar of searchable items and their recipes. Additionally see natural resources and their spawn distributions.

#### Lithium/Iris/Sodium/Shaderpacks

Lithium is included to speed up framerate. Iris is included along with the 'Complementary Shaders' pack, so if you want fancy current-gen graphics and lighting, you can toggle that on.

#### Fast Leaf Decay

Chopping down a tree's logs won't leave leaves in the air forever.

### Gameplay

Here's a summary of the gameplay changes itroduced in this modpack.

#### Extra Block, Crop variants

Croptopia implements fruiting trees and vegetables into world generation, along with extra higher tier foods and kitchen crafting items to make them. Slab/stair/polished variants of many blocks are added.


## Building

```sh
mvn clean install
```

## Server Usage

A container image is shipped to [docker.io/rremer/minecraft-modpack-rosecake]. You can start it via:
```sh
docker run -d \
  -p 25565:25565 \
  -e EULA_MINECRAFT_BOOL=true \
  -v /path/to/persistent/world:/minecraft-modpack-rosecake/.minecraft/world \
  -v /path/to/persistent/backup:/minecraft-modpack-rosecake/.minecraft/backup \
  rremer/minecraft-modpack-rosecake:1.20.6-1
```
... where ```/path/to/persistent``` is some real local filesystem to persist the world data between container restarts.


## Releasing

```sh
mvn versions:set -DnewVersion=1.20.6-1
mvn clean deploy -Dparameter.gpg.skip=false
mvn site site-deploy
```

### Versioning

A version number of this project's artifacts is built as ```<minecraft.version>-<project.version>```, where:
* ```minecraft.version``` is a version of minecraft (1.15.2, 20w10a ...)
* ```project.version``` is an increment for this project to release against a version of minecraft (1,2,3, ...)

[MultiMC]:https://multimc.org/
[Download MultiMC]:https://multimc.org/#Download
[MMC client release 1.20.6-1]:https://repo.maven.apache.org/maven2/com/github/rremer/minecraft-modpack-rosecake-client/1.20.6-1/minecraft-modpack-rosecake-client-1.20.6-1.zip
[docker.io/rremer/minecraft-modpack-rosecake]:https://hub.docker.com/r/rremer/minecraft-modpack-rosecake/tags
