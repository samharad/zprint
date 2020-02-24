# Accelerate the uberjar startup with appcds

There exists an uberjar for zprint which requires only Java to run,
and has no external dependencies.  It starts up rather slowly, but
you can accelerate its startup a lot by using appcds (application class
data sharing) in the JVM.

There is a script which automates the setup for appcds for the zprint uberjar.

Follow these steps to use this script:

## 1. Go to the latest release for zprint
You can find the latest release [here](https://github.com/kkinnear/zprint/releases/latest).
## 2. Download the uberjar
The uberjar is called `zprint-filter-0.x.y`, where `x.y` varies.
Click on this to download it.
## 3. Put the uberjar somewhere on your path
## 4. Download the appcds setup script
The script is called `appcds`.  This is found the same place as the uberjar
(see Step #1).
## 5. Put the appcds setup script in the same directory that you put the uberjar.
## 6. Run the appcds setup script:
The setup script takes two arguments:
  * The filename of the zprint-filter that you would like to speed up with
  appcds.
  * The file name of the executable file produced by the appcds script which
  will startup the uberjar much more qickly.
```
% ./appcds zprint-filter-0.5.3 zprint
```
This will produce a script called zprint which wills startup the 
zprint-filter in about a second.  
## 7. Try it with `-v`
```
% zprint -v
zprint-0.5.4
```
This will also demonstrate the time it takes to start up the uberjar
with appcds.
## 8. Try it with `-e`
```
% zprint -e
```
This should cause the uberjar to emit the entire options map, showing
the current values for all of the configuration options.  Any option whose
value has been changed from the default will be noted by some key value
pairs indicating from where the non-default value originated.
## 9. Try it for real
```
zprint '{:width 90}' < myfile.clj
```
This will format `myfile.clj` and output the value to the terminal.  
