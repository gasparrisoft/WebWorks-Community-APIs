ExtractZIPFile 
==============
Provides extraction (unzipping) of zip archives for html5 under Blackbery 10.


## Including the feature in your application

This API can be installed from source or from the [Cordova Plugin Registry](http://plugins.cordova.io/). Installation from the registry is done through the following:

	cordova plugin add com.blackberry.community.extractzipfile

or,
	
	webworks plugin add com.blackberry.community.extractzipfile

Installation from source is the same but instead of the id ("com.blackberry.community.extractzipfile"), use the file system path to the source plugin folder.


API Examples
--------------
### Example of API usage
	function extractFile(fileName) {
		community.extractZipFile.extract(
			{
				zip: 'folder1/' + zipFilename,
				destination: 'folder2/destination',
				overwriteFiles: true,
				tarBombProtection: false,
				callbackToken: '',
			},
			onExtractCompletion);
	}

	function onExtractSuccess(status) {	
		if (status.result < 0) {
			alert("Extraction Failed");
			console.log(status.resultMessage);

		} else {
			alert("Extracted " + status.zip + " to " + status.destination);
			console.log(status.resultMessage);
		}
		console.log("Extraction returned with token: " + callbackToken);
  	}	 
    									
API Details
===============
The API takes an option object and a callback function.
The following options are supported.

### zip
Required: As you can guess an unknown zip cannot be extracted.
The path and file name to the zip file which is to be extracted.

Default: none! This argument is required!


### destination
The folder into which the zip will be extracted.

Default: './', Current working directory.


### overwriteFiles
If already existing files should be overwritten by those within the zip.

Default: true, Files will be overwritten.


### tarBombProtection
If true any zips which do not contain a folder as the root will extracted into a
new folder named after the zip archives name.

Default: false. 


### callbackToken
String which will be passed back without alteration upon callback. If not given
callbackToken will contain a copy of the zip argument. Use this argument for
concurrent zip extraction to differentiate between callbacks.

Default: duplicate of zip argument.

[![Analytics](https://ga-beacon.appspot.com/UA-46817652-1/WebWorks-Community-APIs/BB10-Cordova/ExtractZipFile?pixel)](https://github.com/igrigorik/ga-beacon)