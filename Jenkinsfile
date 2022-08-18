node {
    stage ("Checkout AuthService"){
        git branch: 'main', url: ' https://github.com/foxwas/bahmsdfox-msdauthservice'
    }
    
    stage ("Gradle Build - AuthService") {
        bat'gradle clean build'
    }
    
    stage ("Gradle Bootjar-Package - AuthService") {
        bat 'gradle bootjar'
    }
    
    stage('User Acceptance Test - AuthService') {
	
	  def response= input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {
	    stage('Deploy - AuthService') {
	      bat 'gradle build -x test'
	      bat 'echo deployment tasks'
	    }
	  }
    }
}