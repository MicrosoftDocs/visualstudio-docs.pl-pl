---
title: Widok procesu — dane rywalizacji o zasoby | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79f9330733a0d32faeb9980813f170f52a6f7121
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643915"
---
# <a name="process-view---contention-data"></a>Widok procesu — dane rywalizacji
Widok procesu przedstawia dane rywalizacji o zasoby dotyczące procesów i wątków, które zostały wykonane podczas uruchomienia profilowania.

 Po symbole są dostępne, procesy są wyświetlane według nazwy. Gdy symbole nie są dostępne, procesy są wyświetlane według ich adres pamięci, w formacie szesnastkowym. Wątki są wyświetlane jako elementy podrzędne procesu, który je utworzył.

 W poniższej tabeli przedstawiono wartości kolumn w tabeli widoku proces.

|Kolumna|Opis|
|------------|-----------------|
|**Czas rozpoczęcia**|Liczba milisekund, czyli cykli procesora od rozpoczęcia profilowania do początku proces lub wątek.|
|**Czas blokowania**|Całkowity czas, w którym funkcje proces lub wątek został zablokowany wykonywania.|
|**% Czasu blokowania**|Wartość procentowa okresu istnienia proces lub wątek, w którym funkcje proces lub wątek został zablokowany wykonywania.|
|**Rywalizacje**|Liczba prób wykonania funkcji proces lub wątek został zablokowany.|
|**% Rywalizacji**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji procesów lub wątków.|
|**Godzina zakończenia**|Liczba milisekund, czyli cykli procesora od czasu rozpoczęcia profilowania do końca proces lub wątek.|
|**Identyfikator**|Wygenerowana przez system identyfikator proces lub wątek.|
|**Okres istnienia**|Liczba milisekund, czyli cykli procesora od początku proces lub wątek do końca proces lub wątek lub końca okresu profilowania.|
|**Typ**|Typ wiersza, przetwarzania lub wątku.<br /><br /> Tylko w **VSReport** raporty wiersza polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|
|**Nazwa**|Nazwa proces lub wątek.|
|**Unikatowy identyfikator**|Identyfikator wygenerowany przez program profilujący jest unikatowy dla proces lub wątek.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok procesu](../profiling/process-view.md)