# Black Duck CoPilot Maven/Travis CI Example

[![Travis CI](https://travis-ci.org/BlackDuckCoPilot/example-maven-travis.svg?branch=test)](https://travis-ci.org/BlackDuckCoPilot/example-maven-travis) [![Black Duck Security Risk](https://copilot.blackducksoftware.com/github/groups/BlackDuckCoPilot/locations/example-maven-travis/public/results/branches/validation/badge-risk.svg)](https://copilot.blackducksoftware.com/github/groups/BlackDuckCoPilot/locations/example-maven-travis/public/results/branches/validation)

This branch shows a working setup for Black Duck CoPilot's validation server.
An example for public use can be found [here](https://github.com/BlackDuckCoPilot/example-maven-travis).

## Travis CI Setup

The `.travis.yml` file has been modified to upload the generated data to Black Duck CoPilot:

```yaml
after_success:
  - mvn com.blackducksoftware.integration:hub-maven-plugin:2.0.2:build-bom -Dhub.output.directory=. -Dhub.deploy.bdio=false
  - bash <(curl -s https://copilot.blackducksoftware.com/bash/travis) ./*_bdio.jsonld
```
