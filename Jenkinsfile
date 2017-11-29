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
            string(defaultValue: 'value', description: '', name: 'KEY2')
        ])
    ]) {
        stage('Test') {
            echo params.KEY
            echo params.KEY2
        }
    }
}
