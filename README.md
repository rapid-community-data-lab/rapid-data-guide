# RAPID Public Data Guide

Dev site: <https://rapid-community-data-lab.github.io/rapid-data-guide/>

## Setting up a local development environment

If you want to contribute new notebooks/sections to the data guide you should set up a local development environment:

1. [install Quarto](https://quarto.org/docs/get-started/)
2. create a fork of [this Github repository](https://github.com/rapid-community-data-lab/rapid-data-guide)
3. git clone your forked repository
4. create a Python virtual environment
5. install the Python requirements
6. create/edit notebooks in Jupyter Lab
7. preview using Quarto
8. push changes back to the repository

### Create a fork of the Data Guide repository

If you don't have permission to write directly to the `rapid-data-guide` you'll need to create your own fork.

Go to the [RAPID Data Guide repository](https://github.com/rapid-community-data-lab/rapid-data-guide) in GitHub and click on the **Fork** button. Then in the pop-up click **Create fork**.

There's [more information about forking](https://docs.github.com/en/pull-requests/how-tos/work-with-forks/fork-a-repo) in the GitHub documentation.

### Clone the `rapid-data-guide` repository

If you have permission to write to the `rapid-data-guide` repository, you can clone it directly, otherwise you need to clone your forked copy.

Go to your newly-forked repository, click on the **Code** button and copy the web url. Then from the command line run:

```bash
git clone <web url of your fork>
```

There's [more information on cloning a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) in the GitHub documentation.

### Create a Python virtual environment

There are a number of different tools and methods used to create Python virtual environments. I mostly use [pyenv](https://github.com/pyenv/pyenv) to manage different Python versions and [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv) to create virtual environments. Assuming you've installed both of these, and used `pyenv` to install Python 3.12, you can create and activate a virtual environment like this:

```bash
cd rapid-data-guide
pyenv virtualenv 3.12 rapid-data-guide
pyenv local rapid-data-guide
```

Once this is done, the virtual environment will be automatically activated anytime you enter the `rapid-data-guide` directory.

### Install requirements

You can install the current set of pinned requirements using `pip`:

```bash
pip install -r requirements.txt
```

If you're creating new notebooks, you might want to add additional Python packages. In this case you'll need to update the `requirements.in` and `requirements.txt` files. I use [pip-tools](https://github.com/jazzband/pip-tools) to manage dependencies and generate the `requirements.txt` file. First, edit `requirements.in` to add the new package name/s. Then generate the `requirements.txt` file by running:

```bash
pip-compile requirements.in
```

You can also use `pip-tools` to install packages:

```bash
pip-sync requirements.txt
```

Make sure you include the updated `requirements` files when you push your changes back to the GitHub repository.

### Create/edit notebooks

Before you start making changes, it's a good idea to create a new git branch to work in, for example:

```bash
git checkout -b my-new-notebook
```

Then start Jupyter Lab with:

```bash
jupyter lab
```

See the [author guide](/contributing/author-guide.ipynb) for some hints and tips.

Alternatively, you can create pages using Markdown.

### Preview using Quarto

To preview the rendered site, run:

```bash
quarto preview
```

This will automatically update as you make changes to the files. If your changes aren't showing up, or you're getting strange errors, try stopping the preview with {{< kbd Ctrl-C >}} and then restarting.

### Adding your changes to the repository

Once you've made your changes, you need to commit them.

```bash
git add .
git commit -m "Add my new notebook"
```

Then you can push your updated branch back to Github:

```bash
git push origin my-new-notebook
```

### Creating a pull request

You can't directly make changes to the `main` branch of the repository. To submit your additions for approval, you need to create a pull request.

If you have permission to write to the [RAPID Data Guide repository](https://github.com/rapid-community-data-lab/rapid-data-guide), click on the 'Pull requests' tab and create a pull request from the branch you just added.

If you're working in a forked version of the repository, click on the 'Pull requests' tab of the forked repository and create a pull request from your new branch.

There's more information on [creating a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork) in the GitHub documentation..

Once the pull requests has been reviewed and approved, it'll be merged into the main repository.