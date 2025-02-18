pipeline {
    agent any

    environment {
        DB_SERVER = "adfbyexample-sqlj.database.windows.net"
        DB_NAME = "Databasesqljack2050"
        DB_USER = "adfbyexample-admin"
        DB_PASSWORD = credentials('AZURE_SQL_CREDENTIALS')  // Credencial en Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'dev', credentialsId: 'f690bf34-dc2b-4a37-ad7d-e52d1d76c3dd', url: 'https://github.com/jackm2030/jenkins-automation'
            }
        }

        stage('Execute SQL Script') {
            steps {
                script {
                    def sqlFile = "sql-scripts/create_table.sql"  // Ruta del script SQL

                    sh '''
                    "/c/Program Files/Microsoft SQL Server/Client SDK/ODBC/170/Tools/Binn/sqlcmd.exe" -S $DB_SERVER -d $DB_NAME -U $DB_USER -P $DB_PASSWORD -i $sqlFile
                    '''
                }
            }
        }
    }
}
