# codenvy-sbt-launch-example
Example sbt build in Codenvy. It contains:
* src folder with sample HelloWorld class
* sbt folder with sbt script and sbt-launch.jar
* ant build.xml
* sbt build.sbt

Build.xml has one task which creates zip with src, sbt folders and build.sbt. 
There is also Docker configuration which:
* configures Java 8u51
* extracts zip, and copies app files to app folder and sbt files to bin folder
* adds bin folder to PATH
* executes sbt clean compile run

sbt files are included in project because I had problems downloading sbt-launch.jar (and sbt zip) from bintray (cloudfront) using wget.
