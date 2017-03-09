pipeline {
    agent {
        label 'build'
    }

    stages {
        stage('build & unit tests') {
            steps {
                node('build') {
                    sleep(2)
                    echo "build"
                }
            }
        }


        stage('static analysis') {
            steps {
                node('build') {
                    sleep(2)
                    echo "static"
                }
             }
        }

        stage('acceptance') {
            steps {
                parallel(
                    'chrome': {
                        node('build') {
                            sleep(2)
                            echo "chrome"
                        }
                    },
                    'edge': {
                        node('build') {
                            sleep(2)
                            echo "edge"
                        }
                    },
                    'firefox': {
                        node('build') {
                            sleep(2)
                            echo "firefox"
                        }
                        }
                )
            }
        }

        stage('staging') {
            steps {
                node('build') {
                    sleep(2)
                    echo "staging"
                }
            }
        }

        stage('manual approval'){
            steps {
                input 'Continue ?'
                echo "manual"
            }
        }

        stage('deploy') {
            steps {
                node('build') {
                    sleep(2)
                    echo "deploy"
                }
            }
        }
    }
}
