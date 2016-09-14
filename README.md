Images builder
============
# Usage

	./build.sh
	Usage: build.sh PATH_TO_SEARCH REGISTRY BASE_NAME BRANCH [DEFAULT_BRANCH=master [TAG_REQUIRED_FOR_BRANCH=false]]

# Naming convension 

## TAG_REQUIRED = true

All images should have names start with repository name e.g. `operations/docker-images` (You can use `BASE_NAME` to setup main prefix)


Builder will collect all Dockerfile-s from all subdirectories and append name of all directories to the name of image.

Examples:
* `percona/5.6/Dockerfile` : `operations/docker-images/percona/5.6`
* `application/Dockerfile` : `operations/docker-images/application`
* `Dockerfile` : `operations/docker-images` (try to avoid please)

 If Dockerfile has prefix (e.g. Application.Dockerfile) this preffix goes to name

Examples:
* `percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6/5.6.7`
* `php/application.Dockerfile` : `operations/docker-images/php/application`
* `Application.Dockerfile` : `operations/docker-images/application`

If builder use `feature` branch of repo (not master), name of branch will go to tag

Examples:
* `percona/5.6/Dockerfile` : `operations/docker-images/percona:5.6:feature`
* `application/Dockerfile` : `operations/docker-images/application:feature`
* `Dockerfile` : `operations/docker-images:feature` (try to avoid please)
* `percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6/5.6.7:feature`
* `php/application.Dockerfile` : `operations/docker-images/php/application:feature`
* `Application.Dockerfile` : `operations/docker-images/application:feature`

## TAG_REQUIRED != true

In case `TAG_REQUIRED != true` tag will not be created and last part of image path and branch name will be spllited by slashes (if branch equal to default)

Example:
* percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6/5.6.7/feature (for feature branch)
* percona/5.6/5.6.7.Dockerfile` : `operations/docker-images/percona/5.6/5.6.7 (for master branch)

