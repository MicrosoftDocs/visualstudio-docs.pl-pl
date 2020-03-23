---
title: Widok procesu — dane rywalizacji | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778404"
---
# <a name="process-view---contention-data"></a>Widok procesu — dane rywalizacji
W widoku Proces są wyświetlane dane rywalizacji dla procesów i wątków, które zostały wykonane podczas przebiegu profilowania.

 Gdy symbole są dostępne, procesy są wyświetlane według nazwy. Gdy symbole nie są dostępne, procesy są wyświetlane według ich adresu pamięci w formacie szesnastkowym. Wątki są wyświetlane jako korle procesu, który je utworzył.

 W poniższej tabeli wyjaśniono wartości kolumn w tabeli Widok procesu.

|Kolumna|Opis|
|------------|-----------------|
|**Godzina rozpoczęcia**|Liczba milisekund lub cykli procesora od początku profilowania do początku procesu lub wątku.|
|**Zablokowany czas**|Całkowity czas, w którym funkcje procesu lub wątku zostały zablokowane przed wykonywaniem.|
|**Zablokowany czas %**|Procent okresu istnienia procesu lub wątku, w którym funkcje procesu lub wątku zostały zablokowane do wykonywania.|
|**Twierdzeniom**|Liczba zablokowanych funkcji procesu lub wątku.|
|**Rywalizacja %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były rywalizacji procesu lub wątku.|
|**Godzina zakończenia**|Liczba milisekund lub cykli procesora od początku profilowania do końca procesu lub wątku.|
|**ID**|Wygenerowany przez system identyfikator procesu lub wątku.|
|**Czas życia**|Liczba milisekund lub cykli procesora od początku procesu lub wątku do końca procesu lub wątku lub na końcu profilowania.|
|**Typ**|Typ wiersza, procesu lub wątku.<br /><br /> Tylko w raportach wiersza polecenia **VSReport.** Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|
|**Nazwa**|Nazwa procesu lub wątku.|
|**Unikatowy identyfikator**|Identyfikator generowany przez profiler, który jest unikatowy dla procesu lub wątku.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok procesu](../profiling/process-view.md)
