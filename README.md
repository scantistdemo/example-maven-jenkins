# Black Duck CoPilot Maven/Travis CI Example

[![Travis CI](https://travis-ci.org/BlackDuckCoPilot/example-maven-travis.svg?branch=test)](https://travis-ci.org/BlackDuckCoPilot/example-maven-travis) [![Black Duck Security Risk](https://test.duckbuild.io/github/groups/BlackDuckCoPilot/locations/example-maven-travis/public/results/branches/test/badge-risk.svg)](https://test.duckbuild.io/github/groups/BlackDuckCoPilot/locations/example-maven-travis/public/results/branches/test)

Shows a working setup for using the Black Duck CoPilot integration to analyze the risk of project dependencies

## Travis CI Setup

The `.travis.yml` file has been modified to upload the generated data to Black Duck CoPilot:

```yaml
after_success:
  - mvn com.blackducksoftware.integration:hub-maven-plugin:2.0.2:build-bom -Dhub.output.directory=. -Dhub.deploy.bdio=false
  - bash <(curl -s https://test.duckbuild.io/bash/travis) ./*_bdio.jsonld
```
