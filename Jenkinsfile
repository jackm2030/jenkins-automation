pipeline {
    agent any
    environment {
        SQL_SERVER = 'adfbyexample-sqlj.database.windows.net'
        SQL_DATABASE = 'Databasesqljack2050'
        SQL_USER = 'adfbyexample-admin'
        SQL_PASSWORD = 'AzureDB_@dm1n23'
    }
    stages {
        stage('Crear Tabla en Azure SQL') {
            steps {
                script {
                    // Guardar el script SQL en un archivo temporal
                    def sqlFile = 'create_table.sql'
                    writeFile file: sqlFile, text: """
                        CREATE TABLE Productos (
                            ID INT IDENTITY(1,1) PRIMARY KEY,
                            Nombre NVARCHAR(100) NOT NULL,
                            Precio DECIMAL(10,2) NOT NULL,
                            FechaRegistro DATETIME DEFAULT GETDATE()
                        );
                    """

                    // Ejecutar el script en Azure SQL usando autenticación SQL Server
                    sh """
                        /opt/mssql-tools/bin/sqlcmd -S $SQL_SERVER -d $SQL_DATABASE -U $SQL_USER -P $SQL_PASSWORD -i $sqlFile
                    """
                }
            }
        }
    }
}

