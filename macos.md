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
	
* One can use: @executable_path , @rpath keywords. Check [here](https://wincent.com/wiki/@executable_path,_@load_path_and_@rpath)



	
#Where to define Environment Variables

ref: [here](http://www.dowdandassociates.com/blog/content/howto-set-an-environment-variable-in-mac-os-x-home-slash-dot-macosx-slash-environment-dot-plist)


Use the file:

    ~/.MacOSX/environment.plist 	

here is an example:

    <?xml version="1.0" encoding="UTF-8"?>                                          
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">                                                           
        <dict>                                                                          
            <key>BOOSTDIR</key>                                                         
            <string>/Users/daniel/Desktop/mypack/package/boost_1_59_0</string>          
            <key>MYLIBDIR</key>                                                         
            <string>/Users/daniel/Desktop/mypack/install</string>                       
            <key>New item</key>                                                         
            <string></string>                                                           
        </dict>                                                                         
    </plist> 
	
 
* One can directly: 'open ~/.MacOSX/environment.plist' and it will load an editor.

