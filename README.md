# The Think About! Website [![Build Status](https://gitlab.com/holderbaum-io/think-about-website/badges/master/pipeline.svg)](https://gitlab.com/holderbaum-io/think-about-website/pipelines)

This is the code for the main Think About! Website, fully responsive.

It contains semantical HTML5 and a mostly class-less minimal CSS styling.

## Development

To see changes locally, simply run:

```sh
./do serve
```

You can also start the server in "preview" mode like this:

```sh
FEATURE_PREVIEW=1 ./do serve
```


This starts a webserver, which you can visit here: http://localhost:9090/en/ .

## Deployment

Deployment is done automatically via Travis CI on every push. Nothing to do here.
