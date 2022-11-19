# ansible-role-docker-container-minio

Role to run Minio in a docker container

## Table of content

- [Default Variables](#default-variables)
  - [docker_container_minio_command](#docker_container_minio_command)
  - [docker_container_minio_env](#docker_container_minio_env)
  - [docker_container_minio_image](#docker_container_minio_image)
  - [docker_container_minio_labels](#docker_container_minio_labels)
  - [docker_container_minio_name](#docker_container_minio_name)
  - [docker_container_minio_networks](#docker_container_minio_networks)
  - [docker_container_minio_ports](#docker_container_minio_ports)
  - [docker_container_minio_volume_dir](#docker_container_minio_volume_dir)
  - [docker_container_minio_volumes](#docker_container_minio_volumes)
  - [docker_image_minio_name](#docker_image_minio_name)
  - [docker_image_minio_pull](#docker_image_minio_pull)
  - [docker_network_minio_name](#docker_network_minio_name)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### docker_container_minio_command

#### Default value

```YAML
docker_container_minio_command: server /export --console-address ":9001"
```

### docker_container_minio_env

Dictionery of key,value pairs for docker environment variables to configure minio.

#### Default value

```YAML
docker_container_minio_env:
  MINIO_ROOT_USER: minio_admin
  MINIO_ROOT_PASSWORD: somesecret
```

### docker_container_minio_image

Repository path and tag used to create the container. If an image is not found or pull is true, the image will be pulled from the registry. If no tag is included, latest will be used.

#### Default value

```YAML
docker_container_minio_image: '{{ docker_image_minio_name }}'
```

### docker_container_minio_labels

Dictionary of key value pairs for container labels.

Example:

```yaml

docker_container_minio_labels:

traefik.enable: "true"

```

#### Default value

```YAML
docker_container_minio_labels: {}
```

### docker_container_minio_name

Name for the container

#### Default value

```YAML
docker_container_minio_name: minio
```

### docker_container_minio_networks

List of networks the container belongs to.

#### Default value

```YAML
docker_container_minio_networks:
  - name: '{{ docker_network_minio_name }}'
```

### docker_container_minio_ports

List of ports to publish from the container to the host.

#### Default value

```YAML
docker_container_minio_ports:
  - 9000:9000
  - 9001:9001
```

### docker_container_minio_volume_dir

Volume mount host directory, where Treafik config files are stored.

#### Default value

```YAML
docker_container_minio_volume_dir: '{{ docker_container__base__volume_dir }}/{{ docker_container_minio_name
  }}'
```

### docker_container_minio_volumes

List of volumes to mount within the container.

#### Default value

```YAML
docker_container_minio_volumes:
  - '{{ docker_container_minio_volume_dir }}/export:/export'
  - '{{ docker_container_minio_volume_dir }}/config:/root/.minio'
```

### docker_image_minio_name

Repository path and tag for the container image.

#### Default value

```YAML
docker_image_minio_name: minio/minio:latest
```

### docker_image_minio_pull

Indicate to always pull the docker image.

#### Default value

```YAML
docker_image_minio_pull: no
```

### docker_network_minio_name

Name of the docker network created for minio.

#### Default value

```YAML
docker_network_minio_name: '{{ docker_container_minio_name }}_backend'
```

## Discovered Tags

**_docker-container-prereq-all_**\
&emsp;Ensure all pre-requisites are installed

**_docker-container-prereq-minio_**\
&emsp;Ensure all pre-requisites for minio are installed

**_docker-container-purge-all_**\
&emsp;Remove all containers and delete volume mounts.

**_docker-container-purge-minio_**\
&emsp;Remove minio and delete volume mounts.

**_docker-container-remove-all_**\
&emsp;Remove all containers.

**_docker-container-remove-minio_**\
&emsp;Remove minio.

**_docker-container-setup-all_**\
&emsp;Run setup task for all containers.

**_docker-container-setup-minio_**\
&emsp;Run setup task for minio.

**_never_**


## Dependencies

None.

## License

license (GPL-2.0-or-later, MIT, etc)

## Author

andif888
