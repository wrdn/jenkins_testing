// in this array we'll place the jobs that we wish to run
def branches = [:]

//running the job 4 times concurrently
//the dummy parameter is for preventing mutation of the parameter before the execution of the closure.
//we have to assign it outside the closure or it will run the job multiple times with the same parameter "4"
//and jenkins will unite them into a single run of the job

compl = 0
nodeCount = 2

def RUN(index) {
  stage("first_${index}") {
    if(index == 0) { sleep 5 }
    echo "first at index ${index}"
  }
  stage("second_${index}") {
    if(index == 1) { sleep 5 }
    echo "second at index ${index}"
    compl++
  }
  stage("sync_${index}") {
    waitUntil { compl == nodeCount }
    echo "sync'd!"
  }
}

for (int i = 0; i < nodeCount; i++) {
  def index = i //if we tried to use i below, it would equal 4 in each job execution.
  branches["branch${i}"] = {
    node {
      RUN(index)
    }
  }
}

pipeline {
  agent none
  stages {
    stage("start") {
      steps {
        script {
          parallel branches
        }
      }
    }
  }
}
