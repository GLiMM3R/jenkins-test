// นี่คือ Declarative Pipeline Syntax
pipeline {
    // 1. กำหนด Agent ที่จะใช้ทำงาน 'any' หมายถึงให้ Jenkins เลือก agent ที่ว่างให้
    agent any

    // 2. กำหนด Stages หรือขั้นตอนการทำงานทั้งหมด
    stages {
        // Stage ที่ 1: Build
        stage('Build') {
            steps {
                echo 'กำลังจำลองขั้นตอนการ Build...'
                // สร้างไฟล์เปล่าๆ ขึ้นมาเพื่อใช้ในขั้นตอนถัดไป
                writeFile file: 'build.log', text: "Build successful at ${new Date()}"
                echo 'Build สำเร็จ!'
            }
        }

        // Stage ที่ 2: Test
        stage('Test') {
            steps {
                echo 'กำลังจำลองขั้นตอนการ Test...'
                // ในสถานการณ์จริง ตรงนี้จะเป็นการรันคำสั่ง test เช่น mvn test, npm test
                echo 'Tests ทั้งหมดผ่าน!'
            }
        }

        // Stage ที่ 3: Archive
        stage('Archive Results') {
            steps {
                echo 'กำลังเก็บผลลัพธ์การ Build...'
                // ทำการเก็บไฟล์ build.log ที่เราสร้างไว้ในขั้นตอน Build
                archiveArtifacts artifacts: 'build.log', followSymlinks: false
                echo 'เก็บผลลัพธ์เรียบร้อย'
            }
        }
    }

    // 3. (ไม่บังคับ) กำหนด Post-build actions ที่จะทำงานหลังทุกอย่างเสร็จสิ้น
    post {
        always {
            echo 'Pipeline จบการทำงานแล้ว'
        }
        success {
            echo 'Pipeline ทำงานสำเร็จทุกขั้นตอน!'
        }
        failure {
            echo 'มีบางอย่างผิดพลาดใน Pipeline!'
        }
    }
}