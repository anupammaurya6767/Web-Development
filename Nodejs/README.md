# 1. Installing Node.js

1. Download Node.js at https://nodejs.org/

2. Check the version of node you have installed: ```$ node -v```


# 2. Using Node.js modules

They are installed by default when Node.js is installed.

To use the modules, first you have to enable them. Write on the first lines of your code:

```const alias = require('moduleName')```

For example, for the [File System](https://nodejs.org/docs/latest-v14.x/api/fs.html) module you should write:

```const fs = require('fs');```

_See the documentation at https://nodejs.org/api/_


# 3. Installing Node Package Manager:

1. Install npm

```$ sudo npm install -g npm```
 
2. Check the version of npm you have installed:

```$ npm -v```


# 4. Create a package.json file on your project folder

#### **1.** Make sure you are located in the path of your project folder: 

```$ cd /folder_path```

#### **2.** 
#### - If you want to create this file with custom values: 

```$ npm init```

The CLI utility will walk you through creating the ```package.json``` file. It only covers the most common items, and tries to guess sensible defaults.
Then the ```package.json``` file will be created ‘automatically’ in your folder with the values you provided. You can change them later by editing the file.

#### - If you want to create this file with default values: 

```$ npm init -y```

The ```package.json``` file will be created ‘automatically’ in your folder with those default values. You can change them later by editing the file.

---

#### Note: 
In the ```package.json``` file under the key ```"dependencies"```, you will see all the dependencies (libraries) that you install in that project.

---

# 5. Installing a package (pkg)

To install a package, you should check its official documentation but generically they can be installed as follows:

```$ npm i pkg-name``` _or_ ```$ npm install pkg-name``` (the latest version of the pkg is installed)

**_or_**

```$ npm install pkg-name@version``` (the chosen version of the pkg is installed)


_* Replace ```pkg-name``` with the name of the package and ```version``` by the version number you want to install (ex: 1.0.0)._

---

#### Note: 
- The first time a pkg is installed, the following files are created 'automatically': 
  - a ```package-lock.json``` file
  - a folder called ```node_modules``` that will contain the packages that you install, each in its own folder (do not manipulate the packages from here, as they are volatile, always do the updates, deletions and any other modifications of the pkgs from the CLI) and also will contain a ```.package-lock.json``` file

- Every time a pkg is installed, the dependency will be added to the ```package.json file``` and the ```package-lock.json``` file.

- The ```package-lock.json``` and ```.package-lock.json``` files, include all the details about every dependency you have installed in your project. The ```package.json file``` only contains the names and versions of the ones you install from the CLI.

---

# 5a. Installing a package for development use only

```$ npm i pkg-name --save-dev``` _or_ ```$ npm install pkg-name --save-dev```

_* Replace ```pkg-name``` with the name of the package._

---

#### Note:
In the ```package.json``` file you will see all the dependencies (libraries) that you installed in that project for development only, under the key ```"devDependencies"```.

---

# 5b. Installing all packages from an existing package.json file

If you delete or you don't have the ```node_modules``` folder but you **do** have a ```package.json``` file with dependencies, you can install all the packages that are declared in that ```package.json``` file as follows:

```$ npm i``` _or_ ```$ npm install```

---

#### Note: 

The version that is installed is the one declared in the ```package.json``` file)

---

# 5c. Uninstalling packages

To uninstall a package, check its official documentation but generically uninstall as follows:

```$ npm uninstall pkg-name``` _or_ ```$ npm remove pkg-name``` _or_ ```$ npm r pkg-name```

_* Replace ```pkg-name``` with the name of the package._

---

#### Note: 
Every time a pkg is uninstalled, the dependency on the ```package.json``` file and the ```package-lock.json``` file will be removed.

---

# 5d. List the packages that are installed

```$ npm ls```
