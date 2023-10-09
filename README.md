# Medidas DAX para Cálculo de Pareto e Formatação de Horas

Este repositório contém duas medidas DAX que podem ser usadas no Power BI:

## Medida para Cálculo de Pareto

A primeira medida é usada para calcular o percentual acumulado das ocorrências de equipamentos em relação ao total de ocorrências. Ela é útil para identificar os principais equipamentos responsáveis pela maioria das ocorrências. Você pode encontrar detalhes sobre como usá-la na seção "Medida para Cálculo de Pareto" abaixo.

## Medida para Formatar Valor de Hora

A segunda medida DAX é usada para formatar um valor numérico como uma hora no formato "hh:mm:ss". Ela é útil quando você precisa exibir valores de hora de uma maneira mais amigável nas visualizações. Você pode encontrar detalhes sobre como usá-la na seção "Medida para Formatar Valor de Hora" abaixo.

---

## Medida para Cálculo de Pareto

A medida para cálculo de Pareto é composta por quatro etapas principais:

1. **VAR TOTAL_OCORRENCIAS**: Calcula o número total de ocorrências em toda a tabela 'SSM', ignorando quaisquer filtros aplicados às visualizações.

2. **VAR TOTAL_ATUAL**: Conta o número de ocorrências na tabela 'SSM' sem considerar quaisquer filtros. Isso representa o número total de ocorrências na visualização atual.

3. **VAR TB_RESUMO**: Cria uma tabela resumida que inclui todos os equipamentos únicos da tabela 'SSM' e calcula o número de ocorrências para cada equipamento.

4. **VAR TOTAL_ACUMULADO**: Calcula a soma acumulada das ocorrências para os equipamentos que têm um número de ocorrências maior ou igual ao número total de ocorrências na visualização atual.

A medida final é o resultado da divisão de `TOTAL_ACUMULADO` por `TOTAL_OCORRENCIAS`, que representa o percentual acumulado.

### Como Usar a Medida

Para usar esta medida DAX em seu projeto do Power BI, siga os seguintes passos:

1. Copie a medida DAX fornecida nesta seção.

2. Abra o Power BI Desktop e vá para a aba "Modelagem".

3. Clique em "Nova Medida" e cole a medida DAX copiada.

4. Certifique-se de que a tabela 'SSM' ou a tabela onde seus registros de ocorrências estão é a tabela de contexto correta.

5. Agora você pode usar essa medida em suas visualizações para calcular o percentual acumulado de ocorrências de equipamentos.

---

## Medida para Formatar Valor de Hora

A medida para formatação de valor de hora é usada para converter um valor numérico em um formato de hora "hh:mm:ss". Ela é útil quando você precisa exibir valores de hora de uma maneira mais amigável nas visualizações.

Aqui está como a medida funciona:

```
VAR _Value = SELECTEDMEASURE()
VAR _Hour = TRUNC ( _Value  )
VAR _DecimalMinute = ( _Value - _Hour) * 60
VAR _Minute = TRUNC ( ( _Value - _Hour) * 60 )
VAR _Second = TRUNC ( ( _DecimalMinute - _Minute ) * 60 )
RETURN
  """" & FORMAT ( _Hour, "0#;0#" ) 
       & ":" 
       & FORMAT ( _Minute, "0#;0#" ) 
       & ":" 
       & FORMAT ( _Second, "0#;0#" )
       & """"
```
### Como Usar a Medida

Para usar esta medida DAX em seu projeto do Power BI, siga os seguintes passos:

1. Copie a medida DAX fornecida nesta seção.

2. Abra o Power BI Desktop e vá para a aba "Modelagem".

3. Clique em "Nova Medida" e cole a medida DAX copiada.

4. Certifique-se de que a tabela 'SSM' ou a tabela onde seus registros de ocorrências estão é a tabela de contexto correta.

5. Agora você pode usar essa medida em suas visualizações para calcular o percentual acumulado de ocorrências de equipamentos.

---

## Contribuições

Sinta-se à vontade para contribuir com melhorias ou correções para essas medidas DAX. Basta criar um fork deste repositório, fazer suas alterações e enviar um pull request.

## Licença

Este projeto é licenciado sob a [Licença MIT](LICENSE). Sinta-se à vontade para usar, modificar e distribuir de acordo com os termos da licença.

