# Angular and Webpack

It seems under the hood, Angular CLI 6 uses Webpack 4+ to bundle Angular 6 application.  Even though we don't have to directly write Webpack configuration file, understand Webpack give us a much clearer picture of how things put together in Angular.

I found a link with great information [**Webpack**](https://angular.io/guide/webpack) but could not get to it directly from https://angular.io/docs.  Maybe there is so technical issue. It also could be since starting from Webpack 4, webpack does not require a configuration file to bundle the project.

We know as of today (May 30th, 2018), we could not eject Webpack from Angular CLI yet.
I found this link regarding [Update to Angular 6 via Webpack manually](https://blog.angularindepth.com/upgrading-a-project-without-cli-to-angular-6-b07b105adc02).  I learn a lot.


**So What is Webpack?**  
Webpack is a module bundler for  JavaScript applications.  Webpack builds and uses a dependency graph to map every module for our application and generate one or more bundles for the project.  This way, we don't have to worry about the sequence of JavaScript codes in our application; also the bundle makes the application's size smaller, and it would run faster.

4 core concepts of webpack are:
> Entry

> Output

> Loaders

> Plugins

For example:

```
entry: {
  'app': './src/main.ts'
},
```
```
entry: {
  app: 'src/app.ts',
  vendor: 'src/vendor.ts'
},

output: {
  filename: '[name].js'
}
```
Configure and use loaders for TypeScript and CSS files:
```
rules: [
  {
    test: /\.ts$/,
    loader: 'awesome-typescript-loader'
  },
  {
    test: /\.css$/,
    loaders: 'style-loader!css-loader'
  }
]
```
Add plugins to create instance of plugins:
```
plugins: [
    new webpack.NoEmitOnErrorsPlugin(),
    new webpack.optimize.UglifyJsPlugin({ // https://github.com/angular/angular/issues/10618
        mangle: {
            keep_fnames: true
        }
    }),
    new ExtractTextPlugin('[name].[hash].css'),
    new webpack.DefinePlugin({
        'process.env': {
            'ENV': JSON.stringify(ENV)
        }
    }),
    new webpack.LoaderOptionsPlugin({
        htmlLoader: {
            minimize: false // workaround for ng2
        }
    })
]
``` 


