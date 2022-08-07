node {
   
   	stage 'Stage 1'
   		echo 'stage1'
   	stage 'Checkout'
   		git url: 'https://github.com/lexsaints/test_Jenkins.git'
   	stage 'Build'
   		sh './build.sh'
   	stage 'Deploy'
   		sh './deploy.sh'
  
}
