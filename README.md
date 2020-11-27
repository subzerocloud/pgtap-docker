# docker-pgtap

pgTAP - Unit testing for PostgreSQL.

This is a docker image that contains pgTAP.

## About pgTAP

> pgTAP is a suite of database functions that make it easy to write TAP-emitting unit tests in psql scripts or xUnit-style test functions. The TAP output is suitable for harvesting, analysis, and reporting by a TAP harness.

From: [pgTAP: Unit testing for PostgreSQL](http://pgtap.org/)

## Install

This docker image is available as an automated build on [the docker registry hub](https://registry.hub.docker.com/r/subzerocloud/pgtap), so using it is as simple as running:


```console
$ docker run subzerocloud/pgtap:pg11
```

## How to use this image

### Start a postgres instance

```console
$ docker run --name db-under-test -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```
then fill the database with tables and data, using something you want to test.

### Execute the tests

```console
$ docker run -i -t --rm --name pgtap --link db-under-test:db -e PASSWORD=postgres -v /local/folder/with/tests/:/test subzerocloud/pgtap:pg11
```

Environment variables:

* DATABASE
* HOST=db
* PORT=5432
* USER="postgres"
* PASSWORD=""
* `TESTS="/test/*.sql"`

A full demonstration can be found at [harobed/poc-postgresql-pgTAP](https://github.com/harobed/poc-postgresql-pgTAP)

## License

### Docker packaging

(this project)

Copyright (C) 2017 [LREN CHUV](https://www.unil.ch/lren/en/home.html)
Copyright (C) 2019 [subZero](https://subzero.cloud)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Initial packaging done by Andreas Wålm <andreas@walm.net>

### pgTAP

[pgTAP license](https://github.com/theory/pgtap#copyright-and-license)

Copyright (c) 2008-2016 David E. Wheeler. Some rights reserved.

Permission to use, copy, modify, and distribute this software and its documentation for any purpose, without fee, and without a written agreement is hereby granted, provided that the above copyright notice and this paragraph and the following two paragraphs appear in all copies.

IN NO EVENT SHALL DAVID E. WHEELER BE LIABLE TO ANY PARTY FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES, INCLUDING LOST PROFITS, ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN IF DAVID E. WHEELER HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

DAVID E. WHEELER SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE SOFTWARE PROVIDED HEREUNDER IS ON AN "AS IS" BASIS, AND DAVID E. WHEELER HAS NO OBLIGATIONS TO PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.

# Acknowledgements

This work has been funded by the European Union Seventh Framework Program (FP7/2007­2013) under grant agreement no. 604102 (HBP)

This work is part of SP8 of the Human Brain Project (SGA1).
