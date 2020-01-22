pipeline {

agent any

stages
{

stage('cloning code')

{

steps

{git 'git 'https://github.com/sahitya15/maven-project.git'
}
}

stage('compile my project')
{
steps
{
withMaven(jdk: 'javapath', maven: 'mavenpath') {
    sh 'mvn compile'
}}}
    
stage('test my project')
{
steps
{
withMaven(jdk: 'javapath', maven: 'mavenpath') {
    sh 'mvn test'
}}}
    
stage('package my project')
{
steps
{
withMaven(jdk: 'javapath', maven: 'mavenpath') {
    sh 'mvn package'
}}}
    

    
        
stage('package my install')
{
steps
{
withMaven(jdk: 'javapath', maven: 'mavenpath') {
    sh 'mvn install'
}}}
	
   
	
	
stage('deploy to  tomcat')
{
steps
{
    sshagent(['tomcat']) {
	 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.33.1:/var/lib/tomcat/webapps'
						}
}
}
    
    
    

}
}
