# DynamicTemplateJsonExample
This is an example on how to setup template.json (and the folder structure) create a project template. 

### Highlights
- Adjusts namespace accordingly (and any other occurence of "ExampleTemplate")
- Generates a fresh GUID and replaces "$guid".

### Json Content
```json
{
    "$schema": "http://json.schemastore.org/template",
    "classifications": [ "Console", "Example", "Template" ],
    "identity": "ExampleTemplate",
    "name": "Example template project with dynamic GUID and Renaming.",
    "shortName": "exampletemplate",
    "sourceName":"ExampleTemplate",
    "tags": {
      "language": "C#",
      "type": "project"
    },
    "symbols": {
        "guidGeneration": {
            "type": "generated",
            "generator": "guid",
            "replaces": "$guid",
            "parameters": {
                "format": "NDnd",
                "defaultFormat": "D"
            }
        }
    }
}
```

### Comments
- The naming happens due to "sourceName" property. Whatever is named "ExampleTemplate" is replaced with the current project name.
- The property "shortName" can be used to target and create a project from a template later on.
- The symbols part is a definition where you can customize special events like creating a new guid (there's a good documentation regarding this but I'm too lazy to find the link now)

### How to install the template

Starting from ExampleTemplate (or your own template project) as a working directory, you type in the following command: 

```cmd
dotnet new install .\
```
This will install our (or your own) template.

### Create a sample project using your newly installed template

In your project repository directory, create a new project using your installed template. You can use the shortName to target and select your previously installed template. In this case we're using "exampletemplate" to create "GreatestProject".

```cmd
dotnet new exampletemplate -o GreatestProject -n GreatestProject
```
It should tell you that the creation was successful.

### Run it!

Move to your newly created project 'GreatestProject' and run it using the ```dotnet run``` command:

```cmd
PS C:\Users\Developer\source\repos> cd .\GreatestProject\
PS C:\Users\Developer\source\repos\GreatestProject> dotnet run
Running from GreatestProject with GUID 71E2990C-4691-4CBE-8C0E-92F3A8D99520
```
Voilá! Modernized custom project templates with some extra.
