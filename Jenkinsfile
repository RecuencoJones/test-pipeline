node {
    properties([
            [$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '2', artifactNumToKeepStr: '1', daysToKeepStr: '5', numToKeepStr: '5']]
    ])

    try {
        properties([
          parameters([string(defaultValue: 'value', description: '', name: 'KEY')])
        ])

        stage('Test') {
          echo params.KEY
        }
    } catch(Exception ignored) {
        currentBuild.result = 'FAILURE'
    }
}
