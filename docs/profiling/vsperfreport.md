---
title: VSPerfReport | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1e20b019e4d32aff1ed71d3e4483a1bd9bd143
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581275"
---
# <a name="vsperfreport"></a>VSPerfReport
Umożliwia tworzenie raportów przy użyciu narzędzia wiersza polecenia VSPerfReport [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools pliku danych profilowania. Domyślny format raportu. *csv* pliku.

 VSPerfReport używa następującej składni:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Należy pamiętać, że `filename` musi być prawidłowym. *Vsp* lub. *vsps* pliku.

 Vsperfreport — narzędzie wiersza polecenia jest również używana do porównania. *vsp* lub. *vsps* plików. Aby wygenerować raport różnica ("diff"), użyj następującej składni:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` musi być prawidłowy. *vsp* lub. *vsps* plików.

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
|**PackSymbols**|Zapisuje symboli do pliku danych (Vsp) profilowania więc symbolu (. *plik PDB*) plików nie są wymagane do analizy.|
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
|**Diff**  `vspfile1 vspfile2`|Porównaj dwa pliki raportów (. *Vsp* lub. *vsps*) plików. Opcje podsumowania zostaną zignorowane przy użyciu opcji różnic.|
|**Diff:**[*wartość*]|Poniżej tej wartości progowe różnicę między dwiema wartościami zostaną zignorowane. Ponadto nowe dane o wartościach poniżej tego progu nie będą wyświetlane.|
|**DiffTable:**[*tablename*]|Użyj tej konkretnej tabeli do porównywania plików. Wartość domyślna to tabeli funkcji.|
|**DiffColumn:**[*columnname*]|Użyj tej wartości porównania określonej kolumny. Wartość domyślna to kolumna procentu próbki wyłączne.|
|**QueryDiffTables**|Listę prawidłowych tabel i kolumn dla tych dwóch plików raportu, pod warunkiem.|

## <a name="see-also"></a>Zobacz także
- [Widoki raportu wydajności](../profiling/performance-report-views.md)