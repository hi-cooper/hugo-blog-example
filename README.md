# hugo-blog-example
create blog with hugo + LoveIt, and automate deployment with Netlify

# 1 Create a repository on github

> repository name: hugo-blog-example

# 2 Netlify settings

> see: https://www.netlify.com/

When you commit to Github, Netlify will automatically compile and publish

# 3 Create a blog with Hugo

> see: https://gohugo.io/getting-started/quick-start/

## 3.1 Create

```shell
hugo new site hugo-blog-example
cd hugo-blog-example
git init --initial-branch=main
git remote add origin git@github.com:hi-cooper/hugo-blog-example.git
git pull origin main:main
```

## 3.2 Modify theme

```shell
git submodule add https://github.com/dillonzq/LoveIt themes/LoveIt
```

a）copy `./themes/LoveIt/exampleSite/*` to root path (override existing files)

b）open `config.toml`, and comment `themesDir = "../.."`

## 3.3 Configure Netlify

create a new file at /`netlify.toml`

```toml
[build]
  command = "hugo"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.111.3"
```

## 3.4 Push to Github

```shell
git add -A
git commit -m 'init project'
git push origin main
```

## 3.5 visit

> url: https://cooperzhu.netlify.app

# 4 Local build

```shell
hugo server --buildDrafts   # start Hugo’s development server (include draft content)
hugo server -D              # start Hugo’s development server
hugo                        # Publish the site (the entire static site in the public directory in the root of your project)
```

