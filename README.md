# Aurora vCard Mapper

Maps the Android vCard API to the [ez-vcard](http://github.com/mangstadt/ez-vcard) API based on [ez-vcard-android](http://github.com/mangstadt/ez-vcard)

It converts an [ez-vcard](http://github.com/mangstadt/ez-vcard) `VCard` object into the appropriate Android data fields, 
so that it can be easily added to an Android User's Contact list.

# Code Sample
```java
File vcardFile = ...
VCardReader reader = null;
try {
  reader = new VCardReader(vcardFile);
  reader.registerScribe(new AndroidCustomFieldScribe());

  ContactOperations operations = new ContactOperations(getApplicationContext());
  VCard vcard = null;
  while ((vcard = reader.readNext()) != null) {
      operations.insertContact(vcard);
  }
} finally {
  reader.close();
}
```
# Downloads
```
dependencies {
  implementation 'com.github.whyorean:aurora-vcard-mapper:v1.0'
}
```

# How to compile ?
1. Install Java JDK 8
2. Install Gradle
3. Clone the repo
4. Run the following code in root dir of the repo
```
./gradlew assembleRelease
./gradlew makeJar
```
On successful build, compiled Jar library will be available in dir `aurora-mapper/build/lib/` 

# Dependencies
`com.googlecode.ez-vcard:ez-vcard`
