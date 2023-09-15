pipeline
{
    agent any
    parameters
    {
        choice(choices: 'dev\ntest\nstage\nwhat-if\nprod\nbatch', description: 'select the target environment.', name: 'Environment')
    }
    stages
    {
        stage("build")
        {
            steps
            {
                echo 'building the application'
            }
        }
        stage("test")
        {
            steps
            {
                echo 'testing the application'
            }
        }
        stage("deploy")
        {
            steps
            {
                echo 'deploying the application'
                sh '''
                gcloud version
                '''
            }
        }
    }
}
