# P9-Desafio-M9

O desafio foi completado se baseando do repositório do https://github.com/ifnesi/1brc

## Resumo do código

O código define uma classe `CreateMeasurement` que gera um grande conjunto de dados de medições de temperatura para diferentes cidades.

**Funcionamento:**

1. **Dados de cidades e temperatura média:**
    - A variável estática `STATIONS` armazena uma lista de tuplas com nomes de cidades e suas temperaturas médias.

2. **DataFrame do Pandas para estações:**
    - O atributo `stations` é um DataFrame do Pandas criado a partir da lista `STATIONS`. Possui duas colunas: "names" para nomes de cidades e "means" para temperaturas médias.

3. **Inicialização da classe (método `__init__`):**
    - Este método inicializa um atributo `rng` que é um gerador de números aleatórios do NumPy.

4. **Gerando um lote de medições (método `generate_batch`):**
    - Este método recebe dois argumentos: `std_dev` (desvio padrão para variações de temperatura) e `records` (número de medições a gerar).
    - Seleciona aleatoriamente `records` linhas do DataFrame `stations` com reposição e embaralhamento.
    - Adiciona uma nova coluna "temperature" com valores gerados de uma distribuição normal com média igual à temperatura média da cidade e desvio padrão de `std_dev`.
    - Remove a coluna "means" e retorna o DataFrame com nomes de cidades e temperaturas geradas aleatoriamente.

5. **Gerando um arquivo de medições (método `generate_measurement_file`):**
    - Este método recebe vários argumentos, incluindo `file_name` (nome do arquivo de saída), `records` (número total de medições), `sep` (separador usado no arquivo de saída) e `std_dev` (desvio padrão para variações de temperatura).
    - Exibe uma mensagem indicando o processo de criação do arquivo.
    - Calcula o número de batches necessário para gerar o número desejado de registros.
    - Abre o arquivo de saída para escrita.
    - Usa uma barra de progresso (`tqdm`) para iterar pelos batches.
    - Dentro do loop, calcula os índices inicial e final para o batch atual.
    - Chama o método `generate_batch` para obter uma amostra aleatória de pares cidade-temperatura para o tamanho do batch atual.
    - Grava os dados do batch no arquivo de saída usando o método `write_csv` do Pandas com o separador e as opções de formatação especificados.
    - Após finalizar todos os batches, exibe uma mensagem indicando a conclusão do processo de criação do arquivo.

6. **Argumentos da linha de comando (bloco `if __name__ == "__main__":`):**
    - Define funções e argumentos para executar o script a partir da linha de comando.
    - Define uma verificação de tipo personalizada (`min_records`) para garantir que o argumento `records` seja um inteiro positivo válido.
    - Usa `argparse` para criar um objeto ArgumentParser para lidar com argumentos da linha de comando.
    - Define dois argumentos:
        - `-o` ou `--output`: permite especificar o nome do arquivo de saída (padrão é "measurements.txt").
        - `-r` ou `--records`: permite especificar o número total de medições a gerar (padrão é 1 bilhão).
    - Analisa os argumentos da linha de comando.
    - Cria uma instância da classe `CreateMeasurement`.
    - Chama o método `generate_measurement_file` do objeto criado, passando os argumentos analisados para nome do arquivo e número de registros.
    


# Funcionamento

link: https://drive.google.com/file/d/1pVKBkrq6Yt7Iiggl8FeSYy7iWJP-zqa7/view?usp=sharing
