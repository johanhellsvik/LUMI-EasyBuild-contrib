# Java instructions

Java in EasyBuild currently uses the OpenJDK distributions and no longer the ones provided
by Oracle.

Installing Java in EasyBuild needs two EasyConfigs. The one with the major version 
only creates an Lmod file telling Lmod which version of Java should be loaded when
that major version is given, while there is also a separate EasyConfig to install
the specific version. So to install, e.g., Java 11, one would use

```
eb Java-11.eb -r
```

where the `-r` is important here to ensure that also the matching actual version
gets installed.

Java can be installed in the special `partition/common` partition to avoid installing
it multiple times in the same `LUMI` stack.


-   [Java OpenJDK web site](http://openjdk.java.net)


## EasyBuild

-   [Java support in the EasyBuilders repository](https://github.com/easybuilders/easybuild-easyconfigs/tree/develop/easybuild/easyconfigs/j/Java)

-   [Java support in the CSCS repository](https://github.com/eth-cscs/production/tree/master/easybuild/easyconfigs/j/Java)


### Java 11 (LTS release)

-   The EasyConfigs come from the EasyBuilders repository with only some
    changes to the documentation, but we've also updated to the lates Java 11
    release at the time of writing from the Eclipse Adoptium Temurin project.

-   Additional change though: `JAVA_ROOT` and `JAVA_BINDIR` are also set (`JAVA_HOME` 
    is set by the EasyBlock) to ensure that all references to the system Java are
    removed when the Java module is loaded.

-   Also added sanity checks, basically to verify if the applications load.


### Java 17 (LTS release)

-   Derived from standard EasyConfigs in the EasyBuilders repository just as Java 11,
    with the same changes and version updates.
    
-   Note that the list of binaries is different from Java/11 so the sanity checks are
    also reworked.
    
