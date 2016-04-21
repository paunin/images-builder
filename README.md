Base images
============

# Naming convension

All images should have names start with repository name e.g. `operations/docker-images`


Builder will collect all Dockerfile-s from all subdirectories and append name of all directories to the name of image.
Last directory in the path to any Dockerfile will be a tag for image.

Examples:
* `percona/5.6/Dockerfile` : `operations/docker-images/percona:5.6`
* `application/Dockerfile` : `operations/docker-images:application`
* `Dockerfile` : `operations/docker-images` (try to avoid please)

 If Dockerfile has prefix (e.g. Application.Dockerfile) this prefix will go to tag and last directory in path will go to name of

Examples:
* `percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6:5.6.7`
* `php/application.Dockerfile` : `operations/docker-images/php:application`
* `Application.Dockerfile` : `operations/docker-images:application`

If builder use `feature` branch of repo (not master), name of branch will be used as suffix for the tag.

Examples:
* `percona/5.6/Dockerfile` : `operations/docker-images/percona:5.6-feature`
* `application/Dockerfile` : `operations/docker-images:application-feature`
* `Dockerfile` : `operations/docker-images:feature` (try to avoid please)
* `percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6:5.6.7-feature`
* `php/application.Dockerfile` : `operations/docker-images/php:application-feature`
* `Application.Dockerfile` : `operations/docker-images:application-feature`
