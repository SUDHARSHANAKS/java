from github import Github

# Use your GitHub personal access token here
token = "your_personal_access_token_here"

# Authenticate with GitHub
g = Github(token)

# Create a new repository and add a README file
def create_repository_with_readme(repo_name, description="A new repository with README"):
    user = g.get_user()  # Get the authenticated user
    
    # Create the repository
    repo = user.create_repo(
        repo_name,
        description=description,
        private=True,  # Set to 'False' if you want it to be public
        auto_init=True  # Initializes the repository with a README file
    )
    
    # Add content to the README file
    readme_content = """
    # Welcome to my new repository!
    
    This is the README file for the `my-new-repository`. This repository will contain all of my exciting projects.

    ## Getting Started

    To get started with this project, clone the repository to your local machine.

    ```bash
    git clone https://github.com/your-username/{0}.git
    ```

    ## License

    This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
    """.format(repo_name)
    
    # Update the README file with custom content
    repo.create_file("README.md", "Initial commit with README", readme_content)
    
    print(f"Repository '{repo_name}' created successfully with README!")

# Call the function to create the repository and add README
repo_name = "my-new-repository"
create_repository_with_readme(repo_name)
