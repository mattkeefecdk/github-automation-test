# Simple Instructions for Setting Up YAML in VSCode
*While these settings can be used for many different platforms, the test is targetted at GitHub Actions.*

1. Download and install the YAML VSCode extension: https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml
2. Visit SchemaStore.org: https://www.schemastore.org/json/
3. Open the `GitHub Workflow` Schema from SchemaStore.org, and copy all of the text from the Schema
4. Create a folder and file for your schema in the repository you're working with called `schemas/githubWorkflow.json`, and paste the copied text from the Schema.
5. In VSCode, open settings. Then search for **"YAML"** in Settings. This should bring up the settings for the YAML extension you installed.
6. Scroll to the "Yaml: Custom Tags: Custom tags for the parser to use", and click on the link to edit in settings.json
7. Within the `yaml.schemas` setting, add the following line: `"./schemas/githubWorkflow.json": ["*.yml"]`. This should result in something like the following. 
    ```
    "yaml.schemas": {
        "./schemas/githubWorkflow.json": ["*.yml"]
    },
    ```
8. Save `settings.json`
9. Test your settings by creating `.github/workflows/simple.yml`. Within this file add a line for `name: Simple Hello World Shell Test`. On the following line, add `on: [pu`, and you should see autocomplete for **push**. Press `[ENTER]` and close the bracket `]`. The resulting file should look like this: 
    ```
    name: Shell Command Hello World Workflow
    on: [push]

    jobs: 
      run-shell-command: 
        runs-on: ubuntu-latest
        steps: 
          - name: echo a string
            run: echo "Hello World!"
    ```
10. **push** your changes to your repository (on GitHub).
11. Visit the Actions Tab on your GitHub repository to view the running shell command you specified in your YAML file.