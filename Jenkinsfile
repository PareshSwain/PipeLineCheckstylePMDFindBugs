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
        	//bat "mvn -Dmaven.test.failure.ignore=true deploy"
        	}
		}
		}

stage('checkstyle') {
            steps {
                echo 'CheckStyle....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true checkstyle:checkstyle"
		step([$class: 'CheckStylePublisher', pattern: '**/target/checkstyle-result.xml'])	
        	}
		}
		}

stage('pmd') {
            steps {
                echo 'PMD....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true pmd:pmd"
		step([$class: 'PmdPublisher', pattern: '**/target/pmd.xml'])
        	}
		}
		}

stage('findbugs') {
            steps {
                echo 'FindBugs....'
		withMaven(jdk: 'JDK1.8', maven: 'MAVEN') {
    		// some block
        	bat "mvn -Dmaven.test.failure.ignore=true findbugs:findbugs"
		step([$class: 'FindBugsPublisher', pattern: '**/target/findbugs.xml'])
        	}
		}
		}
         
  
    }
}
