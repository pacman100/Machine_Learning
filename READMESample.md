# SharePoint Seach Connector

> [![N|Solid](https://img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/RE1Mu3b?ver=5c31)](https://www.microsoft.com/)

## Introduction
>SharePoint search connector tool is designed to help customers onboard common data sources like SQL, Oracle, Rest Apis into Search index and then leverage the search service to retrieve data and present it to users. Rightnow in SharePoint, we have a provision in SharePoint to crawl databases, but it requires IT admin to setup a BDC model with details like database connection string, query etc, This is a complex XML file and it requires good SharePoint knowledge to interpret and debug issues if any with the model. Once model is created, create a new content source using the BDC model to crawl database. Then search service will read items in sequential and puts them into index, which can take lot of time. 

>The advantage of the search connector tool is it can connect to the datasource, read items in batches in parallel and then generates metdata information for all rows as individual html files, which can then be stored in a file share. A new content source needs to be created to crawl these metadata files. The tool also creates various partitions to store items in a logical fashion, which can be used to identity a particular file and retrieve it in an efficient way. It would also be easy to debug issues with any particular data row. You just have to navigate to the particular html file, add/update the metadata in the html file and search service will automatically index them in the next incremental crawl. The search connector tool is a simple console application which can be scheduled either as a task scheduler. Also the tool has capability to write metadata files either to Windows file share or to Azure file share.

>With the following advantages, we are envisioning this tool as an alternative to the complex BDC model we have in SharePoint to crawl datasources and users can using it with minimum configuration changes to crawl their data and get advantage of investment they have done in O365/SharePoint platform.


## Requirements
This tool is .Net Core Console Application with Target Framework being `.Net Core 2.1`. This application consists of four projects:
* Microsoft.SearchConnector.NetCore
* Microsoft.SearchConnector.DataAccess
* Microsoft.SearchConnector.Common
* Microsoft.SearchConnector.Utilities

##### Following nuget packages are required:
1) Autofac.Extensions.DependencyInjection
2) Microsoft.AspNetCore.ApplicationInsights.HostingStartup
3) Newtonsoft.Json
4) Oracle.ManagedDataAccess.Core
5) System.Configuration.ConfigurationManager
6) System.Data.DataSetExtensions
7) System.Data.SqlClient
8) WindowsAzure.Storage


## Usage Instructions
This tool is simple to use and extensible. User needs to just change the configurations in `App.Config` and `RestAPIConfig.json` files. This document details the required configuration changes for SQl Server, Oracle DB and Kaltura Rest API for different scenarios.

##### App.Config File:
Following table provides brief description of `App.Config` file settings and expected values.

| Setting | Description | Expected Vlaues |
| ------ | ------ | ------ |
| DatabaseType | The type of external content source  | (sql, oracle, kalturarestapi) |
| LoggingType | Specifies the location for logging the data: File System or Azure Application Insights  | (file, applicationinsights) |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |
| ------ | ------ | ------ |

### SQL Server

#### Partitioning Based
#### Default Count Based
#### Complete Mode
#### Incremental Mode


### Oracle DB
#### Partitioning Based
#### Default Count Based
#### Complete Mode
#### Incremental Mode


### Kaltura Rest API
#### Default Count Based
#### Complete Mode
#### Incremental Mode

### Azure File Share

### Azure App Insights


## License

Dillinger is a cloud-enabled, mobile-ready, offline-storage, AngularJS powered HTML5 Markdown editor.

  - Type some Markdown on the left
  - See HTML in the right
  - Magic

# New Features!

  - Import a HTML file and watch it magically convert to Markdown
  - Drag and drop images (requires your Dropbox account be linked)


You can also:
  - Import and save files from GitHub, Dropbox, Google Drive and One Drive
  - Drag and drop markdown and HTML files into Dillinger
  - Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions that people naturally use in email.  As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Tech

Dillinger uses a number of open source projects to work properly:

* [AngularJS] - HTML enhanced for web apps!
* [Ace Editor] - awesome web-based text editor
* [markdown-it] - Markdown parser done right. Fast and easy to extend.
* [Twitter Bootstrap] - great UI boilerplate for modern web apps
* [node.js] - evented I/O for the backend
* [Express] - fast node.js network app framework [@tjholowaychuk]
* [Gulp] - the streaming build system
* [Breakdance](http://breakdance.io) - HTML to Markdown converter
* [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

### Installation

Dillinger requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

### Plugins

Dillinger is currently extended with the following plugins. Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| Github | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |


### Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantanously see your updates!

Open your favorite Terminal and run these commands.

First Tab:
```sh
$ node app
```

Second Tab:
```sh
$ gulp watch
```

(optional) Third:
```sh
$ karma test
```
#### Building for source
For production release:
```sh
$ gulp build --prod
```
Generating pre-built zip archives for distribution:
```sh
$ gulp build dist --prod
```
### Docker
Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the Dockerfile if necessary. When ready, simply use the Dockerfile to build the image.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version} .
```
This will create the dillinger image and pull in the necessary dependencies. Be sure to swap out `${package.json.version}` with the actual version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on your host. In this example, we simply map port 8000 of the host to port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Verify the deployment by navigating to your server address in your preferred browser.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

See [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)


### Todos

 - Write MORE Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
