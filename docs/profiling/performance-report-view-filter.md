---
title: Filtr widoku raportu wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a5642a8e153a4dfc7705d91d933397b6f8acb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778457"
---
# <a name="performance-report-view-filter"></a>Filtr widoku raportów wydajności
Okno **Filtr widoku raportu profilera** znajduje się w górnej części okna Raport **wydajności.** Jeśli nie widzisz go, kliknij przycisk **Pokaż filtr.**

 Można zmodyfikować każdą klauzulę filtru, aby zawęzić wyniki. Następujące kolumny są dostępne w konstruktorze filtrów.

|Element filtru|Opis|
|-----------------|-----------------|
|Lub|Wybierz **i** jeśli ta klauzula i następna klauzula musi być true, aby dopasować wynik. Wybierz **lub** jeśli ta klauzula lub następna klauzula może być spełniony, aby dopasować wynik.|
|Pole|Wybierz pole, które ma być używane w klauzuli filtru, z listy pól danych dostępnych w bieżącym pliku raportu.|
|Operator|Wybierz operatora, który określa odpowiednią relację między polem a wartością.<br /><br /> = Równa się<br /><br /> <>  nie równa się<br /><br /> < mniej niż<br /><br /> > większa niż<br /><br /> <= Mniej niż lub Równo<br /><br /> >= większa lub równa|
|Wartość|Wybierz lub wprowadź wartość, która ma być wyszukane. Niektóre pola wyświetlają listę dostępnych wartości pola.|

 Możesz dodawać klauzule filtru, dopóki nie poczujesz, że filtr da Ci najlepsze wyniki. Kliknij **przycisk Uruchom filtr,** aby zastosować filtr do pliku danych.

 W widoku raport **Znaczniki** można wygenerować klauzule filtrowania, aby ograniczyć dane w widokach raportu do danych zebranych między dwoma znakami. Zaznacz znaczniki, które chcesz uruchomić i zakończyć dane raportu, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj filtr na znacznikach** lub **Dodaj filtr w znacznikach czasu**. Oba filtry ograniczają dane w bieżącym pliku danych do tego samego zakresu; **Dodaj filtr na znacznikach** można zastosować do innych plików vsp.

 Aby zapisać filtr, kliknij pozycję **Eksportuj filtr** na pasku narzędzi **Raport wydajności,** a następnie określ lokalizację i nazwę pliku . *vspf.* Aby załadować wcześniej zapisany filtr, kliknij pozycję **Importuj filtr** i znajdź zapisany plik filtru. Pliki filtrów mogą być również używane do filtrowania plików danych na komputerach z zainstalowanymi autonomicznymi narzędziami profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Zobacz też
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
