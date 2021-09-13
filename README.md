# compliance-confluence
A repo that builds out a compliance confluence, based on pre-defined templates.

## Building
Source originally from 
Creating documents from here:
[Jupiter One Policy Builder](https://github.com/JupiterOne/security-policy-builder)
[Jupiter One Templates](https://github.com/JupiterOne/security-policy-templates)

First build in Docker, from root of any directory:
```shell
docker run -it -v "$PWD":/mnt --rm jupiterone/pspbuilder psp build -o /mnt/docs -p /mnt/partials -s /mnt/templates
```
Subsequent builds (like this repo)

```shell
docker run -it -v "$PWD":/mnt --rm jupiterone/pspbuilder psp build -t /mnt/templates -o /mnt/docs -p /mnt/partials -c /mnt/templates/config.json
```

Do not put [docs](./docs) and [partials](./partials) in to source control because they are generated.

## Publishing to Confluence

Docker version: not worked out how to use. The `confluence-pages.json` is save somewhere unknown and so can't be re-used.

```shell
# works with real username and password (not tried with token)
psp publish --confluence --site <your-confluence-name> --space <space-short> -u ${CONFLUENCE_USERNAME} -k ${CONFLUENCE_PASSWORD}
```
