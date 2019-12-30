# defra-hapi-photos
Hapi plugin to upload (type of original and resize to other specified types) and download (types of original and other specified types)


[![Build Status](https://travis-ci.com/DEFRA/defra-hapi-photos.svg?branch=master)](https://travis-ci.com/DEFRA/defra-hapi-photos)
[![Known Vulnerabilities](https://snyk.io/test/github/defra/defra-hapi-photos/badge.svg)](https://snyk.io/test/github/defra/defra-hapi-photos)
[![Code Climate](https://codeclimate.com/github/DEFRA/defra-hapi-photos/badges/gpa.svg)](https://codeclimate.com/github/DEFRA/defra-hapi-photos)
[![Test Coverage](https://codeclimate.com/github/DEFRA/defra-hapi-photos/badges/coverage.svg)](https://codeclimate.com/github/DEFRA/defra-hapi-photos/coverage)

## Installation

Via github:
```
npm install --save https://github.com/DEFRA/defra-hapi-photos.git#master
```

It is recommended that tie to a specific commit/version as follows:
```
npm install --save https://github.com/DEFRA/defra-hapi-photos.git#commit_or_version
```
## Usage
Please note:
 - this example is written using the standard linter (no semicolons)
 - example usage can be found within the unit tests 
```
// Registering the plugin:

const Hapi = require('hapi')
const server = hapi.server()

await server.register([{
 plugin: require('defra-hapi-photos'),
 options: {
   path: '/photos', // original images found at path '/photos/original/example.jpg'
   alternativeSizes: [
     {type: 'small', width: '100', height: '100'},   // small images found at path '/photos/small/example.jpg
     {type: 'medium', width: '200', height: '200'},  // medium images found at path '/photos/medium/example.jpg
   ],
   region: // s3Region,
   apiVersion: // s3ApiVersion,
   bucket: // s3Bucket,
   maxMb: // max upload size of image in Mb,
   minKb: // min upload size of image in Kb,
   payloadMaxBytes: // max upload size for payload in bytes (for multiple uploads),
   options: { // any standard hapi route options }
 }
}])

```
See unit tests for uploading a file in  <https://github.com/DEFRA/defra-hapi-photos/blob/master/lib/photos.test.js> and also the example in <https://github.com/DEFRA/ivory-front-office/blob/master/server/modules/photos/add-photograph.handlers.js>

## Contributing to this project

Please read the [contribution guidelines](/CONTRIBUTING.md) before submitting a pull request.

## License

THIS INFORMATION IS LICENSED UNDER THE CONDITIONS OF THE OPEN GOVERNMENT LICENCE found at:

<http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3>

The following attribution statement MUST be cited in your products and applications when using this information.

>Contains public sector information licensed under the Open Government license v3

### About the license

The Open Government Licence (OGL) was developed by the Controller of Her Majesty's Stationery Office (HMSO) to enable information providers in the public sector to license the use and re-use of their information under a common open licence.

It is designed to encourage use and re-use of information freely and flexibly, with only a few conditions.

