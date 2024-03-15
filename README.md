# 🌐 hugo-mock-landing-page-autodeployed

This project is for CIS 3500 Spring 2024 Homework 2 Part II.

In Homework 1, we cloned the [`hugo-bootstrap-theme` by Felipe Carneiro](url) before customizing the landing page to a product of our choice. We had to choose 6 features to highlight on the landing page, 3 of which were illustrated. These features were derived from user stories, which are also included in this repo.

## 🚀 Deployment

In this repo, we imported the `hugo-mock-landing-page` repo from Homework 1, and updated the `baseURL` in the `config.toml` file. We then configured the repository settings to allow the Workflow to have read and write permissions, ensure the publishing source is `gh-pages`, and allow all actions and reusable workflows.

Then, we added a GitHub Actions workflow to automate the website's deployment. This workflow is located in the `.github/workflows/gh-pages-deployment.yaml` file in this repo. Here is a transcript from Anthropic's Claude AI explaining the workflow line-by-line:

```yaml

name: 🏗️ Build and Deploy GitHub Pages

```

This line sets the name of the GitHub Actions workflow, which is "Build and Deploy GitHub Pages".

```yaml

on:

push:

branches:

- main # Set a branch to deploy

```

This section specifies that the workflow will run whenever there is a push event to the main branch of the repository. You can change main to any other branch name if you want to deploy from a different branch.

```yaml

jobs:

deploy:

runs-on: ubuntu-22.04

```

This section defines a job named deploy, which will run on an Ubuntu 22.04 runner.

```yaml

steps:

- name: 🔄 Check Out Source Repository

uses: actions/checkout@v3.5.1

with:

submodules: true # Fetch Hugo themes (true OR recursive)

fetch-depth: 0 # Fetch all history for .GitInfo and .Lastmod

```

This step checks out the repository's source code, including submodules (e.g., Hugo themes) and fetches the entire commit history (`fetch-depth: 0`) for accurate .GitInfo and .Lastmod file metadata.

```yaml

- name: 🛠️ Initialize Hugo Environment

uses: peaceiris/actions-hugo@v2.6.0

with:

hugo-version: "0.123.4"

extended: true

```

This step sets up the Hugo environment by installing the specified version (`0.123.4`) of Hugo with the extended option enabled.

```yaml

- name: 🏗️ Compile Hugo Static Files

run: hugo -D --gc --minify

```

This step runs the hugo command to build the static files for the website. The -D flag includes content marked as draft, --gc enables garbage collection, and --minify minifies the generated HTML, CSS, and JavaScript files.

```yaml

- name: 🚀 Publish to GitHub Pages

uses: peaceiris/actions-gh-pages@v3.9.3

with:

github_token: ${{ secrets.GITHUB_TOKEN }}

publish_branch: gh-pages

user_name: "github-actions[bot]"

user_email: "github-actions[bot]@users.noreply.github.com"

## NOTE: uncomment below if using a custom domain

## cname: mydomain.com

```

This final step publishes the built static files to the gh-pages branch of the repository, which is used by GitHub Pages to serve the website. It uses the peaceiris/actions-gh-pages action and sets the github_token to the built-in ${{ secrets.GITHUB_TOKEN }}. It also configures the Git user name and email for the commit. The cname line is commented out but can be uncommented and set to your custom domain if you're using one.

We then ensured the website is deployed correctly, updated the link to open an issue on GitHub, and verified this change was made on the deployed website.

## 🤝 Contributing

If you find any issues or have suggestions for improvement, please feel free to open an issue or submit a pull request.

## 📄 License

This project is licensed under the [MIT License](LICENSE).
