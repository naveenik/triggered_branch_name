pipeline{
	agent any
	stages{
		stage('echo'){
            steps{
                script {
                    commit = checkout scm
                    println commit.GIT_BRANCH
                    a = commit.GIT_BRANCH
                    node_lbl = sh ( script: "echo $a | grep -oP '(?<=origin/).*' ",returnStdout: true ).trim()
                }
                sh "echo ${node_lbl}"
                }
					}
		stage('Git pull'){
		    steps{
				git credentialsId: 'git-cred-navin-latest', url: 'https://github.com/naveenik/read.git' , branch: '${node_lbl}"
			     }
		    }
		  }
    }
