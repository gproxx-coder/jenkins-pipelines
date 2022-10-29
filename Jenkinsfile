pipeline {
    agent any
    
    environment {
        name = 'Ganesh'
        role = 'Devops Engineer'
    }
    
    parameters {
        string(name:'username', defaultValue:'ganesh', description:'name of user')
        booleanParam(name:'male', defaultValue:true, description:'gender of user')
        choice(name:'city', choices:['pune', 'mumbai', 'delhi'], description:'city of user')
    }

	stages {
		stage('Normal Commands') {
			steps {
				sh '''
				date
				pwd
				ls
				'''
				}
			}
		stage('Global ENV variable') {
			steps {
				sh '''
				echo "<Jenkins Variable> Build_Id: ${BUILD_ID}"
				echo ${name}
				echo ${role}
				'''
				}
			}
		stage('Local ENV variable') {
		    environment {
                name = 'GP'
                role = 'Cloud Engineer'
            }
			steps {
				sh '''
				echo ${name}
				echo ${role}
				'''
				}
			}
		stage('Parameterized Pipeline') {
			steps {
				sh '''
				echo "Parameter: <username>: ${username}"
				echo "Parameter: <gender>: ${male}"
				echo "Parameter: <city>: ${city}"
				'''
				}
			}
		stage('Parametrs from user - Human Intervention') {
		    input{
		        message "Should we continue?"
		        ok "Yes, Continue"
		    }
			steps {
				sh '''
				echo "Parameter: <username>: ${username}"
				'''
				}
			}
		stage('Deploy to Prod') {
			steps {
				sh '''
				echo "Deployed to Prod> by: ${username}"
				'''
				}
			}
	}
		post {
			always {
				echo "I will always get executed NO matter what happens"
				}
			aborted {
				echo "Aborted"
				}
			success {
				echo "Success"
				}
			failure {
				echo "Failure"
				}
			}

	}
