---
title: Filtr widoku raportów wydajności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8620e5a372d764fef3a75126af52a6212ecc6cd8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774636"
---
# <a name="performance-report-view-filter"></a>Filtr widoku raportów wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Filtr widoku raportów Profiler okna znajduje się u góry okna Raport o wydajności. Jeśli nie widzisz, kliknij pozycję **Pokaż filtr** przycisku.  
  
 Można zmodyfikować każdej klauzuli filtru, aby zawęzić wyniki. Następujące kolumny są dostępne w Konstruktorze filtru.  
  
|Element filtra|Opis|  
|-----------------|-----------------|  
|I/lub|Wybierz **i** Jeśli tę klauzulę i dalej klauzula musi mieć wartość true do Dopasuj wynik. Wybierz **lub** , jeśli ta klauzula lub klauzuli dalej może być wartość true, aby dopasować wynik.|  
|Pole|Wybierz pole, aby użyć w klauzuli filtru z listy pola danych, które są dostępne w bieżącym pliku raportu.|  
|Operator|Wybierz operator, który określa relację między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większa niż lub równe|  
|Wartość|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|  
  
 Możesz dodać klauzul filtru, dopóki nie poczujesz się, że filtr zapewni najlepsze rezultaty. Kliknij przycisk **wykonaj filtr** Aby zastosować filtr do pliku danych.  
  
 Z **znaczniki** widoku raportu, można wygenerować klauzul filtru, aby ograniczyć ilość danych w widoku raportu, dane, które są zbierane pomiędzy dwoma znakami. Wybierz te znaczniki, które mają być początek i koniec raportu, dane, następnie kliknij prawym przyciskiem myszy i wybierz opcję **Dodaj filtr znaczników** lub **Dodaj filtr sygnatury czasowe**. Oba filtry ograniczają dane w bieżącym pliku danych do tego samego zakresu **Dodaj filtr znaczników** można stosować do innych plików Vsp.  
  
 Aby zapisać filtr, kliknij przycisk **Eksportuj filtr** na pasku narzędzi wydajności i określ lokalizację i nazwę pliku .vspf. Aby załadować uprzednio zapisany filtr, kliknij przycisk **filtru importu** i zlokalizuj plik zapisany filtr. Filtr plików można również filtrować pliki danych na komputerach autonomicznych Profiling Tools zainstalowane. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności danych dotyczących narzędzi](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
