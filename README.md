# 📊 Painel: Indicadores Macroeconômicos dos EUA (Inflação, Juros e M2) — 2025

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

## 🗂 Estrutura sugerida do repositório
```
/data
  ├─ m2_monthly.csv
  ├─ cpi_monthly.csv
  └─ fed_funds_rate.csv
/reports
  └─ painel_powerbi.pbix
/visuals
  └─ screenshots/
/docs
  └─ README_data_sources.md
README.md
```

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

## 🧮 Medidas DAX úteis (exemplos)
```DAX
Inflação_12m = 
CALCULATE(
  DIVIDE(
    MAX(CPI[Valor]) - CALCULATE(MAX(CPI[Valor]), DATEADD(CPI[Data], -12, MONTH)),
    CALCULATE(MAX(CPI[Valor]), DATEADD(CPI[Data], -12, MONTH))
  ),
  ALLSELECTED()
)

M2_trilhoes = SUM(M2[Valor]) / 1000000000000
```
> Ajuste nomes de tabelas e colunas conforme seu modelo.

---

## 🧾 Fontes de dados recomendadas
- **FRED (Federal Reserve)** — séries de Fed Funds e M2.  
- **BLS (Bureau of Labor Statistics)** — CPI (inflação).  
- Relatórios e comunicados do **Federal Reserve** e publicações econômicas.

---

## ✅ Boas práticas
- Versionar CSVs com data no nome (ex.: `m2_monthly_2025-08.csv`) para auditoria.  
- Documentar transformações em `NOTAS.md` (ex.: ajustes sazonais, conversões de unidade).  
- Automatizar ETL com scripts Python se precisar de atualizações frequentes.

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
