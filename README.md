# Codename One Tar Library
###### A library for reading and writing TAR files in Codename One

## Synopsis

This library is a port of the [JTar library](https://code.google.com/p/jtar/) which was originally written for J2ME to be able to read and write TAR files.  Small code changes were made by pleather...@gmail.com (see [this issue](https://code.google.com/p/codenameone/issues/detail?id=754)) to resolve the compatibility issues with p Codename One.  I merely packaged these files into a cn1lib file and made some small performance optimizations.

## License

1. JTar is distributed under [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)
2. This library also distributed under Apache License 2.0

## Requirements

1. Codename One 1.0 or higher.
2. Instructions assume you are using Netbeans to develop your app, but it should work in Eclipse also.

## Installation 

1. Download the [CN1JTar.cn1lib](https://github.com/shannah/CN1JTar/blob/master/dist/CN1JTar.cn1lib) file and copy it into your Codename One Application's "lib" directory.
2. Right click on your application's icon in the Netbeans project explorer, and select "Refresh Libs"

## Usage Examples

See the [JTar site](https://code.google.com/p/jtar/) for usage examples, but some of them may not work with this port due to CN1's lack of support for java.io.File.  This port has removed such references.  The following example is from a CN1 project and it works…  Basically it scans a tar file (passed via an input stream) looking for a file named "tour.json".  When it finds it, it reads that file's contents to a string.

```
		TarInputStream tis = new TarInputStream(myinputStream);
		TarEntry e = null;
        while ( (e = tis.getNextEntry())!= null){
            if ( e.isDirectory() ){
                continue;
            }
            String name = e.getName();
            
            name = name.substring(name.lastIndexOf("/")+1);
            if ( name.equals("tour.json")){
                String contents = Util.readToString(tis);
                //  contents now contains the string contents of the tour.json file
            }
        }
 ```
 
 ### Credits
 
 1. Library packaged by [Steve Hannah](https://twitter.com/shannah78)
 2. Original JTar Library by [Kamran](https://github.com/kamranzafar)
 3. CN1 ported by pleather...@gmail.com
 
 