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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '71633af5-521e-4323-87ac-bf5e22fe61d8', path: '', url: 'http://172.31.15.51:8080')], contextPath: 'test', war: '**/*.war'
            }
        }
    }


}