# Under the Hood - TypeScript 

There is a simple introduction to [TypeScript Configuration](https://angular.io/guide/typescript-configuration
) in Angular Guide under Setup & Deployment.  The typical settings are inside of tsconfig.json: 
```
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "lib": [ "es2015", "dom" ],
    "noImplicitAny": true,
    "suppressImplicitAnyIndexErrors": true
  }
}
```

Currently (as of June 1st, 2018), many browsers are still support "es5", that is why even when we see our codes syntac looks familiar to "es6" or later, we still set the target to "es5" so Angular can transpile our application to "es5".

It is a good idea to keep "module" using "commonjs", because Typescript behave differently if we put it to default to a different library.  

"moduleResolution" is set to "node"  tells Typescript to search the ambien declaration under the "node_modules" sub folder "@type".

"sourceMap" set to true tells the transpiler to produce ...js.map files for application debug and tracing.  There are various options of sourceMap setting.

>"emitDecoratorMetadata": true

This will emit our decorator's metadata such as @Component... to the export class

```
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
```

>"experimentalDecorators": true

This allow us to use experimental types such as "es2017" and onward.

>"lib": [ "es2015", "dom" ]

Since we Target to "es5", we want the Typescript compiler to be able to reconize "es2015" type and "dom" browser type in our codes.

>"noImplicitAny": true

This setting help us write better Typescript code and become more concient about missing typing so that we can correct it quickly.


>"suppressImplicitAnyIndexErrors": true

This setting help us to avoid seeing too many anoying index errors which are not really important to us.

We have learn some important settin from the TypeScript Deep Dive book. Such as:

 - "noLib": If set, it will disable the default 'lib.d.ts'.  **Advice**: don't use it unless you are very advance in Typescript and have a need to only use your custom library.
 - "preserveConstEnums": set it if we use const for enums variable; but still want the js code for the enums.

>With Angular-Cli

If we are using Angular-Cli, we need to understand that the tsconfig.json file works together with what we/angular have defined in the 'angular.json' file.

use for verious environment.

> ng serve --configuration=environment_name


environment_name - (dev,qa,prod) same process can be followed for ng build

angular.json
```
"configurations": {
        "production": {
          "fileReplacements": [
            {
              "replace": "src/environments/environment.ts",
              "with": "src/environments/environment.prod.ts"
            }
          ],
          "optimization": true,
          "outputHashing": "all",
          "sourceMap": false,
          "extractCss": true,
          "namedChunks": false,
          "aot": true,
          "extractLicenses": true,
          "vendorChunk": false,
          "buildOptimizer": true
        },
        "dev": {
          "fileReplacements": [
            {
              "replace": "src/environments/environment.ts",
              "with": "src/environments/environment.dev.ts"
            }
          ],
          "optimization": true,
          "outputHashing": "all",
          "sourceMap": true,
          "extractCss": true,
          "namedChunks": false,
          "aot": true,
          "extractLicenses": true,
          "vendorChunk": false,
          "buildOptimizer": true
        },
        "qa": {
          "fileReplacements": [
            {
              "replace": "src/environments/environment.ts",
              "with": "src/environments/environment.qa.ts"
            }
          ],
          "optimization": true,
          "outputHashing": "all",
          "sourceMap": false,
          "extractCss": true,
          "namedChunks": false,
          "aot": true,
          "extractLicenses": true,
          "vendorChunk": false,
          "buildOptimizer": true
        }
      }
```      