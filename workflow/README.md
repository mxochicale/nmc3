# Slides

**00.** Create repository    
**01.** clone it locally  
**02.** create .gitignore  

### (a) Github Actions
#### Setting it up
**01.** Add `shh-rsa` key in https://github.com/settings/keys following [the documentation](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) in github.

**02.** Add a new secret variable called `DEPLOY_KEY` in 
https://github.com/mxochicale/nmc3/settings/secrets 

Where the value is taken from `id_rsa` with 
vim ~/.ssh/id_rsa   
which looks like:  
```
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```


**03.** Create github action workflow
`.github/workflow/*.yml` and then create main.yml 
```
mkdir -p .github/workflows
cd .github/workflows && wget https://raw.githubusercontent.com/mxochicale/learning-latex-action/master/.github/workflows/main.yml
```
* Setting up variables for pdf documents and keys in .github/workflows/main.yml. 
See this [main.yml](https://github.com/mxochicale/learning-latex-action/blob/master/.github/workflows/main.yml) as example.



**03.** Commit genesis in the master using `[skip ci]` to the master branch


**04.** Raise an issue

**06.** Create a generated-pdfs branch for the pdf files [(see more)](https://www.freecodecamp.org/forum/t/push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too/13222).
```
git checkout -b generated-pdfs
rm -rf * README.md .github .gitignore *swp ~.git 
git add -A
git commit -m 'clean generated-pdfs branch'
git push origin generated-pdfs
```

**07.** Create branch for drafting document
```
git checkout master
git checkout -b 01-drafting-slides
```

**08.** add latex document path


**10.** commit changes
```
git add -A
git commit -m 'genesis of slides'
git push origin generated-pdfs
```

**11.** Create pull request
```
Title: [WIP] Drafting slides
Content: Resolves #1
```

### (b) Local build
# Local build in Ubuntu18.04

## Requirements 
* Install latest version of (i.e., Tex Live 2020 [:link:](https://github.com/mxochicale/latex/tree/master/installation)).
* sudo apt-get install python-pygments #https://tex.stackexchange.com/questions/40083/how-to-install-minted-in-ubuntu

## local build
make clean && make && evince main.pdf
