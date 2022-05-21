[![Test](https://github.com/snow-actions/setup-jenkins/actions/workflows/test.yml/badge.svg)](https://github.com/snow-actions/setup-jenkins/actions/workflows/test.yml)

# Setup Jenkins

Set up Jenkins container (PoC).
A few features are available.

## Usage

1. Copy `$JENKINS_HOME/jobs/*/config.xml` from existing Jenkins to `jenkins_home/` in a repository  
or you can put `jenkins_home/jenkins.yaml` if [Jenkins Configuration as Code (JCasC)](#jenkins-configuration-as-code-jcasc)
1. Create a workflow with the jenkins_home path

```yml
steps:
  - uses: actions/checkout@v3
  - uses: snow-actions/setup-jenkins@v0.4.0
    with:
      jenkins_home: jenkins_home
  - run: wget $JENKINS_URL/jnlpJars/jenkins-cli.jar
  - run: java -jar jenkins-cli.jar -webSocket help
  - run: java -jar jenkins-cli.jar -webSocket build job-1 -f -v -p param_1=p1
```

## Inputs

See [action.yml](action.yml)

| Name | Description | Default | Required |
| - | - | - | - |
| `jenkins_image_tag` | [Jenkins image](https://hub.docker.com/r/jenkins/jenkins) tag | `lts-jdk11` | no |
| `jenkins_home` | Jenkins home path which will be<br>mounted to `/var/jenkins_home`.<br>Set `''` if you don't want to mount. | `${{ runner.temp }}/jenkins_home` | no |
| `env_file` | Jenkins container [env_file](https://docs.docker.com/compose/environment-variables/#the-env_file-configuration-option) path | - | no |

## Output environment variables

| Name | Description |
| - | - |
| `JENKINS_HOME` | Path to jenkins_home |
| `JENKINS_VERSION` | Jenkins version |
| `JENKINS_URL` | Jenkins URL: http://localhost:8080 |
| `COMPOSE_FILE` | Docker Compose variable as same as `--file`, `-f` option<br>You can access Jenkins container by `docker compose exec jenkins <command>` |

## Examples

### Workflow

See [test.yml](.github/workflows/test.yml)

### Jenkins Configuration as Code (JCasC)

See [jenkins.yaml](test-resources/jenkins.yaml)

Documents
- https://www.jenkins.io/doc/book/managing/casc/
- https://www.jenkins.io/projects/jcasc/
- https://plugins.jenkins.io/configuration-as-code/
- https://plugins.jenkins.io/configuration-as-code-groovy/
- https://plugins.jenkins.io/job-dsl/

## Supported

### Runners

- `ubuntu-20.04`
- `ubuntu-18.04`
- `self-hosted`

### Events

- Any

## Dependencies

- [Docker Compose V2](https://docs.docker.com/compose/)
- [Jenkins](https://hub.docker.com/r/jenkins/jenkins)

## Contributing

Welcome.
