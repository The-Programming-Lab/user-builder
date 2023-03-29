# User Builder
This repo will build and deploy all user web apps


### command to use
```bash
REPO_OWNER="<this_repo_owner>"
REPO_NAME="<this_repo_name>"

WORKFLOW_ID="<workflow_id>"
# find using url below
# https://api.github.com/repos/<REPO_OWNER>/<REPO_NAME>/actions/workflows



# Set up variables for authentication
GITHUB_TOKEN="<generated token for you account>"
# Here's how you can create a personal access token:
# Log in to your GitHub account.
# Click on your profile icon in the top-right corner of the page, and then click on "Settings".
# In the left sidebar, click on "Developer settings".
# Click on "Personal access tokens".
# Click on the "Generate new token" button.
# Give your token a descriptive name, and select the appropriate scopes for the token.
# Click on the "Generate token" button.

IMAGE_FINAL_NAME="<final_image_name>"
PROJECT_ID="<project_id>"
TO_BUILD_REPO="<repo_with_dockerfile>"


API_ENDPOINT="https://api.github.com/repos/${REPO_OWNER}/${REPO_NAME}/actions/workflows/${WORKFLOW_ID}/dispatches"

# Send the request to trigger the workflow
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: token ${GITHUB_TOKEN}" \
  -H "Content-Type: application/json" \
  -d "{\"ref\":\"main\",\"inputs\":{\"IMAGE_NAME\":\"${IMAGE_FINAL_NAME}\", \"PROJECT_ID\":\"${PROJECT_ID}\", \"BUILD_REPO_NAME\":\"${TO_BUILD_REPO}\"}}" \
  "${API_ENDPOINT}"
  ```