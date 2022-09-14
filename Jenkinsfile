pipeline{
    agent none
    stages{
        // stage("Update packages"){
        //     agent{
        //         label "ansible"
        //     }
        //     options{
        //         timeout(time: 10, unit: 'MINUTES')
        //     }
        //     steps{
        //         withCredentials([file(credentialsId: 'web-pki', variable: 'SSH_KEY')]) 
        //         {
        //             ansiblePlaybook(
        //                 playbook: 'pre-requirements.yml',
        //                 inventory: 'hosts',
        //                 become: 'yes', 
        //                 becomeUser: 'root',
        //                 extraVars: [
        //                     ansible_ssh_private_key_file: "${SSH_KEY}"
        //                 ]
        //             )
        //         }
        //     }
        //     post{
        //         success{
        //             echo "========Update packages Successfully========"
        //         }
        //         failure{
        //             echo "========Update packages failed========"
        //         }
        //     }
        // }
        stage("Deploy Pro&Gra"){
            agent{
                label "ansible"
            }
            options{
                timeout(time: 10, unit: 'MINUTES')
            }
            steps{
                withCredentials([file(credentialsId: 'web-pki', variable: 'SSH_KEY')]) 
                {
                    ansiblePlaybook(
                        playbook: 'playbook.yml',
                        inventory: 'hosts',
                        become: 'yes', 
                        becomeUser: 'root',
                        extraVars: [
                            ansible_ssh_private_key_file: "${SSH_KEY}"
                        ]
                    )
                }
            }
            post{
                success{
                    echo "========Deploy Pro&Gra Successfully========"
                }
                failure{
                    echo "========Deploy Pro&Gra failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========Pipeline's Result========"
        }
        success{
            echo "=> pipeline execution successfully"
        }
        failure{
            echo "=>pipeline execution failed"
        }
    }
}