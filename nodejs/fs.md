# Node File System (fs) Module

- provides interface to interact with server machine's filesystem

## Test Access to File or Folder

- usually implemented to see if account used for server has access to a file or directory

```js
const fs = require('fs');
fs.access('./directory-name', (error) => {
  if ( error ) {
    console.log(`Do not have permission`);
  } else {
    console.log(`Permission granted`);
  }
})
```

## File or Folder Exists?

```js
const fs = require('fs');
try {
  if ( fs.existsSync('./directory-name')) {
    console.log(`Directory exists`);
  } else {
    console.log(`Directory does not exist`);
  }
} catch (err) {
  console.error(`An error occurred`);
}
```

## Create a New Directory

```js
const fs = require('fs');
fs.mkdir('./new-directory-name', (err) => {
  if ( err ) {
    console.log(`An error occurred: ${err}`);
  } else {
    console.log(`New directory was created`);
  }
})
```

## Read All Files in Directory

```js
const fs = require('fs');
try {
  const files = fs.readdirSync('./directory-name');
  console.log(files);
} catch ( err ) {
  console.error(`There was an error`);
}
```

## Get Files in Directory and Files in Subdirectory

- uses recursion for subdirectories

```js
const fs = require('fs');
const path = require('path');

const getAllFiles = (path, allFiles) => {
  let files = fs.readdirSync(path);
  allFiles = allFiles || [];
  
  files.forEach( (file) => {
    if ( fs.statSync(`${path}/${file}`).isDirectory() ) {
      allFiles = getAllFiles(`${path}/${file}`, allFiles)
    } else {
      allFiles.push( path.join(__dirname, path, '/', file) )
    }
  });
  return allFiles;
}
```

## Get Filesize of All Files in Directory

- using `getAllFiles` method from before, to get an array of all files
- that array will then be used to loop through and obtain size information

```js
const fs = require('fs');
const getTotalSize = (path) => {
  const allFiles = getAllFiles(path);
  let totalSize = 0;
  allFiles.forEach( (file) => {
    totalSize += fs.statSync(file).size;
  });
  return totalSize;
}

// provide a human-readable version of byte sizes
const convertBytes = (bytes) => {
  const sizes = ["Bytes","KB","MB","GB","TB"];
  if ( bytes == 0 ) {
    return "0 Bytes";
  }
  const i = parseInt(Math.floor(Math.log(bytes) / Math.log(1024)));
  if ( i == 0 ) {
    return `${bytes} ${sizes[i]}`;
  }
  return `${(bytes / Math.pow(1024, i)).toFixed(1)} ${sizes[i]}
}
```

## Rename a Directory

```js
const fs = require('fs');

const prevPath = './directory-name';
const newPath = './new-directory-name';

fs.rename(prevPath, newPath, (err) => {
  if ( err ) {
    console.error(`There was a problem`);
  } else {
    console.log(`The directory was renamed`);
  }
})
```

```js
const fs = require('fs');

const prevPath = './directory-name';
const newPath = './new-directory-name';

try {
  fs.renameSync(prevPath, newPath);
  console.log(`The directory was renamed`);
} catch ( err ) {
  console.error(`There was a problem`);
}
```

## Delete an Empty Directory

```js
const fs = require('fs');

fs.rmdir('./directory-name', (err) => {
  if ( err ) {
    console.error(`There was a problem`);
  } else {
    console.log(`The directory was removed`)
  }
});

// synchronous version:
try {
  fs.rmdirSync('./directory-name');
  console.log(`The directory was removed`);
} catch ( err ) {
  console.error(`There was a problem`);
}
```

## Delete a Directory With All it's Files

```js
const fs = require('fs');
const path = require('path');

const removeDir = (path) => {
  if ( fs.existsSync(path) ) {
    const files = fs.readdirSync(path);
    if ( files.length > 0 ) {
      files.forEach( (file) => {
        if ( fs.statSync(`${path}/${file}`).isDirectory() ) {
          removeDir(`${path}/${file}`);
        } else {
          fs.unlinkSync(`${path}/${file}`)
        }
      });
      fs.rmdirSync(path);
    } else {
      rs.rmdirSync(path);
    }
  } else {
    console.log(`Directory not found`)
  }
}

removeDir( path.join(__dirname, "directory-name") )
```

[source1](https://coderrocketfuel.com/article/7-methods-for-working-with-directories-in-node-js)

