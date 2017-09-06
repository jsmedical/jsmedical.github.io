# Corporate Website

This repository stores the source code for the JS Medical corporate website. Changes pushed to the `master` branch in GitLab *(not GitHub)* will result in changes to the live site.

Domain: <https://jsmedical.co.uk/>

When changes are pushed to this repository, it may take between 15 - 30 minutes for these to reflect on the site.

## Software stack

The website is written in [Jekyll](https://jekyllrb.com), which will generate a static HTML site to be served.

This allows pages to be templated out, and basic logic to be performed to build sites which have a limited attack vector and can be served fully from cache.

CloudFlare reverse proxies all traffic to the site, so assets will be served from cache at their edge.

The backend of the site is a load balanced (by CloudFlare) split between GitHub Pages and GitLab Pages.

## Pushing changes to the site

The repository in GitLab is synchronised with every push (and every 15 minutes) with a repository at GitHub, which is publically accessible (please bare that in mind when pushing changes).

Making a push to the `master` branch of the GitLab repo will trigger **both** a pipeline to build a new copy of the site at GitLab Pages, and a push to GitHub with a subsequent build of the site at GitHub Pages.

Pushing changes to the GitHub repo would cause the sites to become our of sync, and for the most part, you should only have write access to GitLab.

Failed pipelines should signify a failed build on both GitHub and GitLab - but in the even of a failed pipeline, please make every endeavour to either correct the issue to a pass, or revert your commit.

If you discover an issue or have a query, please log an issue in the GitLab repository.

## Best practice

Perform your changes in a different branch, test locally with a [local Jekyll build](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/), and then put in a merge request for review unless it is an emergency change.