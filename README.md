# Kroshu Tools

Kroshu Tools provides scripts for managing your ROS project. 




## Installation

The easiest way to install Kroshu Tools is to clone this repository and create soft links to the scripts in /usr/bin. This way updating Kroshu Tools is as easy as doing a git pull.

```sh
git clone https://github.com/kroshu/kroshu-tools.git
sudo ln -s /home/user/kroshu-tools/src/kroshu_setup/usr/bin/kroshu_setup /usr/bin/kroshu_setup
```

## Instrucions

#### kroshu_setup: 

The script kroshu_setup initializes your ROS package for continuous integration. It adds neccesary configuration files for Travis CI and SonarQube, installs the TestCoverage cmake module if not already installed and extends your CMakeLists with test coverage options. 

Projects configured with kroshu_setup use a fork of the ros-industrial/industrial\_ci repository. The kroshu fork extends the industrial\_ci by adding SonarQube analysis with test coverage included. In order to use SonarQube, your GitHub organization needs to be set up with SonarCloud or an own SonarQube server, and the SONAR\_TOKEN environment variable needs to be set. More information about setting up SonarCloud with GitHub and Travis CI can be found [here](https://sonarcloud.io/documentation/integrations/github/).

Go inside your ROS package directory and run kroshu_setup with your GitHub organization as input argument. The script makes the following changes to your project:

 - Create .travis.yml file for configuration with Travis CI
 - Create sonar-project.properties file for configuration with SonarQube
 - Create src and test folders if they didn't already exist
 - Append the CMakeLists.txt file with test coverage option. Note: By default no files are checked for coverage. Targets have to be added in CMakeLists.txt explicitly.

Note: if you don't have the TestCoverage cmake module installed (e.g. first time use), you will need to run the script as root. This will install TestCoverage.cmake to /usr/lib/cmake/TestCoverage.

