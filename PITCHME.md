- jekyll and gehlenborglab.org
- django_docker_engine
- dagsheet

---

## jekyll and [gehlenborglab.org](https://github.com/hms-dbmi/gehlenborglab-website)

- Data
- Deployment
- Debugging

+++

### Data

```yaml
_config.yml:

collections:
  projects:
    output: true
    permalink: /research/:collection/:path/
  themes:
    output: true
    permalink: /research/:path/
  members:
    output: true
    permalink: /team/:collection/:path/
  publications:
    output: true
    permalink: /:collection/:path/
  news:
    output: true
    permalink: /:collection/:path/
```

```yaml
_data/grants.yml:

nih_k99hg007583:
  funder: National Institutes of Health - NHGRI
  number: NIH K99HG007583
  name: Visualization of (Epi)Genomic Data for Discovery of Disease-Associated Variants
  url: https://projectreporter.nih.gov/project_info_details.cfm?aid=9128459&icde=33407223
  summary: This proposal combines ...
  start: January 2014
  end: August 2015
  role: Principal Investigator
hsci_csbi:
  funder: Harvard Stem Cell Institute
  number: 
  name: Center for Stem Cell Bioinformatics
  url: 
  summary: 
  start: August 2014
  end: August 2018
  role: Co-Investigator
...
```

+++

### Deployment

```yaml
.travis.yml:

language: ruby
before_install:
  - npm install -g npm@3.10.9
before_script:
  - npm install
script:
  - set -e
  - bundle exec jekyll build
  - "! grep -n '<ERROR' -r _site"
  - bundle exec htmlproofer --alt-ignore '/.*/' --check-html --disable-external --assume-extension ./_site
deploy:
  provider: s3
  bucket: gehlenborglab.org
  skip_cleanup: true
  region: us-east-1
  acl: public_read
  local_dir: _site
  access_key_id: AKIAI37A5SUOEVYA5KOQ
  secret_access_key:
    secure: ...........
```
+++

### Debugging

---

## [django_docker_engine](https://github.com/refinery-platform/django_docker_engine)

---

## [dagsheet](https://github.com/mccalluc/dagsheet)
