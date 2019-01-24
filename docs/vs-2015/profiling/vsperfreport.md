---
title: VSPerfReport | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7667aac348a6f7b208786191c35afe86542862d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788884"
---
# <a name="vsperfreport"></a>VSPerfReport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umożliwia tworzenie raportów przy użyciu narzędzia wiersza polecenia VSPerfReport [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools pliku danych profilowania. Domyślny format raportu jest plikiem CSV.  
  
 VSPerfReport używa następującej składni:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Należy pamiętać, że `filename` musi być prawidłowym plikiem .vsp lub .vsps.  
  
 Vsperfreport — narzędzie wiersza polecenia jest również używany do porównywania plików .vsp lub .vsps. Aby wygenerować raport różnica ("diff"), użyj następującej składni:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` musi być prawidłowe pliki .vsp lub .vsps.  
  
## <a name="symbol-files"></a>Pliki symboli  
 Aby wyświetlić informacje o symbolach, takich jak nazwy i numery wierszy, VSPerfReport wymaga dostępu do symbolu (. Pliki PDB) profilowanych składników i pliki symboli Windows. Aby uzyskać więcej informacji, zobacz [jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Opcje ogólne raportu  
 W poniższej tabeli opisano ogólne raportu, formatowanie i opcje, które wybrać dane do przekazania.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**U**|Dane wyjściowe raportu i konsoli przekierowane dane wyjściowe są zapisywane jako Unicode. Musi być pierwsza opcja określona.|  
|**Podsumowanie:**[*typy*]|Tworzy jeden lub więcej typów raportów.<br /><br /> -   `All` — wszystkie typy raportów są generowane.<br />-   `CallerCallee` -relacje nadrzędne/podrzędne między funkcjami.<br />-   `Function` — funkcje wywoływane.<br />-   `CallTree` -hierarchię wywołanych funkcji.<br />-   `Counter` — wszystkie znaczniki wraz z wydajności Windows wartości liczników.<br />-   `Ip` — instrukcje profilowania.<br />-   `Life` -okresów istnienia przydzielonych obiektów (dostępne, gdy zostały zebrane dane alokacji).<br />-   `Line` źródła danych profilu wiersza kodu.<br />-   `Header` -Raport zawiera informacje o pliku nagłówka.<br />-   `Mark` wszystkie znaczniki.<br />-   `Module` -Moduły profilowania.<br />-   `Process` -profilowanych procesów.<br />-   `Thread` -profilowanych wątków.<br />-   `Type` -przydzielonych typów.<br />-   `Contention` -rywalizacje o zasoby.<br />-   `RuleWarnings` -problemy z wydajnością reguły<br />-   `ETW` — wszystkie zdarzenia śledzenie zdarzeń dla Windows (ETW) zebranych podczas uruchomienia profilowania. Plik etl danych musi być w jej oryginalnej lokalizacji lub do katalogu zawierającego plik .vsp lub .vsps.|  
|**Xml**|Dane wyjściowe raportu w formacie XML.|  
|**CallTrace**|Tworzy listę wejście funkcji i wyjścia, zdarzenia ETW i znaczników.|  
|**ClearPackedSymbols**|Usuwa wcześniej osadzone symbole z pliku danych profilera. Uruchom następujące polecenie przed uruchomieniem PackSymbols na sekundę czasu.|  
|**SymbolPath:** `path`|Określa jedną lub więcej ścieżek wyszukiwania lub serwerów symboli, które zawierają symbole dla pliku danych profilera.|  
|**DebugSymPath**|Wyświetla listę lokalizacji, które są przeszukiwane pod kątem symboli i tego, czy zostaną znalezione. Ta opcja jest przydatna rozwiązać problemy z rozpoznawaniem symboli.|  
|**PackSymbols**|Zapisuje symboli w pliku danych (Vsp) profilowania, tak, aby pliki symboli (.pdb) nie są wymagane do analizy.|  
|**Dane wyjściowe:** *ścieżki*&#124;*nazwy pliku*|Określa alternatywną lokalizację plików wygenerowany raport. Domyślnie raporty są tworzone w bieżącym katalogu.|  
|**SummaryFile**|Analizuj i zapisuje przeanalizowane informacje w pliku podsumowania vsps.|  
|**PrintMarks**|Wyświetla nazwy i sygnatury czasowe dla wszystkich znaków w pliku określonego raportu.|  
|**?**|Wyświetla informacje o użyciu.|  
|**NoLogo**|Ukrywa informacje o wersji, gdy raport jest uruchomiony.|  
|**UserRulesDirectory**|Określa katalog zawierający reguły wydajności zdefiniowanej przez użytkownika [nie została jeszcze zaimplementowana].|  
  
## <a name="filter-options"></a>Opcje filtru  
 W poniższej tabeli opisano opcje filtrowania dostępnych danych.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`][,`callee`]]|Pokaż tylko użytkowników wywołań funkcji aplikacji; Ukryj wywołań systemowych.<br /><br /> -Brak parametrów - ukryć wszystkie funkcje system.<br />-   `caller` — Pokaż jeden poziom funkcji systemu, które wywołują funkcje aplikacji.<br />-   `callee` — Pokaż jeden poziom funkcji systemu, które są wywoływane przez funkcje aplikacji użytkownika.|  
|**Godzina rozpoczęcia:**[*wartość*]|Wyświetla tylko dane zebrane po wartości (w milisekundach).|  
|**EndTime:**[*wartość*]|Wyświetla tylko dane zebrane przed wartością (w milisekundach).|  
|**FilterFile:** `VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z okna Raport dotyczący wydajności programu Visual Studio.|  
|**MsFilter:**[*godzina rozpoczęcia, czas trwania*]|Wyświetla tylko dane z `starttime` aż do długości `duration` (w milisekundach).|  
|**Proces:**[*pid*]|Wyświetla tylko dane z określonego procesu.|  
|**Wątek:**[*threadid*]|Wyświetla tylko dane z określonego wątku.|  
|**Wątek:**[*identyfikator_wątku, identyfikator_procesu*]|Wyświetla tylko dane z określonego wątku skojarzone z określonym procesem.|  
  
## <a name="difference-report-options"></a>Opcje raportu różnicy  
 W poniższej tabeli opisano opcje porównywania plików raportu.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**Diff**  `vspfile1 vspfile2`|Porównaj dwa pliki (.vsp lub .vsps) pliki raportu. Opcje podsumowania zostaną zignorowane przy użyciu opcji różnic.|  
|**Diff:**[*wartość*]|Poniżej tej wartości progowe różnicę między dwiema wartościami zostaną zignorowane. Ponadto nowe dane o wartościach poniżej tego progu nie będą wyświetlane.|  
|**DiffTable:**[*tablename*]|Użyj tej konkretnej tabeli do porównywania plików. Wartość domyślna to tabeli funkcji.|  
|**DiffColumn:**[*columnname*]|Użyj tej wartości porównania określonej kolumny. Wartość domyślna to kolumna procentu próbki wyłączne.|  
|**QueryDiffTables**|Listę prawidłowych tabel i kolumn dla tych dwóch plików raportu, pod warunkiem.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
