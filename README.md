
# Step 1: Configure GitHub Pages

1. Go to your GitHub repository in your web browser.
2. Click on the "Settings" tab.
3. Scroll down to the "Pages" section under the "Code and automation" section.
4. Under "Source," choose the branch you want to use for GitHub Pages (e.g., main).
5. If your HTML files are in a /docs folder, select /docs as the folder; otherwise, select / (root).
5. Click "Save." GitHub will provide a link to your site.
 
# Step 2: Create a GitHub Actions Workflow

1. In your repository/VSCode, create a folder called .github and then a subfolder called workflows.
2. Inside the workflows folder, create a file named deploy.yml.
3. Open the deploy.yml file and add the following content

# YML File Format

name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./  # Use ./docs if your files are in a docs folder

# Step 3: Commit the Workflow File
1. Run the following commands to add and commit the workflow file:
# git add .github/workflows/deploy.yml
# git commit -m "Message"
# git push origin <branch>
---------------------------
---------------------------

# Step 4:Generate a GitHub Personal Access Token for:  ${{ secrets.GITHUB_TOKEN }}
1. Go to your GitHub profile in your web browser and click on your profile picture in the top right corner.
2. Select "Settings" from the dropdown menu.
3. In the left sidebar, click on "Developer settings."
4. Click on "Personal access tokens," then click "Tokens (classic)."
5. Click on the "Generate new token" button.
6. Add a note (e.g., "GitHub Pages Deploy Token") and select the scopes you need (you can start with repo for full control of private repositories).
7. Click "Generate token."
8. Copy the generated token and save it somewhere  (Repo Secrets Next Step), as you won’t be able to see it again.

# Step 5: Create GitHub Repository Secrets
1. Go to your GitHub repository in your web browser.
2. Click on the "Settings" tab.
3. In the left sidebar, click on "Secrets and variables" and then select "Actions."
4. Click the "New repository secret" button.
5. For the Name, enter GITHUB_TOKEN.
6. For the Value, enter your GitHub personal access token. (To create a token, follow the next steps.)
7. Click "Add secret."

# Step 6: Update Your Site

1. To update your website, make changes to your HTML files locally.
2. Run the following commands to add and commit your changes:
# git add .
# git commit -m "Update content"
# git push origin <branch>












