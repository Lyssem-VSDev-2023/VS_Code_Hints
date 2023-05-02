# **Misc VSCode Hints**

<br>
<br>

# Table of Content

1. [Create a Code Snippet](#1-create-a-code-snippet)
1. [Add to Source Code Control (Github)](#2-add-to-source-code-control-github)

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

<!---------------------Add to Source Code Control (Github ----------------------------->

# 2. Add to Source Code Control (Github)

* Open Source Control

![Snippet Menu](/Images/SourceCode_1.png)
* Select **Publish to GitHub** Button
* Confim the proposed Name (Git Hub need to be logged in)
* Confirm teh selected Folders to be synched