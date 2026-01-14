a. Package Managers
•	A package manager is a tool that installs, updates and removes libraries that a project depends on, and keeps track of their versions in one place.
•	In backend development it saves time because we can reuse existing packages (like Express, bcrypt, mongoose) instead of writing everything from scratch, and it keeps all dependencies consistent across different machines.
•	Without a package manager, every developer would manually download libraries, copy files, and remember versions, which quickly leads to missing files, version conflicts, and very hard project setup on a new system.
b. NPM (Node Package Manager)
•	NPM is the default package manager for Node.js and the largest ecosystem of JavaScript packages on the web.
•	It is important because it lets Node.js apps easily install third‑party modules (like Express), run scripts (start, test, build), and share code as packages.
•	NPM manages dependencies using package.json: when you run npm install <pkg>, it records the package and version so anyone can run npm install and get the correct dependencies.
c. Backend Project Initialization
•	The basic command to initialize a Node.js backend project is: npm init (or the shortcut npm init -y).
•	npm init starts an interactive wizard that asks for project name, version, description, entry file etc., and then creates a package.json with those values.[codewithabdur.blogspot]
•	npm init -y does the same thing but automatically answers “yes” to all prompts and creates package.json with default values, so it’s useful for quick setups that you can edit later.
d. Files and Folders Created After Initialization
•	package.json: Main project manifest; stores project info (name, version, scripts) and dependency lists (dependencies, devDependencies) so others can install everything with a single npm install.
•	node_modules/: Folder where NPM actually downloads and stores all installed packages and their sub‑dependencies; it can become very large and is regenerated from package.json and package-lock.json.
•	package-lock.json: Auto‑generated file that locks the exact versions and full dependency tree, ensuring everyone gets identical versions when running npm install.
What to Push to GitHub (and What Not)
•	Do not push node_modules/ because it is huge, machine‑specific, and can always be recreated from the lock files; instead, add it to .gitignore.[mickythegeek.hashnode +1]
•	You must commit package.json and package-lock.json because they describe and lock your dependencies; without them, collaborators or deployment servers cannot reliably install the correct packages for your backend to run.
