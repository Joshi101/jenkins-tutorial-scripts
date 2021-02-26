pipeline {
    agent any
    environment {
	WORKSPACE = "/app/jenkins-tutrial"
	LESSFILEPATH = "./style"
	BRANDCODE = "${brandcode}" 
	TOKEN = credentials("git-token")
	PRIMARY_COLOR = "${color}"
}
    stages {
        stage('Build') {
            steps {

                sh """
                    mkdir -p ${WORKSPACE}
                    cd ${WORKSPACE}
                    if [ -d jenkins-tutorial ]
                    then 
                        rm -rf jenkins-tutorial
                    fi
                    git clone https://github.com/Joshi101/jenkins-tutorial.git
                    cd jenkins-tutorial
                    git config user.email 'ritesh.joshi101@gmail.com'
                    git config user.name 'joshi101'
                    git remote set-url origin https://Joshi101:${TOKEN}@github.com/Joshi101/jenkins-tutorial.git
                    git status
                    mkdir -p ${LESSFILEPATH}/${BRANDCODE}
                    cd ${LESSFILEPATH}/${BRANDCODE}
                    touch ${BRANDCODE}.less
                    echo @color: ${PRIMARY_COLOR} > ${BRANDCODE}.less
                    CHANGED=\$(git diff-index --name-only HEAD --)
                    echo \$CHANGED
                    if [ -n \$CHANGED ]
                    then
                        git add --all
                        git commit -m "auto commit"
                        git push
                    fi
                    """

            }

        }
     stage('Test'){
	  steps{	
		echo 'testing application'
	   }	
       }
     stage('deploy'){
	  steps{
		echo 'deploying applicationi'
	   }
        }
    }

     post {
                success {
                    sh "echo success"
                }
        }
}

