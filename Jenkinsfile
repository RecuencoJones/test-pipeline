def withDefaults(props = [], body) {
    props << [$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '2', artifactNumToKeepStr: '1', daysToKeepStr: '5', numToKeepStr: '5']]
    
    properties(props)
    
    try {
        body()
    } catch(Exception ignored) {
        currentBuild.result = 'FAILURE'
    }
}

node {
    withDefaults([
        parameters([
            string(defaultValue: 'value', description: '', name: 'KEY'),
            string(defaultValue: 'value', description: '', name: 'KEY2'),
            booleanParam(defaultValue: false, description: '', name: 'FAIL')
        ])
    ]) {
        stage('Test') {
            echo params.KEY
            echo params.KEY2
            
            if (params.FAIL) {
                throw params
            }
        }
    }
}
