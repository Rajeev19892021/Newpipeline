pipeline
{

    agent any
    stages
    {
        stage("Contdownload")
        {
            steps{
                git branch: 'main', credentialsId: '71633af5-521e-4323-87ac-bf5e22fe61d8', url: 'https://github.com/Rajeev19892021/Newpipeline.git'
            }
        }


        stage("Contbuild")
        {
            steps{
                sh 'mvn package'
            }
        }


         stage("Contdeploy")
        {
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '691900bb-07d4-4fd7-9f38-1a67ca515a16', path: '', url: 'http://172.31.15.51:8080')], contextPath: 'test', war: '**/*.war'
            }
        }

         stage("Conttest")
        {
            steps{
                sh 'echo "testing passed"'
            }

        }

         stage("Cont_delivery")
        {
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '8ff8ef25-2e6e-4541-a7da-e11bf594b7b4', path: '', url: 'http://172.31.35.208:8080')], contextPath: 'test', war: '**/*.war'
            }
            
        }
    }

post
{
    failure
    {
        mail bcc: '', body: 'project failed ', cc: '', from: '', replyTo: '', subject: 'project failed ', to: 'rajeevbhargava89@gmail.com'
    }
}
}