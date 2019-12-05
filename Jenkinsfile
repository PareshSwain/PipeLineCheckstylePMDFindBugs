pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning the code..'
	git 'https://github.com/PareshSwain/CheckstylePMDTest.git'
            }
        }
        stage('Clean') {
            steps {
                echo 'Clean..'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true clean"
        	}

            }
        }
        stage('Compile') {
            steps {
                echo 'Compiling....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true compile"
        	}
		}
		}

	stage('Test') {
            steps {
                echo 'Testing....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true test"
        	}
		}
		}

	stage('Package') {
            steps {
                echo 'Packaging....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true package"
        	}
		}
		}

stage('Deploy') {
            steps {
                echo 'deploying....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true deploy"
        	}
		}
		}

stage('checkstyle') {
            steps {
                echo 'deploying....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true checkstyle:checkstyle"
        	}
		}
		}

stage('pmd') {
            steps {
                echo 'deploying....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true pmd:pmd"
        	}
		}
		}

stage('findbugs') {
            steps {
                echo 'deploying....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true findbugs:findbugs"
        	}
		}
		}
         
  
    }
}
