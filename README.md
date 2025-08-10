# Painel: Indicadores Macroeconômicos dos EUA (Inflação, Juros e M2)

**Descrição**  
Painel em Power BI que monitora indicadores macroeconômicos dos Estados Unidos: **Fed Funds Rate**, **Inflação (CPI - média móvel/12 meses)** e **Oferta Monetária M2**. O objetivo é acompanhar tendências e apoiar análises sobre política monetária e riscos inflacionários.

---

## 🔎 Visão geral do painel
- Layout com três KPIs principais no topo:
  - **Último Fed Funds Rate**
  - **Média da Inflação** (últimos 12 meses)
  - **Oferta Monetária M2** (em trilhões de US$)
- Visualizações:
  - Linha e barras comparando Fed Funds Rate vs Inflação por período.
  - Evolução da inflação (média móvel / 12 meses).
  - Evolução da oferta monetária M2 (gráfico de área).
- Filtros para explorar por ano e por mês.

---

## 📌 Indicadores (exemplo presente no painel)
- **Fed Funds Rate (efetiva):** 4,33 %  
- **Média da Inflação (12 meses):** 3,59 %  
- **Oferta Monetária M2:** US$ 21,94 trilhões

> **Observação:** esses valores refletem os números atualmente exibidos no painel. Recomenda-se validar periodicamente com as fontes oficiais (FRED, BLS, publicações do Federal Reserve).

---

## 🔁 Como atualizar os dados (passo a passo rápido)
1. **Obter os dados brutos**:
   - M2: série mensal do M2 (nominal) — FRED.
   - Inflação: CPI mensal — BLS (calcular variação anual ou média móvel 12 meses).
   - Fed Funds: taxa efetiva mensal — FRED.
2. **Salvar/atualizar CSVs** em `/data` mantendo nomes e colunas consistentes (`Date`, `Value` ou similar).
3. **No Power BI**:
   - `Home > Transform data` → confirmar tipos de coluna (Date como Date).
   - Atualizar consultas e clicar em **Refresh**.
4. **Verificar/ajustar medidas DAX** (ex.: inflação 12m, conversão de M2 para trilhões).
5. **Publicar**: `File > Publish` para o workspace do Power BI (se aplicável).

---

## 🧮 Medidas DAX úteis (card Oferta Monetária M2)
```DAX
M2_Ultimo_card = 
VAR UltimaData = MAX('EUA-macro_data_25yrs_ptBR'[Date])
VAR Valor = 
    CALCULATE(
        MAX('EUA-macro_data_25yrs_ptBR'[M2_Money_Supply]),
        'EUA-macro_data_25yrs_ptBR'[Date] = UltimaData
    )
RETURN
FORMAT(Valor, "#,0.00") & " Tri"
```
> Ajuste nomes de tabelas e colunas conforme seu modelo.

---
## Resultado Final 
<img width="1082" height="606" alt="Painel_Final_economico _EUA" src="https://github.com/user-attachments/assets/dd901b92-921a-4898-a8f5-dd120af84c28" />

---

## 🧾 Fontes de dados recomendadas
- **FRED (Federal Reserve)** — séries de Fed Funds e M2.  
- **BLS (Bureau of Labor Statistics)** — CPI (inflação).  
- Relatórios e comunicados do **Federal Reserve** e publicações econômicas.

---

## 🧑‍💻 Reproduzir / Contribuir
Posso ajudar com:
- Gerar os CSVs atualizados a partir das fontes (script Python).  
- Ajustar o `.pbix` para ingestão automática dos arquivos.  
- Criar script de atualização (Python + Power BI REST / agendamento).

Diga qual opção prefere e eu preparo os arquivos/roteiro.

---
<h2>📄 Licença</h2>
<p>Este projeto está licenciado sob a <a href="LICENSE">MIT License</a>.</p>
    
<h2>🤝 Contribuição</h2>

<p>Fique à vontade para abrir issues e enviar pull requests para melhorias no projeto!</p>
    
<h2>📞 Contato</h2>
<p>Caso tenha dúvidas ou sugestões, entre em contato:</p>
<ul>
    <li>📧 Email: <a href="mailto:santossilvahenrygabriel58@gmail.com">Meu email de contato</a></li>
    <li>🔗 LinkedIn: <a href="www.linkedin.com/in/henry-gabriel-santos-silva-6ba776209">Meu Perfil linkedin</a></li>
</ul>
    
<hr>
    
<p>⭐ Se gostou do projeto, deixe um star no repositório!</p>
