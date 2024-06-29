# git-course

## Version control with Git

This is an introduction to using version control with Git and GitHub.
No prior experience with version control is assumed.
The material is based on the Software Carpentry lesson and the work of Aleksandra Pawlik, but has been heavily modified.

# Running with Docker locally for development

Instead of installing ruby and jekyll, you can use docker to run a live version of your repo locally.
As you make changes, it will recompile the changes and all you will need to do is refresh the browser.

The following command it assumes that you are inside your cloned github repo. Adapted from [this blog](https://dev.to/michael/compile-a-jekyll-project-without-installing-jekyll-or-ruby-by-using-docker-4184):

```
docker run --rm -it --volume="$PWD:/srv/jekyll" --volume="$PWD/vendor/bundle:/usr/local/bundle" \
 --env JEKYLL_ENV=development --platform linux/amd64 -p 4000:4000 jekyll/jekyll:4.0.1 \
 jekyll serve --config _config.yml,_config_dev.yml
```

You should then be able to open the live page at http://localhost:4000/

What this command does is

- `--rm` automatically removes the container when it exits
- `-it` allows you to interrupt the running server to exit with Ctrl+C
- `--volume="$PWD:/srv/jekyll"` takes the current directory indicated by `$PWD` and map it to the directory at `/srv/jekyll` within the container so that it could build it
- `--volume="$PWD/vendor/bundle:/usr/local/bundle"` this option maps the contents of the current directory's `/vendor/bundle` and maps it to `/usr/local/bundle`. The reason for this option is so that gems could be cached and reused in future builds
- `--env JEKYLL_ENV=development` allows local development.
- `jekyll/jekyll:4.0.1` this tells it to use this specific tagged version of the Jekyll container
- `jekyll serve --config _config.yml,_config_dev.yml` serves the live compiled content

If you already have jekyll installed for other projects, you can run
`jekyll serve --config _config.yml,_config_dev.yml` inside your cloned github repo.
