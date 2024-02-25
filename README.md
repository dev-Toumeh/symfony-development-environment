# php-dockerCompose-devstack
This repository is designed to serve as a foundation for projects based on PHP.

## Use the Repository as base for your Typo3 Project

1. create a new repository for your new project
2. Clone the newly created repository to your local machine.
```bash
git clone https://github.com/yourusername/new-repository-name.git
```
3. Add typo3 Remote Reference to the Existing Repository: Navigate into the cloned repository directory and add a 
    remote reference to the existing repository you want to use as a base.
```bash
git remote add typo3-dev-env https://github.com/dev-Toumeh/php-dockerCompose-devstack.git
```
4. Fetch and merge the content from the existing repository
    into your new repository.
```bash
git pull typo3-dev-env typo3 --allow-unrelated-histories
```
5. commit the changes
```bash
git commit -am "Merged PHP Docker Compose Dev Stack into the project"
```
6. push the changes to your origin main branch
```bash
   git push origin main
```
7. Cleanup (Optional): Cleanup (Optional): If you don't need the reference to the PHP Docker Compose Dev Stack anymore, you can remove it
```bash
git remote remove old-repo
```