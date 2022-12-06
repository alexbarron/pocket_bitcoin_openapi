# Unofficial Pocket Bitcoin OpenAPI Generator

This repository contains an OpenAPI yaml file to automatically generate API wrappers and reference docs for the Pocket Bitcoin API. This file was not created by Pocket Bitcoin, nor is it supported by them. Use this as you wish, but be mindful it is unsupported and not necessarily production grade.

* [Contact Pocket Bitcoin](https://pocketbitcoin.com/contact) to get API credentials.
* [Official Pocket Bitcoin API Docs](https://pocketbitcoin.com/developers)
* Don't know about OpenAPI? See here: https://openapi-generator.tech/

## Instructions

### Initial Setup

First, clone the repo to your local.

```shell
git clone https://github.com/alexbarron/pocket_bitcoin_openapi.git
```

Next, install OpenAPI following instructions for the [CLI Installation](https://openapi-generator.tech/docs/installation).

### Generating Libraries & Docs

#### API Client Libraries

OpenAPI supports over 60 languages and frameworks.

You can generate a client library using the command below, replacing `LANGUAGE` with the language you're using. See [OpenAPI Client Generators](https://openapi-generator.tech/docs/generators/#client-generators) for the full list of possible values.

```shell
openapi-generator-cli generate -i pocket_bitcoin_openapi.yaml -g LANGUAGE -o ~/path/where/to/put/pocket_bitcoin
```

For example, the command for Python:

```shell
openapi-generator-cli generate -i pocket_bitcoin_openapi.yaml -g python -o ~/path/where/to/put/pocket_bitcoin
```

The generated client library will automatically include a README file with usage instructions.

You must prefix the Authorization header value with `client_id` before your key. This can be set in the API's configuration at initialization in either the `api_key_prefix` or `apiKeyPrefix` field depending on the language you're using. See `Getting Started` in the README of the generated library for how to set the prefix.

#### API Docs

The same yaml file used for creating API libraries can also be used to generate API reference documentation. OpenAPI currently supports 9 different generators for documentation. See [OpenAPI Documentation Generators](https://openapi-generator.tech/docs/generators/#documentation-generators) for possible formats.

For example, to generate markdown docs:

```shell
openapi-generator-cli generate -i pocket_bitcoin_openapi.yaml -g markdown -o ~/path/where/to/put/pocket_bitcoin_md
```

Or to generate HTML docs:

```shell
openapi-generator-cli generate -i pocket_bitcoin_openapi.yaml -g html -o ~/path/where/to/put/pocket_bitcoin_html
```

#### Optional Configs

You can add optional configurations to modify the default output of the generator. For example, you might want to have a particular package name or metadata if you want to publish it publicly.

You can see available configs for any language by running the following command. Once again, replacing LANGUAGE with the language you're using.

```shell
openapi-generator-cli config-help -g LANGUAGE
```

For example, the command for Python:

```shell
openapi-generator-cli config-help -g python
```

You can look up config options by following the links to the language specific docs from [OpenApi's docs](https://openapi-generator.tech/docs/generators/#client-generators).

Create a file called `config.yaml` in the same directory as `pocket_bitcoin_openapi.yaml` and add your configs. Or modify the sample config file provided.

```yaml
# sample_config.yaml

# javascript
projectName: pocket-bitcoin-api-js
projectVersion: 1.0.0

# python
packageName: pocket_bitcoin_python
packageUrl: https://abarron.com
packageVersion: 1.0.0
projectName: pocket-bitcoin-api

# ruby
gemName: pocket_bitcoin_ruby
gemAuthor: Alex Barron
gemHomepage: https://abarron.com
gemVersion: 1.0.0
```

To include a config file, add `-c config.yaml` to your generate command.

```shell
openapi-generator-cli generate -i pocket_bitcoin_openapi.yaml -g python -o ~/path/where/to/put/pocket_bitcoin_python -c config.yaml
```
