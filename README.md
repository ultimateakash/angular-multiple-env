
### <h1 align="center"  id="heading">Create Multiple Environments In Angular</h1>
## environments 
```
 environment.ts
 environment.stage.ts
 environment.prod.ts
```
## angular.json
```json
"architect": {
    "build": { 
            ...
            ...
        },
        "configurations": {
            "production": {
                "budgets": [
                    {
                        "type": "initial",
                        "maximumWarning": "500kb",
                        "maximumError": "1mb"
                    },
                    {
                        "type": "anyComponentStyle",
                        "maximumWarning": "2kb",
                        "maximumError": "4kb"
                    }
                ],
                "fileReplacements": [
                    {
                        "replace": "src/environments/environment.ts",
                        "with": "src/environments/environment.prod.ts"
                    }
                ],
                "outputHashing": "all"
            },
            "staging": {
                "budgets": [
                    {
                        "type": "initial",
                        "maximumWarning": "500kb",
                        "maximumError": "1mb"
                    },
                    {
                        "type": "anyComponentStyle",
                        "maximumWarning": "2kb",
                        "maximumError": "4kb"
                    }
                ],
                "fileReplacements": [
                    {
                        "replace": "src/environments/environment.ts",
                        "with": "src/environments/environment.stage.ts"
                    }
                ],
                "outputHashing": "all"
            },
            "development": {
                "buildOptimizer": false,
                "optimization": false,
                "vendorChunk": true,
                "extractLicenses": false,
                "sourceMap": true,
                "namedChunks": true
            }
        },
        "defaultConfiguration": "production"
    },
    "serve": {
        "builder": "@angular-devkit/build-angular:dev-server",
        "configurations": {
            "production": {
                "browserTarget": "angular-multiple-env:build:production"
            },
            "staging": {
                "browserTarget": "angular-multiple-env:build:staging"
            },
            "development": {
                "browserTarget": "angular-multiple-env:build:development"
            }
        },
        "defaultConfiguration": "development"
    } 
}
```
## development
```bash
ng serve
ng build
```

## staging
```bash
ng serve --c staging
ng build --c staging
```

## production
```bash
ng serve --c production
ng build --c production
``` 
## Note:-
```bash
--c is alias for --configuration 
```
```bash
--prod is deprecated 
```
