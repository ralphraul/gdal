# GDAL Mirror Branch

This repository exists to allow us to build a custom branch of gdal with changes required for 1int to work optimally.

## Branches

This repo contains 2 branches, master and source.

- master: This branch is the one used to build the gdal artifacts by [mvn_gdal_build_w64](https://bitbucket.org/1spatial/mvn_gdal_build_w64/src/master/) and [mvn_gdal_build_lx86_64](https://bitbucket.org/1spatial/mvn_gdal_build_lx86_64/src/master/). It should be equal to a certain tag of the gdal public repo, with our changes applied on top.

- source: This should be an exact mirror of the gdal public repo at a certain tag. This should be equal to master without the custom changed we have made.

## How to update

To update the master to a new tag of the gdal branch:

- If you haven't already, add the gdal github repo as a new remote `git remote add github https://github.com/OSGeo/gdal.git`

- Switch to the source branch `git checkout source`

- Fetch the commits from github `git fetch github`

- Reset the branch to the desired tag `git reset --hard tags/v3.2.2`

- Verify that the latest commit is a 'Prepare for GDAL' commit.

- Switch back to master

- Rebase this branch on top of the source branch (avoid merging, as we don't want master to get cluttered with merge commits)

- Push both branches