# Spring Test Generator

[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/) [![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg?v=103)](https://opensource.org/licenses/mit-license.php) [![Bash Shell](https://badges.frapsoft.com/bash/v1/bash.png?v=103)](https://github.com/ellerbrock/open-source-badges/) [![written-in-shell-script](https://img.shields.io/badge/</>-Shell%20Script-<COLOR>.svg)](https://shields.io/) [![current-version](https://img.shields.io/badge/version-1.0.4-blue.svg)](https://shields.io/) [![native-support](https://img.shields.io/badge/native--support-Linux%20%7C%20MacOS-lightgrey.svg)](https://shields.io/)

- Writing Test Cases for Spring hasn't being more fun than ever.
- **This was created in order to make writing test cases as easy as writing a controller**
- Simple yet powerful Test Case generator

# --initialData

The test cases generated by the script requires the presence of initial java files that handles most of the heavylifting so if your using this script for the first time on a project then consider running this script using `--initialData` flag

    ./spring-Test-Generator.sh --initialData

# Usage

In Order to use this script without any issues.

At First, we have to install `jq` Json Processor for the your Environment using:

    sudo apt-get install jq

This is for the Debian and Ubuntu Repositories, check out the below link for the rest of the Linux Distributions, MacOS and Windows:

[Download jq](https://stedolan.github.io/jq/download/)

Then you have to create the `tests.json` file in this format:

```javascript
    {
      "package": "com.spring.project", //Package data of the Main file inside Test Directory
      "functions": [
        {
          "fileName": "SimpleController",
          "tests": [
            {
              "functionName": "getDatafromSpringControllerTest",
              "auth": true,
              "authData": "default",
              "type": "GET",
              "endpoint": "/data/2?info=8",
              "result": "HttpStatus.OK",
              "data": ""
            }
          ]
        }
    }
```

For Post/Put/Delete Requests where we have Data:

```javascript
    {
      "fileName": "PostDataController",
      "tests": [
        {
          "functionName": "postData",
          "auth": true,
          "authData": "default",
          "type": "Post",
          "endpoint": "/sendData",
          "result": "HttpStatus.OK",
          "data": {
            "1": 1,
            "2": "2",
            "3": true
          }
        }
      ]
    }
```

If you want to use custom email and password apart from the Application Config file `authData` key is available and make sure that the `auth` key is set to `true` by writing your required `email<;:semi-colon>password` and entering `default` to `authData` key would fetch it from `ApplicationConfig` values.

    "auth": true,
    "authData": "mailId;password"

If there is an Endpoint that requires headers:

```javascript
    {
      "fileName": "headerController",
      "tests": [
        {
          "functionName": "headerData",
          "auth": true,
          "authData": "me@mail.com;1234",
          "type": "Get",
          "headers": true,
          "endpoint": "/head",
          "result": "HttpStatus.OK",
          "data": ""
        }
      ]
    }
```

If in case you have some headers to fill make sure `headers` key is set to `true`

```javascript
    {
          "fileName": "NotificationSettingController",
          "tests": [
            {
              "functionName": "notificationSettingUpdateWithExistingResource",
              "auth": false,
              "type": "POST",
              "headers": true,
              "headersData": [
                {
                  "key": "directory",
                  "value": "MED"
                },
                {
                  "key": "fileName",
                  "value": "Medical-2018.pdf"
                }
              ],
              "endpoint": "/notificationSettingUpdate",
              "result": "HttpStatus.OK",
              "data": {
                "1": 21,
                "2": "40%"
              }
            }
          ]
        }
```

If your project already has the required initial Data, then simply run:

    ./spring-Test-Generator.sh

## Further Developments

- Add JSON data from data key properly to the java file
- Implementing headersData if headers is set to true
- if replace key is set to false present at the fileName key then below functions will start to add above the previous functions
- Creating .bat file for Windows so alternatively you can use git bash to execute bash script in Windows

# Special Thanks

Special Thanks to stackoverflow user: `@vfalcao` without whom the main component of this script wouldn't have being developed!!
