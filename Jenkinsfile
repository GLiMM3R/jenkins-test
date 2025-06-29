pipeline{
    agent{
        docker { image: 'oven/bun:1' }
    }
    stages{
        stage("A"){
            steps{
                sh 'bun --version'
            }
        }
    }
}