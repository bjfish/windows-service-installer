Maven plugin to build installers with Windows service support
=============================================================

This plugin allows to build installers with support to be installed and run as Windows service.
Installer is based on [izPack](http://izpack.org/), [PrunSrv](http://commons.apache.org/proper/commons-daemon/procrun.html)
is used for Windows service management.

Plugin usage
------------

Add common library as a dependency:

    <dependency>
        <groupId>com.alexkasko.installer</groupId>
        <artifactId>windows-service-installer-common</artifactId>
        <version>1.0.2</version>
    </dependency>

Implement `com.alexkasko.installer.DaemonLauncher` in application launcher class:

    public class Launcher implements DaemonLauncher {
        public void startDaemon() {
            // start application background thread
        }
        public void stopDaemon() {
            // stop (interrupt) application background thread
        }
    }

Add plugin to build part of pom file:

    <plugin>
        <!-- to be run with "mvn windows-service-installer:installer" -->
        <groupId>com.alexkasko.installer</groupId>
        <artifactId>maven-windows-service-installer-plugin</artifactId>
        <version>1.0.2</version>
        <dependencies>
            <dependency>
                <groupId>com.alexkasko.installer</groupId>
                <artifactId>windows-service-installer-common</artifactId>
                <version>1.0.2</version>
            </dependency>
        </dependencies>
        <configuration>
            ...
        </configuration>
    </plugin>

Run `mvn windows-service-installer:installer` to build installer.

License information
-------------------

This project is released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)

Changelog
---------

**1.0.2** (2013-12-17)

 * initial public version