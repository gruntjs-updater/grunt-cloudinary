# grunt-cloudinary

> Uploads specified static files to cloudinary

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-cloudinary --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-cloudinary');
```

## The 'cloudinary' task

### Overview
In your project's Gruntfile, add a section named `cloudinary` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  cloudinary: {
      // Options for cloudinary
      options: {},
      // source files to be processed
      files: [{}]
    }
});
```

### Options

#### options.remove
Type: `Boolean`
Default value: `false`

A Boolean value that is used remove the src files after upload (to be done in next release...).

#### options.replace
Type: `Boolean`
Default value: `false`

A Boolean value that is used to replace all occurrences

#### options.dir
Type: `String`
Default value: `empty string`

A String value that is used to indicate the path where all occurrences in project should be replaced (removal to be done in next release...)

### Usage Examples

#### Simplified Options
In this example, the simplified options are used to upload files to cloudinary

```js
grunt.initConfig({
  cloudinary: {
    options: {
      credentials: { // cloudinary credentials
        'api_key': 'yourapikey',
        'api_secret': 'yourapisecret',
        'cloud_name': 'yourcloudnamehere'
      }
    },
    files: [{
      expand: true, // should be set to true to find whole path
      cwd: '<%= project.dist %>',
      src: [
        'images/**/*.ico', 'images/**/*.png', 'images/**/*.jpeg',
        'scripts/**/*.js', 'scripts/**/*.js'
      ]
    }]
  }
});
```

#### Custom Options
See full example with upload and replace options enabled

```js
grunt.initConfig({
  cloudinary: {
    // Options for cloudinary
    options: {
      replace: true, // replaces originals with uploaded ones // default false
      // in case replace is false find and replace all occurrences is not enabled
      dir: '<%= project.dist %>/', // path where the occurrences should be replaced // defaults to ""
      credentials: { // cloudinary credentials
        'api_key': 'yourapikey',
        'api_secret': 'yourapisecret',
        'cloud_name': 'yourcloudnamehere'
      }
    },
    // source files to be processed
    files: [{
      expand: true, // should be set to true to find whole path
      cwd: '<%= project.dist %>',
      src: [
        'images/**/*.ico', 'images/**/*.png', 'images/**/*.jpeg'
      ]
    }, {
      expand: true, // should be set to true to find whole path
      cwd: '<%= project.dist %>', // use your project destination
      src: [
        'styles/**/*.css'
      ]
    }, {
      expand: true, // should be set to true to find whole path
      cwd: '<%= project.dist %>', // use your project destination
      src: [
        'scripts/**/*.js'
      ]
    }]
  }
});
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_Version: 0.3.2_
