### Manage Packages

Briefly:

```powershell
v [module option] [param]
```

###### module options:

```
   install           Install a module from VPM.
   remove            Remove a module that was installed from VPM.
   search            Search for a module from VPM.
   update            Update an installed module from VPM.
   upgrade           Upgrade all the outdated modules.
   list              List all installed modules.
   outdated          Show installed modules that need updates.
```

Read more:

You can also install modules already created by someone else with [VPM](https://vpm.vlang.io/):
```powershell
v install [module]
```
###### Example:
```powershell
v install ui
```

Removing a module with v:

```powershell
v remove [module]
```
###### Example:
```powershell
v remove ui
```

Updating an installed module from [VPM](https://vpm.vlang.io/):

```powershell
v update [module]
```
###### Example:
```powershell
v update ui
```

Or you can update all your modules:
```powershell
v update
```

To see all the modules you have installed, you can use:

```powershell
v list
```
###### Example
```powershell
> v list
Installed modules:
  markdown
  ui
```

To see all the modules you have installed, you can use:
outdated          Show installed modules that need updates.
```powershell
v outdated
```
###### Example
```powershell
> v outdated
Modules are up to date.
```