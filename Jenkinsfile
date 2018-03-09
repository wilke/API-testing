pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building... and clea up'	    
	        sh '''
		      set +x
          chmod -R a+w /tmp/.singularity-runtime.*
          rm -rf /tmp/.singularity*
	        '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
	  	          sh'''
                set +x
                source /etc/profile
                module load singularity/2.4.2
                singularity exec -B `pwd`:/scratch --pwd /scratch docker://mgrast/api-testing-env:latest make test\
	              
	              '''
            }
        }
    }
}
