# monorepo_typescript


create packages folder ,where have multiple module or package

structure of this is ,
.
├── node_modules
├── package-lock.json
├── package.json
├── packages
│   ├── package1
│   ├── package2
│
├── tsconfig.build.json
└── tsconfig.json

then you will get this node modules
.node_modules/
├── ...
├── package1 -> ../packages/package1
├── package2 -> ../packages/package2


# Steps

Step 1

create one package.json
which will in root file
npm init -y 

create ' package.json' on root directory

example json code 

``` bash {
    "name": "project59",
    "private": true,
  
    "workspaces": [
        "packages/*"
    ],
    "devDependencies": {
        "@tsconfig/recommended": "^1.0.2",
        "@types/node": "^20.6.0",
        "ts-node": "^10.9.1",
        "typescript": "^5.2.2"
    },
    "dependencies": {
        "tsc-watch": "^6.0.4"
    }
}
```
# step 2

create 'tsconfig.json' on root directory

example ts config

``` bash
{
    "extends": "@tsconfig/recommended",
    "compilerOptions": {
      "incremental": true,
      "target": "es2019",
      "module": "commonjs",
      "declaration": true,
      "sourceMap": true,
      "composite": true,
      "strict": true,
      "moduleResolution": "node",
      "esModuleInterop": true,
      "skipLibCheck": true,
      "forceConsistentCasingInFileNames": true
    }
  }

```


   

# step 3
 create 'tsconfig.build.json'

 here is example of this 
 ```bash
 {
    "files": [],
    "references": [
      {
        "path": "packages/package1"
      },
      {
        "path": "packages/package2"
      }
    ]
  }

 ```

 # step4
 And while we are here, let’s also add a build script to the root package.json:
 
 ``` bash
"scripts": {
        "build": "tsc --build --verbose tsconfig.build.json"
    }
```

# then package will be

``` bash
{
    "name": "project59",
    "private": true,
    "scripts": {
        "build": "tsc --build --verbose tsconfig.build.json"
    },
    "workspaces": [
        "packages/*"
    ],
    "devDependencies": {
        "@tsconfig/recommended": "^1.0.2",
        "@types/node": "^20.6.0",
        "ts-node": "^10.9.1",
        "typescript": "^5.2.2"
    },
    "dependencies": {
        "tsc-watch": "^6.0.4"
    }
}

```

# Creating a package

we need to create individual package 

``` bash
npm init --workspace packages/packages1 -y

```
as like this initialize next packages

then package.json will create into packages1 directory

# alternative good approach for this for @projectname

Scoping helps you avoid any confusion with existing packages.
In order to use scoping, when calling
 npm init provide a flag --scope @projectname.
This way, all your packages will be prefixed with @projectname, and won’t cause any confusion.
```bash
 npm init  --scope @project-59
````









