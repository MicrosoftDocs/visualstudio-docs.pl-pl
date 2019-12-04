---
title: Widok procesu — dane rywalizacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 30c938088538bcecc71e3a7e37d5ae403dd476e1
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778404"
---
# <a name="process-view---contention-data"></a>Widok procesu — dane rywalizacji
Widok procesu przedstawia dane rywalizacji dotyczące procesów i wątków, które zostały wykonane podczas przebiegu profilowania.

 Gdy symbole są dostępne, procesy są wyświetlane według nazwy. Gdy symbole nie są dostępne, procesy są wyświetlane według adresów pamięci w formacie szesnastkowym. Wątki są wyświetlane jako elementy podrzędne procesu, który go utworzył.

 W poniższej tabeli objaśniono wartości kolumn w tabeli widoku procesu.

|Kolumna|Opis|
|------------|-----------------|
|**Godzina rozpoczęcia**|Liczba milisekund lub cykli procesora od początku profilowania do początku procesu lub wątku.|
|**Czas blokowania**|Łączny czas, w którym funkcje procesu lub wątku zostały zablokowane do wykonania.|
|**% Czasu blokowania**|Wartość procentowa okresu istnienia procesu lub wątku, w którym zablokowano wykonywanie funkcji przez proces lub wątek.|
|**Rywalizacji**|Liczba operacji blokowania wykonywania funkcji przez proces lub wątek.|
|**Rywalizacji**|Wartość procentowa wszystkich rywalizacji w przebiegu profilowania, które były rywalizacjami o proces lub wątek.|
|**Czas zakończenia**|Liczba milisekund lub cykli procesora od początku profilowania do końca procesu lub wątku.|
|**#C1**|Wygenerowany przez system identyfikator procesu lub wątku.|
|**Czas życia**|Liczba milisekund lub cykli procesora od początku procesu lub wątku do końca procesu lub wątku albo końca profilowania.|
|**Wprowadź**|Typ wiersza, proces lub wątek.<br /><br /> Tylko w raportach wiersza polecenia **VSReport** . Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|
|**Nazwa**|Nazwa procesu lub wątku.|
|**Unikatowy identyfikator**|Wygenerowany przez profiler identyfikator, który jest unikatowy dla procesu lub wątku.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok procesu](../profiling/process-view.md)
