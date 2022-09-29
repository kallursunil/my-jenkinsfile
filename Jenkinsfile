pipeline {
	agent { node { label 'slave1' } }
		stages {
			stage ('CleanWorkSpace') {
				steps {
					cleanWs()
				}
			}
			stage ("git-clone") {
				steps {
					sh "git clone https://github.com/ValaxyTech/hello-world.git"
				}
			}
			stage ("build-step") {
				steps {
					sh "mvn -f /home/ec2-user/workspace/pipeline1/hello-world/pom.xml clean install"
				}
			}
			stage ("deploy") {
				steps {
					sh "rm /home/ec2-user/tomcat-9/webapps/webapp.war"
					sh "cp /home/ec2-user/workspace/pipeline1/hello-world/webapp/target/webapp.war /home/ec2-user/tomcat-9/webapps/"
				}
			}
		}
}
