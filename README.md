# Como instalar o Spark no meu computador ?

Uma instalação rápida e fácil sem configurações avançadas, apenas para uso prático e local do Spark.

1. Certifique-se de ter instalado uma versão do Java compatível com o Spark e o Python em sua máquina.

   - https://www.java.com/pt-BR/download/ie_manual.jsp?locale=pt_BR
   - https://www.python.org/downloads/
     * Certifique-se de reiniciar o computador caso tenha instalado o Java.

2. Certifique-se que a variável de ambiente JAVA_HOME foi configurada.

  Ex: `C:\PROGRA~1\Java\JDK-11~1.15`

3. Crie um diretório e ative um ambiente virtual com o gerenciador de sua preferência.

   ```bash
   python -m venv venv
   ```

4. Instale o Pyspark.

   ``` bash
   pip install pyspark
   ```

5. Instale o findspark (Opcional).

   ```bash
   pip install findspark
   ```

6. Instale o Jupyter notebook (Opcional).

   ``` bash
   pip install notebook
   ```

7. Crie um arquivo main.py e teste seu código spark.

   7.1 Caso tenha seguida o passo 5.

   ```python
   import findspark 
   findspark.init()
   ```

   7.2 Se não.

   ```python
   import os
   os.environ['PYSPARK_PYTHON'] = r'venv\Scripts\python.exe'
   os.environ['PYSPARK_DRIVER_PYTHON'] = r'venv\Scripts\python.exe'
   ```

   

   ```python
   from pyspark.sql import SparkSession
   spark = SparkSession.builder.appName('LocalApp').getOrCreate()
   source = [('Fulano', 30)]
   
   if __name__ == '__main__':
       df = spark.createDataFrame(data=source, schema=['Nome', 'Idade'])
       df.show()
   ```

8. Execute em seu terminal, python main.py ou jupyter notebook. 
