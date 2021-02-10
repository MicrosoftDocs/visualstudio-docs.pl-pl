---
title: Widok procesu — dane rywalizacji | Microsoft Docs
description: Dowiedz się, w jaki sposób widok procesu wyświetla dane rywalizacji dotyczące procesów i wątków, które zostały wykonane podczas przebiegu profilowania.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 60f137c470b31ddccfa9b26cb907b13288d07dc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957312"
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
|**ID (Identyfikator)**|Wygenerowany przez system identyfikator procesu lub wątku.|
|**Czas życia**|Liczba milisekund lub cykli procesora od początku procesu lub wątku do końca procesu lub wątku albo końca profilowania.|
|**Typ**|Typ wiersza, proces lub wątek.<br /><br /> Tylko w raportach wiersza polecenia **VSReport** . Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|
|**Nazwa**|Nazwa procesu lub wątku.|
|**Unikatowy identyfikator**|Wygenerowany przez profiler identyfikator, który jest unikatowy dla procesu lub wątku.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok procesu](../profiling/process-view.md)
