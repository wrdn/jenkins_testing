// in this array we'll place the jobs that we wish to run
def branches = [:]

//running the job 4 times concurrently
//the dummy parameter is for preventing mutation of the parameter before the execution of the closure.
//we have to assign it outside the closure or it will run the job multiple times with the same parameter "4"
//and jenkins will unite them into a single run of the job

for (int i = 0; i < 4; i++) {
  def index = i //if we tried to use i below, it would equal 4 in each job execution.
  branches["branch${i}"] = {
    stage("a_${index}") {
      echo index.toString()
    }
    stage("b_${index}) {
          echo "something else..."
    }
  }
}
          
pipeline {
  agent any
  stages {
    script {
      parallel branches
    }
  }
}
