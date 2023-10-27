# GradleToMaven
This tiny windows application will use gradle cache to construct local maven. Most of the times when I'm home my access to internet is very limited or none-existing on weekends due to data prices in my country in remote areas. This will make trying to compile applications with Gradle impossible. Gradle need access internet to refresh its cache at least once a day but when your libraries exist in local maven, cache will be refereshed from local too. I compile the application in office once which will create a Gradle cache, then I update my local maven using this utility. Now I can continue using local maven instead of public, by adding reference to my local maven to project on top of existing ones; When a local copy doesn't exists, I will still need to connect to internet to fetch it, but that would be better than downloading gigs of data on a internet connection that charges me per MegaByte.

## How to use it
Create a local folder preferably in root of your drive.

From windows explorer drag that folder over this executable and it will magically copy the files from gradle cache and create a local maven in the folder you have created.
To Reference your local maven in project, add following line above your existing online repositories inside `repositories` tag

```
maven { url 'PathToYourLocalMaven' }
```

If you are running this app from console, you can run it as 

```
GradleToMaven (PathToYourLocalMaven)
```

### Example:
```
GradleToMaven Z:\maven
```

```
repositories {
    maven { url 'Z:\maven' }
    mavenCentral()
    google()
}
```


## Notes:
- For this application to work correctly, Gradle must be installed and configured correctly on your system which means setting environment variables and adding gradle to path.
- Running this application on existing local maven will not remove any files from it but will add files to it and update existing packages.
- There are situations that a package is corrupted. in such cases remove its folder, run gradle again and then run this application to re-construct the package folder.
- There is a 256 character limitation of path lentgh in Microsoft OS. This might cause some package folders to become inaccessible. Anyone would think a 42 years old limitation should have been removed by now every time OS core changed from 8bit to 16bit to 32bit to 64bits!
- This application is designed to work on windows systems, however with minor modification you can convert it to run on linux or if you wish re-write it for Java, PHP, JavaScript, Pyton, Perl or any other language you wish but remember this is AGPL license so you will need to publish your own source code too.

