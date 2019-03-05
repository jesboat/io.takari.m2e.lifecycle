# Modifications applied

- Change all Bundle-RequiredExecutionEnvironment to 8 and build with an 8 JDK. Otherwise, the build can fail because JDT doesn't include JDK libraries. Didn't look into why.

- Remove dependency on takaristats, since it's not actually required and this way it's one less thing to build

- Comment out takari's (down) repository

- Comment out `io.takari.m2e.lifecycle.test` module; it failed to launch and I don't want to bother figuring out why.

# Build

    repo=http://repo1.maven.org/maven2/.m2e/connectors/m2e/1.6.0/N/LATEST/
    env \
        JAVA_HOME=$(/usr/libexec/java_home -v 1.8) \
        mvn -X -Dm2e-core.url=$repo -DrepositoryUrl=$repo install

# Install

Remove Takari's download.takari.io repository from Eclipse, if it got added somehow. Add:

    file:// HERE /io.takari.m2e.lifecycle.repository/target/repository

Install the feature using the "Install New Software" flow.

