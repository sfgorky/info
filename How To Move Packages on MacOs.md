#How to move packages on MacOS

Ref: [StackOverflow](http://stackoverflow.com/questions/17703510/dyld-library-not-loaded-reason-image-not-loaded)

**Issue**: 
A package was build in a particular location and I decided later to move it to another location.


When trying to run the binaries from this library in the 'moved' location, I've get errors like the error:

	dyld: Library not loaded: <libName>.dylib
  		Referenced from: myBinaryName
  		Reason: image not found
	Trace/BPT trap:5


What was happening is that the library path has 'hard-coded' inside the executable. To change it, you can use the 'install_name_tool' binnary, as indicated:

	install_name_tool -change <fromLibDir>/libname.dylib <toList>/libname.dylib exefile


**Note:**

* To check the dependency libraries you can use:

		otool -L
	
* Add to .bashrc 
	
		alias ldd='otool -L' 
	

	
	
	
 

