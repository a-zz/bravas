# brⱯvⱯs - Development guidelines

## Development cycle

### Overview
Every **brⱯvⱯs** version is identified according to the version name scheme:

    v{major}.{minor}_{release}
    
Every **major version** is a consecutive integer number; since this isn't an 
ambitious project and is to be released since very early stages of development,
major version numbers start at 0. This is the current major version and there're
no plans to increase it in a foreseable future. Whether to increase it is 
unclear so far.

Every **minor version** is a consecutive number starting by 1. It should be 
increased whenever a new feature is added to **brⱯvⱯs**.

Major.minor versions are identified as branches in the project Git repository
as:

    v{major}.{minor}

Within major.minor version, releases are numbered with consecutive numbers 
assigned in the following fashion:

* Consecutive release candidates are named rc1, rc2, etc.
* Production-ready releases are named 1, 2, etc.

**Releases** are identified as tags, named as:

    v{major}.{minor}_{release}
    
Releases are very conveniently handled by GitHub, as it doesn't only create the
tag but also sets links for downloading the product. Release creation is to be
run on GitHub, therefore.

**The most important clause in the development cycle contract is that the 
js/metadata.json file structure isn't to be changed within a single minor 
version, so a production site upgraded through consecutive releases won't break. 
Upgrading from a minor version to a different one can / would generally require 
migrating the js/metadata.json file.**

### Development cycle procedure

Whenever to add a new feature to **brⱯvⱯs**, a new branch is to be added with
the name:

    v{major}.{minor}_unstable
    
The new branch will be usually derived from the master branch (see later), but
this really depends on the current status of the project. 

The suffix _"_unstable"_ marks the version / branch as ineligible for releases, 
so it shouldn't be tagged; not at least with tag names that could be mistaken as
release identificators.

**Once the branch is ready for release:**

0. No more commits are allowed on js/metadata.json

1. Rename the branch as

    v{major}.{minor}
    
2. Decide the new version number; maybe _v{major}.{minor}_rc1_ or 
   _v{major}.{minor}_1_, depending on estimated code maturity.

3. Update the version number in README.md and commit the change with the 
   message: "v{major}.{minor}_{release} ready!"

4. Create the new tag / release.

5. Merge the version branch into the master branch.

Released versions will usually be the subject of new releases (bug fixes and the
like). **When a branch is ready for a new release:**

1. Decide the new version number. Add 1 to the latest release, or maybe move
   from rc? to 1.

2. Update the version number in README.md and commit the change with the 
   message: "v{major}.{minor}_{release} ready!"

3. Create the new tag / release.

4. Only if the release is created on the latest branch: merge the version branch
   into the master branch.

## Code style
