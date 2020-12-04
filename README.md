# CI

Gitlab CI templates for other projects

## Default section

The defaults only set up stages and default container versions for build and
others. Note that the containers referred are part of our
[base-image](https://gitlab.com/ModioAB/base-image) repo.


##  Container build example

See the  local .gitlab-ci.yml for example on how to use the container build.
It's meant to be used in conjugation with
[build.mk](https://gitlab.com/ModioAB/build.mk)


This job monopolizes the  `script`  section, allowing you to extend it with
`before_script` and `after_script`.

## SSH include

If you have a stage that needs to perform some kind of SSH auth, the ssh
include has a `before_script` that contains the relevant points.

It's really simple, starting the SSH agent and adding some public keys for
known remote hosts, which is the common prep for installing a package from a
git+ssh, or similar step.

This job monopolizes the `before_script` to set up ssh.

## Rebase job

The rebase job template sets up git alias named `every` that aliases `git
rebase` and is meant to be used with the `-x` feature of git, to run a command
on every commit.


    rebase:
       extends: .rebase
       script:
          -  git every -x 'make test'



Caveat: The rebase template will only run on Merge requests, so it should be
combined with a job that runs on tags and/or main branch as well.

Note that this job monopolizes the `before_script` to set up git.
