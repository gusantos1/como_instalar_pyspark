# Como instalar o Spark no meu computador ?

Uma instalação rápida e fácil sem configurações avançadas, apenas para uso prático e local do Spark.

1. Certifique-se que versão mais recente do Java e Python estão instalados em sua máquina.

   - https://www.java.com/pt-BR/download/ie_manual.jsp?locale=pt_BR
   - https://www.python.org/downloads/
     * Certifique-se de reiniciar o computador caso tenha instalado o Java.

2. Crie um diretório e ative um ambiente virtual com o gerenciador de sua preferência.

   Ex: C:\Users\\...\Documents\sparklocal

   ```bash
   python -m venv venv
   ```

3. Instale o Pyspark.

   ``` bash
   pip install pyspark
   ```

4. Instale o findspark.

   ```bash
   pip install findspark
   ```

5. Instale o Jupyter notebook (Opcional).

   ``` bash
   pip install notebook
   ```

6. Crie um arquivo main.py e teste seu código spark.

   ```python
   import findspark
   findspark.init()
   from pyspark.sql import SparkSession
   
   
   spark = SparkSession.builder.appName('LocalApp').getOrCreate()
   source = [('Fulano', 30)]
   
   if __name__ == '__main__':
       df = spark.createDataFrame(data=source, schema=['Nome', 'Idade'])
       df.show()
   ```

7. Execute em seu terminal, python main.py ou jupyter notebook. 
