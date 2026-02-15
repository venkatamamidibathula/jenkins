# Jenkins
---

**Paramters**

- Parameters are variables whose values are chosen when a build is triggered, then used inside the job or pipeline logic.

- Typical uses: choosing environment (dev/qa/prod), branch name, version tag, feature flags, or file paths.



---
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
**Declaring and Defining Environment Variables**

```groovy

pipeline {
    agent any
    
    environment {
        
        build_filename = 'laptop'
    }

    stages {
        stage('Hello') {
            steps {
                cleanWs()
                echo 'Building a new laptop...'
                sh '''mkdir -p build
                    touch build/"${build_filename}".txt
                    echo "Mainboard" >> build/"${build_filename}".txt'''
            }
        }
    }
}

```


**Docker container as agent**

To use docker container as agent. 

```groovy


pipeline {
    agent any

    stages {
        stage('Without Docker') {
            steps {
                echo 'Hello World'
            }
        }

        stage('With Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'npm --version'
            }
        }
    }
}


```


**Workspace Synchronization**

```groovy


pipeline {
    agent any

    stages {
        stage('Without Docker') {
            steps {
                echo 'Hello World'
            }
        }

        stage('With Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
		    reuseNode true
                }
            }
            steps {
                sh 'npm --version'
            }
        }
    }
}


```

