### Publish Package

1. Put a `v.mod` file inside the toplevel folder of your module (if you
	created your module with the command `v new mymodule` or `v init` you already have a v.mod file). 

	```sh
	v new mymodule
	Input your project description: My nice module.
	Input your project version: (0.0.0) 0.0.1
	Input your project license: (MIT) 
	Initialising ...
	Complete!
	```

	Example `v.mod`:
	```v ignore
	Module {
		name: 'mymodule'
		description: 'My nice module.'
		version: '0.0.1'
		license: 'MIT'
		dependencies: []
	}
	```

	Minimal file structure:
	```
	v.mod
	mymodule.v
	```

	Check that your module name is used in `mymodule.v`:
	```v
	module mymodule

	pub fn hello_world() {
		println('Hello World!')
	}
	```

2. Create a git repository in the folder with the `v.mod` file 
	(this is not required if you used `v new` or `v init`):
	```sh
	git init
	git add .
	git commit -m "INIT"
	````

3. Create a public repository on github.com.
4. Connect your local repository to the remote repository and push the changes.
5. Add your module to the public V module registry VPM:
	https://vpm.vlang.io/new

	You will have to login with your Github account to register the module.
	**Warning:** _Currently it is not possibility to edit your entry after submiting.
	Check your module name and github url twice as this cannot be changed by you later._
6. The final module name is a combination of your github account and 
	the module name you provided e.g. `mygithubname.mymodule`.

**Optional:** tag your V module with `vlang` and `vlang-module` on github.com 
to allow a better search experiance.