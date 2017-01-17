# django-polls

Polls service for Django.

## Installation

This projects uses Gradle (at least version 3.3) as its build system along with
a Docker and docker-compose wrapper for continuous development. On Debian Linux
distributions Gradle can be installed with the following commands:

```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:cwchien/gradle
sudo apt-get update
sudo apt-get install default-jdk gradle=3.4-0ubuntu1
```

If you prefer to install Docker and docker-compose (highly recommended) refer to
the [official instructions][install-docker-compose].

## Usage

To start the service get the project and install its dependencies. Once the
migrations have successfully been applied, run the development server
at `http://127.0.0.1:8000/`.

```bash
git clone https://github.com/marcbperez/django-polls
cd django-polls
sudo gradle dependencies
gradle install
gradle makeMigrations
gradle migrate
python manage.py runserver
```

To add this service module, start by declaring it in `settings.py` and include
the module's URL configuration in `urls.py`.

```python
INSTALLED_APPS = [
    ...
    'polls',
]
```

```python
urlpatterns = [
    ...
    url(r'^polls/', include('polls.urls')),
]
```

## Testing

Tests will be executed by default every time the project is built. To run them
manually start a new build or use Gradle's test task. For a complete list of
tasks check `gradle tasks --all`.

```bash
gradle test
```

A continuous build cycle can be executed with `gradle --continuous` inside a
virtual environment, or with Docker.

```
sudo docker-compose up
```

## Troubleshooting

The [issue tracker][issue-tracker] intends to manage and compile bugs,
enhancements, proposals and tasks. Reading through its material or reporting to
its contributors via the platform is strongly recommended.

## Contributing

This project adheres to [Semantic Versioning][semver] and to certain syntax
conventions defined in [.editorconfig][editorconfig]. To get a list of changes
refer to the [CHANGELOG][changelog]. Only branches prefixed by *feature-*,
*hotfix-*, or *release-* will be considered:

  - Fork the project.
  - Create your new branch: `git checkout -b feature-my-feature develop`
  - Commit your changes: `git commit -am 'Added my new feature.'`
  - Push the branch: `git push origin feature-my-feature`
  - Submit a pull request.

## Credits

This project is created by [marcbperez][author] and maintained by its
[author][author] and contributors.

## License

This project is licensed under the [Apache License Version 2.0][license].

[author]: https://marcbperez.github.io
[issue-tracker]: https://github.com/marcbperez/django-polls/issues
[editorconfig]: .editorconfig
[changelog]: CHANGELOG.md
[license]: LICENSE
[semver]: http://semver.org
[install-docker-compose]: https://docs.docker.com/compose/install/
