# dmarc-import-lambda :postal_horn: :mailbox: #

[![Build Status](https://travis-ci.org/dhs-ncats/dmarc-import-lambda.svg?branch=develop)](https://travis-ci.org/dhs-ncats/dmarc-import-lambda)

`dmarc-import-lambda` contains code to build AWS Lambda functions that
utilize [`dmarc-import`](https://github.com/dhs-ncats/dmarc-import) to
parse DMARC aggregate reports.

## Examples ##

### All scanners ###

Building the environment zip files for all scanners and deploying them
to AWS Lambda using `domain-scan`:
1. `cd ~/dhs-ncats/dmarc-import-lambda`
2. `docker-compose build`
3. `docker-compose up`
4. `cp *.zip ~/18F/domain-scan/lambda/envs/`
5. `cd ~/18F/domain-scan`
6. `./lambda/deploy pshtt --create`
7. `./lambda/deploy sslyze --create`
8. `./lambda/deploy trustymail --create`

### One scanner ###

Building the `pshtt` environment zip file and deploying it to AWS
Lambda using `domain-scan`:
1. `cd ~/dhs-ncats/lambda_functions`
2. `docker-compose build build_pshtt`
3. `docker-compose up build_pshtt`
4. `cp pshtt.zip ~/18F/domain-scan/lambda/envs/`
5. `cd ~/18F/domain-scan`
6. `./lambda/deploy pshtt --create`

## Note ##

Please note that the corresponding Docker image _must_ be rebuilt
locally if the script `<scanner>/build_<scanner>.sh` changes.  Given
that rebuilding the Docker image is very fast (due to Docker's
caching) if the script has not changed, it is a very good idea to
_always_ run the `docker-compose build` step when using this tool.

## License ##

This project is in the worldwide [public domain](LICENSE.md).

This project is in the public domain within the United States, and
copyright and related rights in the work worldwide are waived through
the [CC0 1.0 Universal public domain
dedication](https://creativecommons.org/publicdomain/zero/1.0/).

All contributions to this project will be released under the CC0
dedication. By submitting a pull request, you are agreeing to comply
with this waiver of copyright interest.