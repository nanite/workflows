# workflows

Shared github workflows for any of our projects. You can use them at your own risk. They may be changed without warning.

## Avilable Workflows

We currently have a few workflows included as standard. They make wild assumptions on your setup and version naming so be careful with how you use them.

**Always check the files and their defaults!**

### `base-java.yml`

This is a basic but comprehensive workflow for any gradle based project. It supports caching, any amount of gradle tasks to run, and allows you to define your own java version.

### `standard-release.yml`

This is intended for any normal Minecraft mod release using Forge or Fabric. We make some assumptions about the files you'll want to release but this can be modified.

We do the following:

- Run `base-java.yml`
  - With `build publish`
  - We defualt a task of `curseforge` to release to curseforge for you. You can leave it blank if you don't want to release to curseforge
  - Release to github with a configurable changelog file.
    - This only happens if the github ref is a tag meaning it won't attempt to release to github when a tag is not set.

### `standard-arch-release.yml`

The arch release refers to `architectury` and makes some assumptions about the naming schema. A compliant schema is ` accelerated-decay-fabric-2.0.0+mc1.19.3.jar` for example. This means you must have the follow `name-[version (semver)]+mc(mc version).jar`. If this is not the case, it will not find the assets.

We do the follow:

- Run `standard-release.yml`
  - Set the publish task to `curseforgePublish`
  - Set the filename schema, you can customise this.