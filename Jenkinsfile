pipeline {
    agent any
    enviornment {
	WORKSPACE = "/app/jenkins-tutrial"
	BRANDCODE = $brandcode 
}
    stages {
        stage('Build') {
            steps {

                sh '''if [ -d jenkins-tutorial ]
                    then 
                        rm -rf jenkins-tutorial
                    fi
                    git clone https://github.com/Joshi101/jenkins-tutorial.git
                    cd jenkins-tutorial
                    git config user.email 'ritesh.joshi101@gmail.com'
                    git config user.name 'joshi'
                    git remote set-url origin https://Joshi101:ba81dc97636feb1ed3e00adca8fe370f7b6aef4f@github.com/Joshi101/jenkins-tutorial.git
                    git status
                    echo creating ${BRANDCODE}
                    touch ${BRANDCODE}.txt
                    CHANGED=$(git diff-index --name-only HEAD --)
                    if [ -n "$CHANGED" ]
                    then
                        git add --all
                        git commit -m "auto commit"
                        git push
                    fi
                    '''

            }

        }
     stage('Test'){
		echo 'testing application'
	}
     stage('deploy'){
		echo 'deploying applicationi'
        }
     post {
                success {
                    sh "echo success"
                }
        }
    }
}

