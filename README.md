# podrun
Easy to use solution for selecting pod source installation: from remote repo or from local path. Useful for those who develop pods in both private and public repos.


## Using script
1. Put the script into the folder with the podfile. Alternatively you can place this script anywhere and add path to it into you PATH variable.
2. Create or update your podfile to the next structure:
```ruby
  source 'https://github.com/CocoaPods/Specs.git'
  
  # Check if we want to run pods from the local storage or from remote
  if "#{ENV['DC_INSTALL_LOCALLY']}" == "true"
  # Local pods
	  puts "Using local pods"
	  pod "SomePod", :path => "#{ENV['SOME_REPOSITORY_PATH']}/Pods/SomePod"
    # List all pods with paths here
  else
  # Remote pods
	  puts "Using remote pods"
	  pod 'SomePod'
    # List all pods here
  end
  ```
**NOTE:** 
  `DC_INSTALL_LOCALLY` can't be changed (it is hardcoded in script).
  `SOME_REPOSITORY_PATH` environment variable with path to the repository should be added if you want to use this example style. Generally this path can be written in any way.

3. Open console and navigate to the podfile folder
4. Run `podrun` command with necessary flags to install pods

## podrun flags
  * **-c <pod_command>** -- command, that Cocoapods should run (`pod install --verbose` by default) 
  * **-r** -- delete Pods folder and Podfile.lock file before installation (no delete by default)
  * **-l** -- install pods locally (remote by default)
  * **-u** -- make Cocoapods update repos before installing pods
  * **-h** -- show script help
