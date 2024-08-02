<br/>

## 🛠 Installation & Setup

There are three ways to use **GitProfile**. Use any.

- [Forking this repo _(recommended)_](#forking-this-repo)
- [Setting up locally](#setting-up-locally)

### Forking this repo

These instructions will get you a copy of the project and deploy your portfolio online using GitHub Pages!

- **Fork repo:** 
- **Rename repo:**
  - If you want to host your portfolio at `https://<USERNAME>.github.io`, rename your forked repository to `username.github.io` in GitHub, where `username` is your GitHub username (or organization name).
  - If you want to host your portfolio at `https://<USERNAME>.github.io/<REPO_NAME>` (e.g. `https://<USERNAME>.github.io/portfolio`), rename your forked repository to `<REPO_NAME>` (e.g. `portfolio`) in GitHub.
- **Enable workflows:** Go to your repo's **Actions** tab and enable workflows.

  ![Workflows](https://github.com/arifszn/gitprofile/assets/45073703/7e82f7d4-900c-4cb9-83f9-bcaa1ca2b910)

- **Base Value:** Open `gitprofile.config.ts`, and change `base`'s value.

  - If you are deploying to `https://<USERNAME>.github.io`, set `base` to `'/'`.

  - If you are deploying to `https://<USERNAME>.github.io/<REPO_NAME>` (e.g. `https://<USERNAME>.github.io/portfolio`), then set `base` to `'/<REPO_NAME>/'` (e.g. `'/portfolio/'`).

  ```ts
  // gitprofile.config.ts
  {
    base: '/',
    // ...
  }
  ```

- **Commit the changes:** Now commit to your **main** branch with your changes. Wait a few minutes so that the CI/CD pipeline can publish your website to GitHub Pages. You can check the progress in the [Actions](https://github.com/arifszn/gitprofile/actions) tab.

Your portfolio website will be live shortly. Any time you commit a change to the **main** branch, the website will be automatically updated. If you face any issue viewing the website, double-check the `base` value in the `gitprofile.config.ts` file. Also, check if **Source** is set to **GitHub Actions** in **Settings** ➜ **Pages** ➜ **Build and deployment**.

If you wish to add a custom domain, no CNAME file is required. Just add it to your repo's **Settings** ➜ **Pages** ➜ **Custom domain**.

As this is a Vite project, you can also host your website to Netlify, Vercel, Heroku, or other popular services. Please refer to this [doc](https://vitejs.dev/guide/static-deploy.html) for a detailed deployment guide to other services.

### Setting up locally

- Clone the project and change directory.


- Install dependencies.

  ```shell
  pnpm install
  ```

- Run dev server.

  ```shell
  pnpm run dev
  ```

- Finally, visit `http://localhost:5173/gitprofile/` from your browser.

> Alternatively, you can set up and run the project using Docker with **[Vail](https://github.com/arifszn/vail)**, a powerful tool for local development of JavaScript/TypeScript Apps.

## Customization

All the magic happens in the file `gitprofile.config.ts`. Open it and modify it according to your preference.

You can leave most of the sections empty if you don't want to display them on your portfolio.


### Themes

There are 33 themes available that can be selected from the dropdown.

The default theme can be specified.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  themeConfig: {
    defaultTheme: 'light',
    // ...
  },
};
```

You can create your own custom theme by modifying these values. Theme `procyon` will have the custom styles.

```ts
// gitprofile.config.ts
const CONFIG = {
  /**
   * Defines the custom theme colors and styles for the application.
   * The theme includes the following properties:
   * - `primary`: The primary color used throughout the application.
   * - `secondary`: The secondary color used for accents and highlights.
   * - `accent`: The accent color used for special elements.
   * - `neutral`: The neutral color used for backgrounds and text.
   * - `base-100`: The base background color.
   * - `--rounded-box`: The border radius for boxes and containers.
   * - `--rounded-btn`: The border radius for buttons.
   */
  themeConfig: {
    customTheme: {
      primary: '#fc055b',
      secondary: '#219aaf',
      accent: '#e8d03a',
      neutral: '#2A2730',
      'base-100': '#E3E3ED',
      '--rounded-box': '3rem',
      '--rounded-btn': '3rem',
    },
  },
};
```

### Google Analytics

**GitProfile** supports both GA3 and GA4. If you do not want to use Google Analytics, keep the `id` empty.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  googleAnalytics: {
    id: 'G-XXXXXXXXX',
  },
};
```

Besides tracking visitors, it will track `click events` on projects and blog posts, and send them to Google Analytics.

### Hotjar

**GitProfile** supports [hotjar](https://www.hotjar.com) to track visitor interaction and behavior. If you do not want to use Hotjar, keep the `id` empty.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  hotjar: {
    id: '',
    snippetVersion: 6,
  },
};
```

### Skills

To showcase your skills provide them here.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  skills: ['JavaScript', 'React.js'],
};
```

Empty array will hide the skills section.

### Experience

Provide your job history in `experiences`.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  experiences: [
    {
      company: 'Company Name',
      position: 'Position',
      from: 'September 2021',
      to: 'Present',
      companyLink: 'https://example.com',
    },
    {
      company: 'Company Name',
      position: 'Position',
      from: 'July 2019',
      to: 'August 2021',
      companyLink: 'https://example.com',
    },
  ],
};
```

Empty array will hide the experience section.

### Education

Provide your education history in `educations`.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  educations: [
    {
      institution: 'Institution name 1',
      degree: 'Bachelor of Science',
      from: '2015',
      to: '2019',
    },
    {
      institution: 'Institution name 2',
      degree: 'Higher Secondary Certificate (HSC)',
      from: '2012',
      to: '2014',
    },
  ],
};
```

### Projects

#### Github Projects

- **Automatic Mode:** Seamlessly showcase your top GitHub projects based on stars or last updated date.
- **Manual Mode:** Choose specific repositories to highlight.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  projects: {
    github: {
      display: true, // Display GitHub projects?
      header: 'Github Projects',
      mode: 'automatic', // Mode can be: 'automatic' or 'manual'
      automatic: {
        sortBy: 'stars', // Sort projects by 'stars' or 'updated'
        limit: 8, // How many projects to display.
        exclude: {
          forks: false, // Forked projects will not be displayed if set to true.
          projects: [], // These projects will not be displayed. example: ['arifszn/my-project1', 'arifszn/my-project2']
        },
      },
      manual: {
        // Properties for manually specifying projects
        projects: ['arifszn/gitprofile', 'arifszn/pandora'], // List of repository names to display. example: ['arifszn/my-project1', 'arifszn/my-project2']
      },
    },
  },
};
```

#### External Projects

- **Highlight Projects Beyond GitHub:** Feature projects hosted on other platforms or personal websites.
- **Control over Content:** Provide custom titles, descriptions, images, and links for each external project.

```ts
// gitprofile.config.ts
const CONFIG = {
  // ...
  projects: {
    external: {
      header: 'My Projects',
      // To hide the `External Projects` section, keep it empty.
      projects: [
        {
          title: 'Project Name',
          description:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nunc ut.',
          imageUrl:
            'https://img.freepik.com/free-vector/illustration-gallery-icon_53876-27002.jpg',
          link: 'https://example.com',
        },
        {
          title: 'Project Name',
          description:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nunc ut.',
          imageUrl:
            'https://img.freepik.com/free-vector/illustration-gallery-icon_53876-27002.jpg',
          link: 'https://example.com',
        },
      ],
    },
  },
};
```

## This Project is made with the help of [GitProfile](https://github.com/arifszn/gitprofile)