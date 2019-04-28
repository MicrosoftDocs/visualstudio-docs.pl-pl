---
title: Filtr widoku raportów wydajności | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4c5281386cb43d4dddb55db8578aea7515dce1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793984"
---
# <a name="performance-report-view-filter"></a>Filtr widoku raportów wydajności
**Filtr widoku raportów Profiler** okna znajduje się w górnej części **raport dotyczący wydajności** okna. Jeśli nie widzisz, kliknij pozycję **Pokaż filtr** przycisku.

 Można zmodyfikować każdej klauzuli filtru, aby zawęzić wyniki. Następujące kolumny są dostępne w Konstruktorze filtru.

|Element filtra|Opis|
|-----------------|-----------------|
|I/lub|Wybierz **i** Jeśli tę klauzulę i dalej klauzula musi mieć wartość true do Dopasuj wynik. Wybierz **lub** , jeśli ta klauzula lub klauzuli dalej może być wartość true, aby dopasować wynik.|
|Pole|Wybierz pole, aby użyć w klauzuli filtru z listy pola danych, które są dostępne w bieżącym pliku raportu.|
|Operator|Wybierz operator, który określa relację między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większa niż lub równe|
|Wartość|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|

 Możesz dodać klauzul filtru, dopóki nie poczujesz się, że filtr zapewni najlepsze rezultaty. Kliknij przycisk **wykonaj filtr** Aby zastosować filtr do pliku danych.

 Z **znaczniki** widoku raportu, można wygenerować klauzul filtru, aby ograniczyć ilość danych w widoku raportu, dane, które są zbierane pomiędzy dwoma znakami. Wybierz te znaczniki, które mają być początek i koniec raportu, dane, następnie kliknij prawym przyciskiem myszy i wybierz opcję **Dodaj filtr znaczników** lub **Dodaj filtr sygnatury czasowe**. Oba filtry ograniczają dane w bieżącym pliku danych do tego samego zakresu **Dodaj filtr znaczników** można stosować do innych plików Vsp.

 Aby zapisać filtr, kliknij przycisk **Eksportuj filtr** na **raport dotyczący wydajności** narzędzi a następnie określ lokalizację i nazwę pliku. *vspf* pliku. Aby załadować uprzednio zapisany filtr, kliknij przycisk **filtru importu** i zlokalizuj plik zapisany filtr. Filtr plików można również filtrować pliki danych na komputerach autonomicznych Profiling Tools zainstalowane. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Zobacz także
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)