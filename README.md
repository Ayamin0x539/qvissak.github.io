# qvissak.github.io
Personal and professional website with project and resume details.

# How To Create Your Own Website (w/ configurations)
Please note that my machine is a windows machine running Windows 10. Set-up instructions may vary slightly with other OS (operating systems).
In order to set up a website yourself, follow these simple steps:
1. Make sure you have a clear understanding of HTML (Hyper Text Markup Language), JavaScript (not the same as Java) and CSS (Cascading Style Sheet Computing).

2. Install a text-editor, such as Notepad++, Atom or Vim.

3. If you would like to post your code publically or even keep it private and accessible from any computer, set up a Github repository.
  3.1 Install Git and set up your text editor in your local PATH.
  3.2 Create an account on github.com.
    3.2.1 Make sure to name your repository your-username.github.io so that you'll be able to host your website for free. You are allowed one domain per Github account.
    3.2.2 If you want to use an existing repository, you can rename it online. Be careful when renaming it especially with multiple contributors because changes might be lost and re-cloing might be necessary.
    3.2.3 Visit https://pages.github.com for more information. You could also customize your own URL by purchasing a domain name from a DNS provider.
  3.3 Follow the simple steps to create your first repository. Be sure to initialize your repository with a README.md in order to clone it to your computer.
  3.4 Clone the repository. Open the Git Bash, and type "git clone https://www.github.com/your=account/your-project-name".
  3.5 Navigate into the repository by typing "cd your=project-name".
  3.6 Type "ls" to see the README.md file. If you can see this file, you have successfully cloned your repository.
  3.7 Edit the README.md file by typing "atom README.md" or open with your preferred text editor.
  3.8 Once you make a change, save and navigate back to your project directory. Your changes are in your working directory.
  3.9 Type "git add README.md" to add your changes to README.md to your staging area.
  3.10 Type "git commit -m "First commit change to README file."" to commit all your changes in the staging area to the local repository.
  3.11 Type "git push" to push all your changes in the local repository to the remote repository.
  3.12 Type "git status" to verify your commit. It is a good habit to do this before and after commits to prevent mistakes.
  3.13 Type "git pull" to get changes from the repo if you have other people adding to the repository.

