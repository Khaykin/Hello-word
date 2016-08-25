#!/usr/bin
node {
    echo 'xara'
}
node {
   stage 'Stage 1'
   echo 'Jopa Jopa Jopa'
   stage 'Stage 2'
   echo 'JJOOPPAA JJOOPPAA JJOOPPAA'
}
node {
    stage 'Stage 3'
    sh 'rm -rf *'
    sh 'ls -l'
    //sh 'echo AOEU=$(echo aoeu) > propsfile'
}
node{
    stage 'Stage 4'
    gitClean()
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '1', url: 'git@github.com:ARMmbed/ta-TZInfra.git']]])
}
/**
 * Clean a Git project workspace.
 * Uses 'git clean' if there is a repository found.
 * Uses Pipeline 'deleteDir()' function if no .git directory is found.
 */
def gitClean() {
    timeout(time: 60, unit: 'SECONDS') {
        if (fileExists('.git')) {
            echo 'Found Git repository: using Git to clean the tree.'
            // The sequence of reset --hard and clean -fdx first
            // in the root and then using submodule foreach
            // is based on how the Jenkins Git SCM clean before checkout
            // feature works.
            sh 'git reset --hard'
            // Note: -e is necessary to exclude the temp directory
            // .jenkins-XXXXX in the workspace where Pipeline puts the
            // batch file for the 'bat' command.
            sh 'git clean -ffdx -e ".jenkins-*/"'
            sh 'git submodule foreach --recursive git reset --hard'
            sh 'git submodule foreach --recursive git clean -ffdx'
        }
        else
        {
            echo 'No Git repository found: using deleteDir() to wipe clean'
            deleteDir()
        }
    }
}
node {
    stage 'Stage 5'
    sh './tests_builder.sh'
}
node {
    //mail bcc: '', body: 'build finished', cc: '', from: '', replyTo: '', subject: 'pipeline_news', to: 'igor.haykin@sansasecurity.com'
}