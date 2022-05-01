pipeline {
  agent any
  parameters {
    string(name: 'link', defaultValue: 'https://github.com/Sahakanush/Pipeline_Library.git')}
  stages {
stage('Checkout "Tasks" Repo')  {
      steps {
        dir('TasksRepo') {
          git branch: 'master', url: "${params.link}"
          sh "ls"
        }
      }
    }
    stage('gource')  {
      steps {
        sh "gource -1280x720 --stop-at-time 3 -o gource.ppm"
        sh "ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i gource.ppm -vcodec libx264 -preset medium -pix_fmt yuv420p -crf 1 -threads 0 -bf 0 gource.mp4"
      }
    }
    
  }
}
