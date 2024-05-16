# Continuous Integration and Continuous Deployment (CICD) Automation

This repository contains a Node.js script (`CICD.js`) designed to automate Continuous Integration and Continuous Deployment (CICD) processes for your projects. The script is configured via a JSON configuration file (`config.json`) or name it as you like.

## How it Works

The script monitors a specified Git repository for changes and triggers the following actions upon detecting a change:

1. **Version Monitoring**: The script continuously monitors the specified Git repository's `main` branch for changes in version.
2. **Automated Build and Deployment**: When a change in the version is detected, the script automatically clones the repository, executes specified build commands, and deploys the built program to the deployment folder.
3. **Folder Cleanup**: Optionally, the script can clean up a specified folder after the deployment process is completed.

## Requirements

- Node.js installed on your system.
- Git installed on your system.
- Access to the Git repository you want to monitor.
- Configuration file (`config.json`) containing build and deployment instructions.

## Setup

1. Clone this repository to your local machine.
2. Edit the configuration file (`config.json`) following its content.
3. Customize the configuration file according to your project requirements, specifying build commands, deployment paths, and the Git repository to monitor.

## Usage

1. Ensure the configuration file (`config.json`) is correctly configured.
2. Run the script:
   ```
   node CICD.js --config ./config.json
   ```
   or using pm2
   ```
   pm2 start CICD.js --name YOUR-PROCESS-NAME -- --config "path/to/config/file"
   ```
4. The script will start monitoring the specified Git repository and execute the defined CICD processes upon detecting changes.

## Configuration File (`config.json`)

The configuration file (`config.json`) contains the following parameters:

- **build**: An array of objects specifying the build process. Each object includes the working directory and build commands.
- **mouve**: An array of commands to move the built program to the deployment folder.
- **clearFolder**: (Optional) The folder to be cleaned up after deployment.
- **repo**: The URL of the Git repository to monitor.
- **cron**: the cron expression of the interval you want the program to run at.
