---
title: VSPerfReport | Microsoft Docs
description: Dowiedz się, że narzędzie wiersza polecenia VSPerfReport służy do tworzenia raportów przy użyciu plików danych profilowania programu Visual Studio narzędzia profilowania.
ms.date: 11/04/2016
ms.topic: reference
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ed3ba5453976e3f3976aba43bc296c040a86b7a5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719776"
---
# <a name="vsperfreport"></a>VSPerfReport
Narzędzie wiersza polecenia VSPerfReport służy do tworzenia raportów przy użyciu  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plików danych profilowania narzędzia profilowania. Domyślny format raportu to. plik *CSV* .

 VSPerfReport używa następującej składni:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Należy pamiętać, że `filename` musi być prawidłowy.*VSP* lub. plik *vsps* .

 Narzędzie wiersza polecenia VSPerfReport służy również do porównywania. *VSP* lub. pliki *vsps* . Aby wygenerować raport różnic ("diff"), użyj następującej składni:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` musi być prawidłowy. *VSP* lub. pliki *vsps* .

## <a name="symbol-files"></a>Pliki symboli
 Aby wyświetlić informacje o symbolach, takie jak nazwy funkcji i numery wierszy, VSPerfReport wymaga dostępu do symbolu (. PDB) pliki profilowanych składników i plików symboli systemu Windows. Aby uzyskać więcej informacji, zobacz [How to: Określanie lokalizacji plików symboli w wierszu polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Ogólne opcje raportu
 W poniższej tabeli opisano ogólne opcje formatowania raportu i opcje, które wybierają dane do zgłoszenia.

|Opcje|Opis|
|-------------|-----------------|
|**'T**|Dane wyjściowe raportu i przekierowane dane wyjściowe konsoli są zapisywane w formacie Unicode. Musi być pierwszą określoną opcją.|
|**Podsumowanie:**[*typy*]|Tworzy jeden lub więcej typów raportów.<br /><br /> -   `All` — generowane są wszystkie typy raportów.<br />-   `CallerCallee` -relacje nadrzędny/podrzędny między funkcjami.<br />-   `Function` -Functions o nazwie.<br />-   `CallTree` -Hierarchia funkcji o nazwie.<br />-   `Counter` — wszystkie znaczniki wraz z wartościami liczników wydajności systemu Windows.<br />-   `Ip` -instrukcje profilowane.<br />-   `Life` — okres istnienia przydzielonych obiektów (dostępny podczas zbierania danych alokacji).<br />-   `Line` dane profilu wiersza kodu źródłowego.<br />-   `Header` -Raport zawiera informacje nagłówka pliku.<br />-   `Mark` wszystkie znaczniki.<br />-   `Module` — profilowano moduły.<br />-   `Process` -przetwarza profilowane.<br />-   `Thread` -wątki profilowane.<br />-   `Type` -przydzielono typy.<br />-   `Contention` — rywalizacje o zasoby.<br />-   `RuleWarnings` -Problemy z regułą wydajności<br />-   `ETW` — wszystkie zdarzenia śledzenia zdarzeń systemu Windows (ETW) zebrane w przebiegu profilowania. Plik danych ETL musi znajdować się w jego oryginalnej lokalizacji lub w katalogu zawierającym plik VSP lub vsps.|
|**Dokument**|Raport wyjściowy w formacie XML.|
|**CallTrace**|Tworzy listę wpisów funkcji i wyjść, zdarzeń ETW i znaczników.|
|**ClearPackedSymbols**|Usuwa poprzednio osadzone symbole z pliku danych profilera. Uruchom to polecenie przed uruchomieniem PackSymbols po raz drugi.|
|**SymbolPath —:**`path`|Określa co najmniej jedną ścieżkę wyszukiwania lub serwery symboli, które zawierają symbole dla pliku danych profilera.|
|**DebugSymPath**|Wyświetla listę lokalizacji, w których są wyszukiwane symbole i czy zostały znalezione. Ta opcja jest przydatna do rozwiązywania problemów z rozpoznawaniem symboli.|
|**PackSymbols**|Zapisuje symbole w pliku danych profilowania (. vsp), tak aby symbol (.*PDB*) nie są wymagane do analizy.|
|**Dane wyjściowe:** *ścieżka*&#124;*filename*|Określa alternatywną lokalizację dla wygenerowanych plików raportu. Domyślnie raporty są tworzone w bieżącym katalogu.|
|**SummaryFile**|Analizuj i zapisuj przeanalizowane informacje w pliku podsumowania. vsps.|
|**PrintMarks**|Pokaż nazwy i sygnatury czasowe dla wszystkich znaczników w określonym pliku raportu.|
|**?**|Wyświetla informacje o użyciu.|
|**NoLogo**|Ukrywa informacje o wersji, gdy raport jest uruchomiony.|
|**UserRulesDirectory**|Określa katalog zawierający reguły wydajności zdefiniowane przez użytkownika [jeszcze nie zaimplementowane].|

## <a name="filter-options"></a>Opcje filtru
 W poniższej tabeli opisano opcje filtrowania dostępnych danych.

|Opcje|Opis|
|-------------|-----------------|
|**JustMyCode**[**:**[ `caller` ] [, `callee` ]]|Pokaż tylko wywołania funkcji aplikacji użytkownika; Ukryj wywołania systemowe.<br /><br /> -Brak parametrów-Ukryj wszystkie funkcje systemowe.<br />-   `caller` -Pokaż jeden poziom funkcji systemowych, które wywołują funkcje aplikacji.<br />-   `callee` -Pokaż jeden poziom funkcji systemowych, które są wywoływane przez funkcje aplikacji użytkownika.|
|**StartTime:**[*Value*]|Pokaż tylko dane zebrane po wartości (w milisekundach).|
|**Endtime:**[*wartość*]|Pokaż tylko dane zebrane przed wartością (w milisekundach).|
|**FilterFile:**`VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany z okna raportu wydajności programu Visual Studio.|
|**MsFilter:**[*StartTime, Duration*]|Pokaż tylko dane z `starttime` do długości `duration` (w milisekundach).|
|**Proces:**[*PID*]|Wyświetla tylko dane z określonego procesu.|
|**Wątek:**[*ThreadID*]|Wyświetla tylko dane z określonego wątku.|
|**Wątek:**[*ThreadID, identyfikator procesu*]|Pokaż tylko dane z określonego wątku skojarzone z określonym procesem.|

## <a name="difference-report-options"></a>Różnice — opcje raportu
 W poniższej tabeli opisano opcje porównywania plików raportów.

|Opcje|Opis|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|Porównaj dwa pliki raportu (.*VSP* lub. *vsps*) plikach. Opcje podsumowania zostaną zignorowane przy użyciu opcji diff.|
|**Diff:**[*wartość*]|Poniżej wartości progowej różnica między dwiema wartościami zostanie pominięta. Ponadto nowe dane o wartościach poniżej tego progu nie będą wyświetlane.|
|**Diffie:**[*TableName*]|Użyj tej konkretnej tabeli do porównywania plików. Wartość domyślna to tabela funkcji.|
|**DiffColumn:**[*ColumnName*]|Ta szczegółowa kolumna służy do porównywania wartości. Wartość domyślna to kolumna procent wyłącznych próbek.|
|**QueryDiffTables**|Wyświetl listę prawidłowych tabel i kolumn dla dwóch udostępnionych plików raportów.|

## <a name="see-also"></a>Zobacz także
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
