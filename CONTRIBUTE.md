# Contribute

No strict guidelines needed so far, just some hints down below. If you want to contribute just  open issues or pull requests.

## (optional) Using pre-commit framework

If you want some code checks to happen before every commit (as a nice reminder of what you forgot to clean up ;-) ), you can activate pre-commit.

In the root dir of this role run
```console
pip install pre-commit
pre-commit install
```
and you are good to go.

## Using python virtual environments

To be as close as possible to the environment that the CI pipeline will create you can use a [helper script](./create_venv.sh) to setup a fresh python virtual environment. Then call `source .venv/bin/activate` and you can call molecule etc.

## Maintenance scripts

In the dir maintenance/ are scripts that shall help to keep the code clean. Like to check if all molecule scenarios are placed at the corresponding place (matrix) in the test workflow for github. Call `python3 maintenance/run_checks.py` to use all of them together.

## Testing the role

Testing the role relies on some packages to be installed. You can make your life easy and just have a look at the section above about automatic python virtual environment creation. That way all the tooling is installed locally for this repo. Ohterwise have a look at the `requirements.txt` file in the `.github/workflows` directory for a list of (you guessed it) requirements.

With all the tooling: As a good starting point you can run
```console
molecule test --all
```
and see if everything works fine.