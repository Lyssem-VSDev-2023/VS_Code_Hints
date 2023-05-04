# **Misc VSCode Hints**

<br>
<br>

# Table of Content

1. [Create a Code Snippet](#1-create-a-code-snippet)
1. [Add to Source Code Control (Github)](#2-add-to-source-code-control-github)
1. [Install MarkDown Compiler](#3-install-markdown-compiler)
1. [Automatic Markdown compilation](#4-automatic-markdown-compilation)
1. [Install TypeScript](#5-install-typescript)


<br>
<br>

<!---------------------Create a Code Snippet----------------------------->

# 1. Create a Code Snippet

Go to the following menu:
- File
- Preferences
- Configure Uer Snippets
- Select the language (or a global snippet)
- Type you code under the "language".json

```json
    "Print String to console": {
		"prefix": "log_String",
		"body": [
			"let $1 = \"$2\";",
			"console.log($1);",
		],
		"description": "Log Declaration output to console"
	},
	"Print Number to console": {
		"prefix": "log_Number",
		"body": [
			"let $1 = $2;",
			"console.log($1);",
		],
		"description": "Log Declaration output to console"
	},
```
![Snippet Menu](/Images/Snippet_1.png)

<!-----------------Add to Source Code Control (Github) -------------------------->
<hr>

# 2. Add to Source Code Control (Github)

* Open Source Control

![Source Control Menu](/Images/SourceCode_1.png)
* Select **Publish to GitHub** Button
* Confim the proposed Name (Git Hub need to be logged in)
* Confirm teh selected Folders to be synched

<!-----------------Install MarkDown Compiler -------------------------->
<hr>

# 3. Install MarkDown Compiler

1. Install the markdown-it compiler: ``` npm install -g markdown-it ```

2. Create a tasks.json file: 
    - In VsCode, go to **Terminal** Menu
	- Select **Configure Tasks...**
	- Select **Create tasks.json file from template**
	- Select **Others...**

3. In the created tasks file, update the label and the task action, then save the file:
```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Compile Markdown single file",
            "type": "shell",
            "command": "markdown-it Readme.md -o Readme.html"
        }
    ]
}
```
4. Run the build task
    - In VsCode, go to **Terminal** Menu
	- Select **Run Tasks...**
	- Select the task as per the name you just created
	- Select the Default option *(continue without scanning)* or select any other suitable option.

![MarkDown Menu](/Images/markdwon1.png)

<!---------------------Automatic Markdown compilation----------------------------->

# 4. Automatic Markdown compilation

1. Install gulp globally: ``` npm install -g gulp ```
2. Install gulp locally: ```  npm install gulp gulp-markdown-it ```
3. Create gulp task script: 
    - Create a **gulpfile.js** file under root folder of the project  where the md files have to be processed
	- Part the following **Javascript** code under the created file:
```js
//Script that watches any change on the .md files, in order to recompile them in .html at save
var gulp = require('gulp');
var markdown = require('gulp-markdown-it');
gulp.task('markdown', function () {
    return gulp
        .src('**/*.md')
        .pipe(markdown())
        .pipe(
            gulp.dest(function (f) {
                return f.base;
            })
        );
});
gulp.task('default', function () {
    return gulp.watch('**/*.md', gulp.series(['markdown']));
});
```
4. Create the batch task: 
```json
{
    // See https://go.microsoft.com/fwlink/?Link...
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "type": "gulp",
            "task": "default",
            "problemMatcher": [],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```
5. Run the build task
    - Go to **Terminal** Menu
	- Select **Run Tasks...**
	- Select the task as per the name you just created
6. The task will be lauched and **watching** for any change to the **.md** files, and proceed with their **complation** to **.html** 
7. To stop the task:
	- Go to **Terminal** Menu
	- Select Terminate Task
`

<!---------------------Install TypeScript----------------------------->

# 5. Install TypeScript


