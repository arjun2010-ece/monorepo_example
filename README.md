## A working monorepo example with a reactapp and a next apps.

1.  In the root folder, fire the command:
      yarn init -y
      Add the "private" key as true in the root project.json then only monorepo will work.
      Then in the package.json file add "workspaces" key and add individual projects path there in a double quote.like::
      <code>
        "workspaces":["services/reactapp", "services/nextapp"],
      </code>.
      Then add the next key as "scripts" to run both the project from this root package.json file::
      <code>
         "scripts": {
            "start:react": "yarn workspace @monorepo/reactapp start",
            "start:next": "yarn workspace @monorepo/nextapp dev"
        }
      </code>

      yarn workspace command then with each project name (e.g @monorepo/reactapp) present in package.json of each project then each projects command to run the app like in reactapp its "start" and in nextapp its "dev".

      You can check the name of this commands in each projects package.json.
      In the reactapp project "start" command runs the project and in the nextapp project "dev" starts the app.


2.  Make a services folder in the root and then 2 projects one with create-react-app and other for next app 
    with individual project folder name as "reactapp" and "nextapp".

3. In each projects folders package.json put a name as "@monorepo/reactapp" and "@monorepo/nexttapp".
    "@" symbol is important to be used with root projects name "monorepo" then with a slash the other projects name like reactapp and nextapp.

4.  Go to each project and with the command "ls -la" check whether they have .git and .gitignore file. 
    Fire the command "rm -rf .git" and "rm -rf .gitignore" and uninitialise a git repo from those project folders. and then in the root "monorepo" folder, do "git init" and add global gitignore files in the root folder.
    Then we can push this global folder in the github.

5. VERY VERY IMPORTANT:: always remember that you put node_modules in gitignore files for both the subprojects. If by mistake your nodemodules is committed then that subfolder will not be pushed in github.


INSTALL/UNINSTALL A PACKAGE IN ANY SUBPROJECT FROM ROOT:::
========================================================
To install a package in any subproject from the root you have to use npm and not yarn.

Below command will do the tasks::

npm i react-hooks-use-modal --workspace=services/web

npm uninstall react-hooks-use-modal --workspace=services/web

yarn workspace services/web add react react-dom --dev






