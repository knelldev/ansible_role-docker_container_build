# docker.container.build

This include_role builds a docker container. The user id for docker container mapping is automatically computed.

## Requirements
- knelldev.docker_install

## Variables
| Name | Default | Type | Description |
| --- | --- | --- | --- |
| app_user | "{{ os_user }}" | str | The user name for the docker container build args. |
| app_path | "{{ storage_base_path }}/{{ app_name }}" | str | The app base path. Can be omitted if app_build_path is set. |
| app_build_path | "{{ app_path }}/build" | str | The app build path. Typically this folder will contain the Dockerfile. |
| app_build_args | {} | dict | The args for the build as dict. By default, app_gid and app_uid will be added automatically. |
| app_imagename | hello-world | str | The name of the docker image to be built. |
| app_version | latest | str | The tag of the docker image to be built. |
| app_push | False | boolean | If true, the docker image will be pushed to the docker image registry, otherwise False |

## Dependencies
None

## Minimal example
```yaml
- name: Build docker container image
  include_role:
      name: docker.container.build
  vars:
      app_user: app
      app_imagename: app
      app_version: latest
```

## Full example
```yaml
- name: Build docker container image
  include_role:
      name: docker.container.build
  vars:
      app_user: app
      app_path: /opt/app
      app_build_args:
        DEPENDENCY_VERSION: 1.0
      app_imagename: app
      app_version: latest
      app_push: False
```

## License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Contributors
- [knelldev](https://github.com/knelldev)
- [CSteinmetz15](https://github.com/CSteinmetz15)