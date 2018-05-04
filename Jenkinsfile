#!/usr/bin/env groovy
@Library(['pipeline-lib']) _

pipeline {
    agent 'none'
    options {
        timestamps()
    }
    stages {
        stage('Compile') {
            steps {
                executeCompileStageSteps()
            }
            post {
                success {
                    executeCompileStagePostSuccessSteps()
                }
                failure {
                    executeCompileStagePostFailureSteps()
                }
            }
        }
        stage('Unit Tests and Static Analysis') {
            steps {
                executeUnitTestsAndStaticAnalysisStageSteps()
            }
            post {
                success {
                    executeUnitTestsAndStaticAnalysisStagePostSuccessSteps()
                }
                failure {
                    executeUnitTestsAndStaticAnalysisStagePostFailureSteps()
                }
            }
        }
        stage('Publish to Artifact Repository') {
            steps {
                executePublishToArtifactRepositoryStageSteps()
            }
            post {
                success {
                    executePublishToArtifactRepositoryStagePostSuccessSteps()
                }
                failure {
                    executePublishToArtifactRepositoryStagePostFailureSteps()
                }
            }
        }
        stage('Deploy to Pre-Production') {
            steps {
                executeDeployToPreProductionStageSteps()
            }
            post {
                success {
                    executeDeployToPreProductionStagePostSuccessSteps()
                }
                failure {
                    executeDeployToPreProductionStagePostFailureSteps()
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                executeDeployToProductionStageSteps()
            }
            post {
                success {
                    executeDeployToProductionStagePostSuccessSteps()
                }
                failure {
                    executeDeployToProductionStagePostFailureSteps()
                }
            }
        }
    }
    post {
        success {
            executePostPipelineSuccessSteps()
        }
        failure {
            executePostPipelineFailureSteps()
        }
    }
}
