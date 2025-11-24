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

                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '71633af5-521e-4323-87ac-bf5e22fe61d8', path: '', url: 'http://172.31.44.96:8080')], contextPath: 'test', war: '**/*.war'
            }
        }

         stage("Conttest")
        {
            steps{
                sh 'echo "testing passed"'
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