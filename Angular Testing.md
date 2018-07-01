# Angular (6) Testing

A few useful links

[Angular Doc - Test](https://angular.io/guide/testing)

[Angular 6 Testing Service - with a Helper Service issue](https://stackoverflow.com/questions/50503822/angular-6-testing-service-with-reference-to-helper-that-uses-httpclient)

[Angular 6.0 and Karma Jasmine - browser closes after test finish](https://stackoverflow.com/questions/50265743/angular-6-0-and-karma-jasmine-browser-closes-after-test-finish) 

Angular test works right out of the box.  (June 27, 2018) I downloaded the sample 'spec.testing',  
run    
$ng test  

It produced 198 tests, with Bash staying in watch mode, and Karma-Test-Runner output in the "Jasmine HTML Reporter" a browser using port 9876 showing the 198 tests.  My heart felt appreciation to the people made this great user and learner experience.  Thank you!  

Now the Learning Testing journey begin...

#First I create a simple Test app: test-simple-app  
The file 'karma.config.js' and 'test.js'

```
    basePath:...
    frameworks: ...
    plugins:...
    client:...
    coverageInstanbulReporter: ...
    angularCli: ...
    reporters:...


    port: 9876,
    colors: true,
    logLevel: config.LOG_INFO,
    antuWatch: true,
    browsers: ['Chrome'],
    singleRun: false
```
When I first ran 'ng test', there is an error.  Because our new app's name is 'test-simple-app'; I have to change the corresponding fields and info to reflect this.  
**Notice**: we test if the component is created, its title, and the \<h1> is where to place the title.

# Learn Component Test Basics
To test a component, we can use one of these approaches:

>Test it as used by DashboardComponent.  
>Test it as a stand-alone component.  
>Test it as used by a substitute for DashboardComponent.

Find the immediate goal first.  It could be a child inside of the component.  For example, the immediate goal is to test the DashboardHeroComponent, not the DashboardComponent, so, we can try to 'Test it as a stand-alone component' or 'Test it as used by a subtitute for DashboardComponent'.

# Learn and Apply Component Test Scenarios

 - Binding

 - External Files

 - Async Service

 - Input and Output

 - In a test host

 - Routing

 - Routed

 # Test Other major Elements

  - Directive

  - Pipe


# Test Debugging

# Testing Utility APIs



