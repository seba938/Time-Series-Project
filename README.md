# Previsione delle vendite mensili di auto (1960–1968)

Progetto di analisi di serie storiche in **R**: studio delle vendite mensili di auto dal 1960 al 1968 e costruzione di un modello per prevedere le vendite dell'ultimo anno.

## Strumenti
R · forecast · tseries

## Passaggi
1. **Analisi esplorativa**: grafico della serie, decomposizione moltiplicativa, ACF e seasonal plot. La serie ha un trend crescente, una forte stagionalità annuale (picco a maggio, calo in estate) e una varianza che aumenta nel tempo
2. **Trasformazioni per rendere la serie stazionaria**: logaritmo, differenza prima e differenza stagionale (lag 12), verificate con il test ADF
3. **Scelta del modello**: confronto di tre modelli SARIMA tramite AIC, partendo dall'analisi di ACF e PACF. Il migliore è **SARIMA(0,1,1)(0,1,1)[12]**
4. **Gestione degli outlier**: individuato un valore anomalo a settembre 1962 e sostituito con la media dei mesi di settembre
5. **Previsione**: modello addestrato sul periodo 1960–1967 e testato sul 1968

## Risultati
- Dopo la gestione dell'outlier, i residui del modello si comportano come rumore bianco (test di Ljung-Box, p = 0,46)
- Errore medio di previsione sul 1968 di circa l'**8,6%** (MAE)
- **MASE = 0,72**: il modello fa circa il 28% meglio di una previsione naive
- Rimuovere l'outlier ha migliorato tutte le metriche (MASE da 0,80 a 0,72)

## Contenuto
- `report.pdf`: report completo con codice, grafici e commenti

## Fonte dei dati
[Monthly Car Sales – Kaggle](https://www.kaggle.com/datasets/rassiem/monthly-car-sales)
