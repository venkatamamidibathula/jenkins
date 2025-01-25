# Jenkins

**Clean working directory** : cleanWs()

**Post Build Artifacts** : archiveArtifacts artifacts: '{path}' 

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh 'echo "Hello World"'
                sh 'echo "Building a new laptop ....."'
                sh 'mkdir build'
                sh 'touch build/computer.txt'
                sh 'echo "MainBoard" >> build/computer.txt'
                sh 'echo "Display" >> build/computer.txt'
                sh 'cat build/computer.txt'
            }
        }
    }
    post {

        success{

            archiveArtifacts artifacts: 'build/**'
        }
    }
}

```
**Combining Multiple Steps into one**

You have to give all your commands inside ''' '''

sh '''
	....
	....
	....
'''


```groovy


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
		sh '''
			mkdir -p build
			touch build/computer.txt
			echo "Mainboard" >> build/computer.txt
			cat build/computer.txt
			echo "Display" >> build/computer.txt
			cat build/computer.txt
		'''
            }
        }
    }
    post {
        
        success{
            
            archiveArtifacts artifacts: 'build/**'
        }
    }
}


```

**Multiple stages with test validations**


```groovy

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh '''
                    mkdir -p build
                    touch build/computer.txt
                    echo "Mainboard" >> build/computer.txt
                    cat build/computer.txt
                    echo "Display" >> build/computer.txt
                    cat build/computer.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the laptop..........'
                sh 'test -f build/computer.txt'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'build/**'
        }
    }
}

```




