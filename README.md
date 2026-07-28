# Criando um mapa de estados do Brasil no Power BI

## Importar e transformar os dados de população dos estados (Wikipédia)

1. Abra o **Power BI Desktop**.
2. Clique em **Obter dados** > **Web**.
3. Cole o seguinte endereço da Wikipédia:

   ```
   https://pt.wikipedia.org/wiki/Lista_de_unidades_federativas_do_Brasil_por_popula%C3%A7%C3%A3o
   ```

4. Clique em **Usar a primeira linha como cabeçalho**.
5. Clique em **Remover Linhas Superiores** e informe o valor **1**.
6. Clique em **Remover Linhas Inferiores** e informe o valor **1**.
7. Crie uma **Coluna Personalizada** chamada **Populacao** utilizando a fórmula abaixo:

   ```powerquery
   Text.Remove([#"População[3][4]"], {" "})
   ```

8. Selecione as colunas **Unidade federativa** e **Populacao**.
9. Clique em **Remover Outras Colunas**.

---

## Importar o arquivo TopoJSON e criar o mapa dos estados

1. No **Power BI Desktop**, adicione o visual **Mapa de formas (Shape Map)**.
2. Arraste a coluna **Populacao** para **Saturação da cor**.
3. Arraste a coluna **Unidade federativa** para **Localização**.
4. Abra **Formatar visual**.
5. Em **Configurações do mapa**, altere **Tipo de mapa** para **Mapa personalizado**.
6. Adicione o arquivo **`brazil.states.topo.json`**, disponível na pasta **Mapas JSON** deste diretório.
7. Em **Cores** > **Saturação da cor**, configure as cores e os valores para representar os menores e maiores valores de população.

---

> [!NOTE]
> O Power BI possui uma opção nativa chamada **Brasil: estados** em **Tipo de mapa**. No entanto, para utilizá-la corretamente, os nomes dos estados na coluna de localização devem estar **sem acentos**.