4. Install a web server program to create a working environment (e.g. Apache, Lighttpd, IIS, nginx). We will use Apache, which is open source and free to use.
  4.0 Note: Apache is pre-installed on Mac OS X. In the world of DNS (Domain Name System), every machine/computer knows the address: localhost. This is a reference to your own server, located on your personal machine. You can hit localhost in the address bar of your browser without even being connected to the Internet. Localhost actually points to a reserved IP address of your own personal machine.
  4.1 Install Visual C++ Redistributable for Visual Studio 2012. This Microsoft software package contains dependencies for the Windows version of Apache server.
  4.2 To install an Apache web server, use a binary distribution (ApacheHaus, Apache Lounge, BitNami WAMP Stack, WampServer, XAMPP) to deploy Apache httpd, optionally along with PHP and MySQL. We will use Apache Launcher found here: https://www.apachelounge.com/download/. Apache Lounge distributes Windows versions of the latest Apache build. You can download from the official Apache site, but will then need to compile your own build, which is well beyond the scope of this tutorial.
  4.3 Download the zip file for your machine and extract its contents. Move the Apache24 folder to your root directory specified in the README file or C:/Apache24 for Windows 10. Note: if you move the folder to another directory, you will have to change many configurations in the httpd.conf file found in C:/Apache24/conf. See below on changing those configurations if you move the folder to a different directory. Please note even if you move Apache24 to the default directory, you will have to edit the document and perform step 4.3.3 and 4.3.7 regardless.
    4.3.1 Open httpd.conf in a text editor, such as notepad++ or atom.
    4.3.2 Find the line that starts with ServerRoot (approximately line 37). Change it to "ServerRoot "your-directory-here/Apache24"", include the quotes around your directory path.
    4.3.3 Find the line that contains ServerName (approximately line 222). Remove the pound sign (#) that precedes it. Then change it to "ServerName localhost:80". This will mean that you access your web server by typing localhost into your browser (http://localhost/).
    4.3.4 Find the line that starts with DocumentRoot (approximately line 246). Change it to reflect the position of your document root, which should be: "DocumentRoot "your-directory-here/Apache24/htdocs". The document root is where Apache looks for your website files.
    4.3.5 Then change the line directly below it to match the new position: "<Directory "your-directory-here/Apache24/htdocs">".
    4.3.6 Scroll down to the line that has DirectoryIndex index.html (approximately line 280). Add "index.php" in there or any other files you need your server to recognize as index files. For example: "DirectoryIndex index.php index.html index.js index.css".
    4.3.7 Save and close the file with your changes.
  4.4 Navigate to C:/Windows/System32/drivers/etc in windows explorer.
  4.5 Open the hosts file with a text editor as an administrator and add the following line before everything (on its own line): "127.0.0.1 localhost" without the quotes. This tells windows that when you try to navigate to localhost in a browser, it should direct the requests to your own computer. Save the file and close.
  4.6 Navigate to the Apache24/bin folder. Execute httpd.exe to run your server. It should be a blank black screen without any error messages. With your server running (you have to run the executable whenever you want localhost to work), you can use localhost (type it into your browser, like: http://localhost/) to access your web files. Your server uses the web files in Apache24/htdocs. There will already be a simple HTML file in there.
  4.7 You will want to move your document root somewhere other than the default htdocs folder. Open the httpd.conf file again and change the location for the DocumentRoot and the following line (approximately lines 246 and 247): "your-git-repo-directory-on-your-local-machine". You can have it anywhere you want. Note: any changes you make to the httpd.conf file will require a restart of the web server (close it and open it again) to take effect. Example of a document root path: C:\Users\Your-Name\Your-Repo-Name
  4.8 Enable mod_rewrite on your Apache server. Search for the line that contains mod_rewrite.so (in http.conf) and remove the preceding pound sign (#). Save the file and close.
  4.9 If you are experiencing difficulties and step 4.6 does not work after doing the latter steps, then follow the advice below.
    4.9.1 Open cmd. Type "netstat -a -o -n" and hit enter. Scroll up to the IP with port 80 (near the top). Write down the PID.
    4.9.2 In cmd type "taskkill /F /PID #" where # is the number you wrote down in the previous step. Hit enter.
    4.9.3 If you are unable to stop the server on that port from running, open your httpd.conf again. Change everywhere 80 is in the document to another port, say 3000. Start your local by typing in http://localhost:3000.
Note: if you are only going to be developing in html/css files with minor JavaScript, you can type the file path into your browser where your files are saved to render the page. Using a server regardless, however is excellent practice and a necessary tool when using a complex framework to sculpt your project.

5. Install Node.js and npm (make sure PATH is set correctly, it should automatically set with install). Check to see if you have it by opening Git Bash and typing "node -version" and "npm -version". Npm should install with Node automatically.
Note: Node.js is a great framework to use. It is optional but highly recommended for any website with JavaScript.

6. In your text editor, create a file called "homepage.html" and save it in your repo directory. Modify it to your heart's desire. You'll also probably create some .js files as well as a couple .css files. Have fun with it. If you are looking for a challenge, and to properly parse your code into components and modules, look into using React.js, a JavaScript library that allows you to build and render html-like code (actually called JSX) within your JavaScript files; especially useful for componentizing your code for reuse and customization.

7. Launch your website for the world to see.
  7.1 Navigate to your repository on GitHub.
  7.2 Click on the settings tab.
  7.3 Make sure your project repository name matches your username in the format your-username.github.io
  7.4 Rename your landing page file to index.html and put it in the root directory. Don't forget to update any references to that file or in that file.
  7.5 Go to https://your-username.github.io to see your hard work!

8. Change your URL to something more custom. You'll have to pay a DNS-provider for the URL.
