# CodeIgniter Startup Script

This Bash script automates the setup of a CodeIgniter project. It modifies the default download from the [CodeIgniter website](http://codeigniter.com) such that the `application` and `system` folders are outside of the website root folder. It also (optionally) sets up GetSparks, a Git repository, [Git Flow](https://github.com/nvie/gitflow), and does the first remote Git push. Read more about all of the executed operations in the **Processes** section below.

## Requirements

1. cURL
2. Git
3. Git Flow

## Processes

1. Create the specified directory based on the project name provided
2. Get the latest version of CodeIgniter from the website
3. Extract Zip
4. Remove all index.html and .htaccess files (not needed since system files are outside of webroot)
5. Create asset folders in webroot below a dash folder
6. Create placeholder style.css and core.js files
7. Move license.txt and index.php into webroot
8. Chmod cache and log folders to 755
9. Remove the welcome controller and view
10. Install Sparks
11. Move basic .gitignore into place and create initial Git commit
12. Check for a valid remote Git repository and push to origin
13. Install Git Flow with default settings
14. Provide text instructions to complete setup

## Configuration

1. Edit setupci.cfg so that it points to the root of your remote Git server. For example, `git@github.com:bold`
2. Review the files within the 'templates' folder. We've set them up how we like them, but that may not be best for you.
3. Make sure that the Bash script is in your environment PATH

## Usage

	// create a CI project in the new_project folder with default settings
	$ setupci new_project

	// create a CI project in the new_project folder without sparks
	$ setupci new_project --no-sparks

	// create a CI project in the new_project folder without Git
	$ setupci new_project --sparks --no-git

	// create a CI project in the new_project folder without a remote Git
	$ setupci new_project --sparks --git --no-gitremote

	// create a CI project in the new_project folder without Git Flow
	$ setupci new_project --sparks --git --gitremote --no-gitflow

## To Do's

1. Better handling of command line options. Right now they have to be in the specified order.
2. Add a --quiet option to limit output
