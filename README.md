# Insights Operator Gatherting Conditions

This repository provides gathering conditions for the conditional gatherer
in the [Insights Operator](https://github.com/openshift/insights-operator) and [Insights Operator Condition Service](https://github.com/redhatinsights/insights-operator-gathering-conditions-service)

## Linting

```shell script
python3 -m venv .env
source .env/bin/activate
pip3 install -r requirements.txt
# to install the precommit script
pre-commit install
# to run the precommit script
pre-commit run --all-files
```

## Build

Just execute the script:

```shell script
./build
```

It will build the container image with the rules.


## Testing

`build.sh` script is tested using a Bats framework. To run the tests, run `test/test_helper/bats/bin/bats test/test.bats` from root directory of this repository.


# Docker image

You can create a Docker image that will share the rules folder with:

```
docker build -t io-gathering-conditions .
docker run --mount type=volume,source=.,target=/conditions io-gathering-conditions:latest
```
