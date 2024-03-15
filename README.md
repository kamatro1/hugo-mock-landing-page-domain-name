# 🌐 hugo-mock-landing-page-domain-name

This project is for CIS 3500 Spring 2024 Homework 2 Part III.

In Homework 1, we cloned the [`hugo-bootstrap-theme` by Felipe Carneiro](url) before customizing the landing page to a product of our choice. We had to choose 6 features to highlight on the landing page, 3 of which were illustrated. These features were derived from user stories, which are also included in this repo.

## 🚀 Deployment

In this repo, we imported the `hugo-mock-landing-page-autodeployed` repo from Homework 2 Part II, and updated the `baseURL` in the `config.toml` file. We then configured the repository settings to allow the Workflow to have read and write permissions, ensure the publishing source is `gh-pages`, and allow all actions and reusable workflows.

Then, we bought a domain name on [NameCheap] (https://www.namecheap.com). To match the name of my product, I bought dailyxpert.co (http://dailyxpert.co/). We configured the domain name to point to our GitHub Pages website, before updating the 'gh-pages-deployment.yaml' workflow file in the '.github/workflows/' directory of this repo to have the cname set to our new domain name.

## 🤝 Contributing

If you find any issues or have suggestions for improvement, please feel free to open an issue or submit a pull request.

## 📄 License

This project is licensed under the [MIT License](LICENSE).
