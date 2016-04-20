default.xml
===============

    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
      <remote name="origin"
              fetch=".." />

      <default revision="refs/heads/master"
               remote="origin"
               sync-j="4" />

      <project path="project/A" name="LocalManifestsDemo/project-A" />
      <project path="project/B" name="LocalManifestsDemo/project-B" />
    </manifest>

local_manifests/default_local.xml
===============

    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
      <remove-project name="LocalManifestsDemo/project-A" />
      <project path="project/B" name="LocalManifestsDemo/project-B" revision="stable" />
      <project path="project/C" name="LocalManifestsDemo/project-C" />
    </manifest>

merged manifest.xml
===============

    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
      <remote name="origin"
              fetch=".." />

      <default revision="refs/heads/master"
               remote="origin"
               sync-j="4" />

      <project path="project/B" name="LocalManifestsDemo/project-B" revision="stable" />
      <project path="project/C" name="LocalManifestsDemo/project-C" />
    </manifest>

How To Use Local Manifests
===============

    $ repo init -u https://github.com/LocalManifestsDemo/manifests.git
    $ repo sync

You will see the local directory as:

    LocalManifestsDemo
    ├── A (master)
    └── B (master)

After you run the following commands:

	$ ./.repo/manifests/local_manifests.py
    $ repo sync

The local directory will be changed:

    LocalManifestsDemo
    ├── B (stable)
    └── C (master)