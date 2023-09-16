pipeline
{
    agent any
    environment
    {
        CLOUDSDK_CORE_PROJECT = 'gen-ai-395201'
        CLIENT_EMAIL = 'jenkins-gcloud@gen-ai-395201.iam.gserviceaccount.com'
    }
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
                withCredentials([file(credentialsId: 'gcloud-creds', variable: 'GCLOUD_CREDS')])
                {
                    sh '''
                    gcloud version
                    gcloud auth activate-service-account --key-file="$GCLOUD_CREDS"
                    gcloud compute zones list
                    gcloud config get-value project
                    gcloud app deploy
                    '''
                }
            }
        }
    }
 post
    {
        always
        {
            sh 'gcloud auth revoke $CLIENT_EMAIL'
        }
    }
}
