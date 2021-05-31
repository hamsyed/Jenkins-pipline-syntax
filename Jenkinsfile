/*localhost:8080/env-vars.html/  this is where you can find all the enviornment provided by Jenkins itself
pipeline{
  agent any
  enviornment{
    NEW_VERSION = '1.O.3'
    /*this need to be created Jenkins UI via Credentials plugin and Credentials binding plugin
    /*this way the credentials are present in all the stages but if u want to use in only one stage see below
    SEVER_CREDENTIALS = Credentials('sever_credentials')
  }
  stages{
    stage('git clone'){
      steps{
        echo'cloning git library'
        echo "new version ${NEW_VERSION}"
      }
    }
    stage('build and test'){
       when{
          expression{
            //* can be BRANCH_NAME OR env.BRANCH_NAME (This is provided by jenkins)
            BRANCH_NAME == 'feature1' && CODE_CHANGES == true
          }
        }
      steps{
        echo"building the code"
        withCredentials([usernamePassword(credentials: 'sever_credentials', usernameVariable: USER, passwordVariable: PASS)]){
            sh"${USER} ${PASS}"
        }
      }
    }
    stage('deploy'){
       when{
          expression{
            //* can be BRANCH_NAME OR env.BRANCH_NAME (This is provided by jenkins)
            BRANCH_NAME == 'feature1' || BRANCH_NAME == 'master'
          }
        }

      steps{
        echo "deploy the code"
        sh"ssh -i ${SEVER_CREDENTIALS}"
      }
    }
    post{
      always{
        echo "always execute this block"
      }
      success{
        echo"execute this only if successful"
      }
      failure{
        echo"execute this if build fails"
      }
    }
  }
}
