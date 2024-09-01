pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Replace 'your-username', 'your-repo', and 'your-branch' with your actual GitHub credentials
                def githubRepo = 'https://github.com/your-username/your-repo.git'
                def githubBranch = 'your-branch'

                // Clone the repository
                git(
                    url: githubRepo,
                    branch: githubBranch,
                    credentialsId: 'github-credentials'
                )
            }
        }
        stage('Build') {
            steps {
                // Replace 'your-script' with the actual command to build your project
                sh 'your-script'
            }
        }
        stage('Upload to GitHub') {
            steps {
                // Add your GitHub credentials to the Jenkins credentials store
                withCredentials([usernamePassword(credentialsId: 'github-credentials', passwordVariable: 'GITHUB_PASSWORD', usernameVariable: 'GITHUB_USERNAME')]) {
                    // Use the git publisher to push the changes to GitHub
                    sh "git add ."
                    sh "git commit -m 'Automated commit'"
                    sh "git push origin ${githubBranch}"
                }
            }
        }
    }
}
