# Skeleton build to run Kubernetes and OpenShift Origin clusters on Travis CI


# Usage

In your repo, and particularly in this example, I'm using `vim`. 

```
vi test.sh

# Add the module
git submodule add --name ci https://github.com/kubernetes/
pushd ci ; git pull ; popd
git commit -asm "Add traviskube CI submodule"

# You then need to copy the .travis.yml.
cp ci/.travis.yml .
git commit -asm "Add .travis.yml"
```

In theory, you can use 'trunk releasing'. In the above example I just used `git stash pop`. You should see something like: 

```git
stash@{0}: WIP on submit: 6ebd0e2... Update git-stash documentation
stash@{1}: On master: 9cc0589... Add git-stash
```

Make sure you have Travis CI enabled through the UI or CLI. 

# Why?

This will help users to understand if it's a straight deployment - or not. In very binary terms. 

# Troubleshooting 

If there's an issue building, try running: 

```git
git pull
...
file foobar not up to date, cannot merge.
git stash
git pull
git stash pop
```
If you have further problems, look at the logs, the logs will tell you a story: 

```git
xargs git log --merges --no-walk --grep=K8S
```
