# shoddyguard.me

Here lies the code for [shoddyguard.me](https://shoddyguard.me).

## Development

Development should be done against the `dev` branch. Once you're happy with the changes, create a pull request to merge into `production`.

This is done so that changes can be reviewed against the dev site before being deployed to the live site.

### Prerequisites

- Hugo (extended version) - [Installation guide](https://gohugo.io/getting-started/installing/)
- Ensure theme submodule is initialized:

  ```bash
  git submodule update --init --recursive
  ```

### Content

There are several different Hugo archetypes available for creating new content depending on the type of content you want to create.

#### Posts

To create a new post, run the following command:

```bash
hugo new content/posts/YYYY/MM/DD-post-title/index.md --kind <POST_KIND>
```

Where `<POST_KIND>` is one of the archetypes available in the `archetypes/posts/` directory.

#### Static Pages

To create a new static page, run the following command:

```bash
hugo new content/pages/page-name/_index.md
```

This should automatically pick up the `page` archetype.

### Adding icons

Head to [tabler icons](https://tabler-icons.io/) and search for the icon you want.
**Download** or **Copy SVG** and paste to `assets/icons/`.
You'll need to remove `width="24" height="24"` in the SVG file.
This should merge with the existing icons in the theme.

### Building

The following command will build the site to the `public/` directory. By passing the `-D` flag, draft posts will be included. The site will be available at `http://localhost:1313`.

```bash
hugo server -D
```

> **Note:** By default this will build the site with the `development` environment. To build with the `production` environment, use the `-e production` flag.

### Deployment

The site is hosted on Cloudflare Pages. The deployment is automated via a Cloudflare worker that triggers on changes to the `main` and `dev` branches.
(Deploying to the `production` and `development` environments respectively.)
