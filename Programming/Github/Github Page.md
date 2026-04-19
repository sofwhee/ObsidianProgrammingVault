https://docs.github.com/en/pages/quickstart


6. Under your repository name, click  **Settings**. If you cannot see the "Settings" tab, select the  dropdown menu, then click **Settings**.
    
    ![Screenshot of a repository header showing the tabs. The "Settings" tab is highlighted by a dark orange outline.](https://docs.github.com/assets/cb-28260/images/help/repository/repo-actions-settings.png)
    
7. In the "Code and automation" section of the sidebar, click  **Pages**.
    
8. Under "Build and deployment", under "Source", select **Deploy from a branch**.
    
9. Under "Build and deployment", under "Branch", use the branch dropdown menu and select a publishing source.
    
    ![Screenshot of Pages settings in a GitHub repository. A menu to select a branch for a publishing source, labeled "None," is outlined in dark orange.](https://docs.github.com/assets/cb-47265/images/help/pages/publishing-source-drop-down.png)
    
10. Optionally, open the `README.md` file of your repository. The `README.md` file is where you will write the content for your site. You can edit the file or keep the default content for now.
    
11. Visit `username.github.io` to view your new website. Note that it can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub.
    

## [Changing the title and description](https://docs.github.com/en/pages/quickstart#changing-the-title-and-description)

By default, the title of your site is `username.github.io`. You can change the title by editing the `_config.yml` file in your repository. You can also add a description for your site.

1. Click the **Code** tab of your repository.
    
2. In the file list, click `_config.yml` to open the file.
    
3. Click  to edit the file.
    
4. The `_config.yml` file already contains a line that specifies the theme for your site. Add a new line with `title:` followed by the title you want. Add a new line with `description:` followed by the description you want. For example:
    
    ```yaml
    theme: jekyll-theme-minimal
    title: Octocat's homepage
    description: Bookmark this to keep an eye on my project updates!
    ```
    
5. When you are done editing the file, click **Commit changes**.
    

## [Next Steps](https://docs.github.com/en/pages/quickstart#next-steps)

For more information about how to add additional pages to your site, see [Adding content to your GitHub Pages site using Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll#about-content-in-jekyll-sites).

For more information about setting up a GitHub Pages site with Jekyll, see [About GitHub Pages and Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll).