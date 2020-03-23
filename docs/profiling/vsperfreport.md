---
title: VSPerfReport | Dokumenty firmy Microsoft
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 282bb801625429d639e625a0a5edb02a8fb4da25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777988"
---
# <a name="vsperfreport"></a>VSPerfReport
Narzędzie wiersza polecenia VSPerfReport służy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do tworzenia raportów przy użyciu plików danych profilowania narzędzi profilowania. Domyślnym formatem raportu jest plik . pliku *csv.*

 VsPerfReport używa następującej składni:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Należy `filename` pamiętać, że musi być prawidłowy . *vsp* lub . *vsps.*

 Narzędzie wiersza polecenia VSPerfReport służy również do porównywania . *vsp* lub . *vsps* plików. Aby wygenerować raport różnicy ("diff"), należy użyć następującej składni:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2`muszą być ważne . *vsp* lub . *vsps* plików.

## <a name="symbol-files"></a>Pliki symboli
 Aby wyświetlić informacje o symbolu, takie jak nazwy funkcji i numery wierszy, vsPerfReport wymaga dostępu do symbolu (. PDB) profilowanych komponentów i plików symboli systemu Windows. Aby uzyskać więcej informacji, zobacz [Jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Opcje raportu ogólnego
 W poniższej tabeli opisano opcje formatowania raportu ogólnego i opcje, które wybierają dane, które mają być zgłaszane.

|Opcje|Opis|
|-------------|-----------------|
|**U**|Dane wyjściowe raportu i przekierowane dane wyjściowe konsoli są zapisywane jako Unicode. Musi być pierwszą określoną opcją.|
|**Krótki opis:**[*typy*]|Tworzy jeden lub więcej typów raportów.<br /><br /> -   `All`- generowane są wszystkie typy raportów.<br />-   `CallerCallee`- relacje nadrzędne i podrzędne między funkcjami.<br />-   `Function`- funkcje wywoływane.<br />-   `CallTree`- hierarchia funkcji tzw.<br />-   `Counter`- wszystkie znaczniki wraz z wartościami licznika wydajności systemu Windows.<br />-   `Ip`- instrukcje profilowane.<br />-   `Life`- okres istnienia przydzielonych obiektów (dostępne po zebraniu danych alokacji).<br />-   `Line`danych profilu linii kodu źródłowego.<br />-   `Header`- raport zawiera informacje nagłówka plików.<br />-   `Mark`wszystkich znaków.<br />-   `Module`- moduły profilowane.<br />-   `Process`- procesy profilowane.<br />-   `Thread`- wątki profilowane.<br />-   `Type`- przydzielone typy.<br />-   `Contention`- rywalizacja o zasoby.<br />-   `RuleWarnings`- problemy z regułami wydajności<br />-   `ETW`- wszystkie zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) zebrane w przebiegu profilowania. Plik danych .etl musi znajdować się w oryginalnej lokalizacji lub w katalogu zawierającym plik vsp lub .vsps.|
|**Xml**|Raport wyjściowy w formacie XML.|
|**Calltrace**|Tworzy listę wpisów i wyjść funkcji, zdarzeń ETW i znaczników.|
|**ClearPackedSymbols**|Usuwa uprzednio osadzone symbole z pliku danych profilera. Uruchom to polecenie przed uruchomieniem PackSymbols po raz drugi.|
|**Ścieżka symboli:**`path`|Określa jedną lub więcej ścieżek wyszukiwania lub serwerów symboli zawierających symbole pliku danych profilera.|
|**Ścieżka debugowania**|Wyświetla listę lokalizacji, które są wyszukiwane symbole i czy są one znalezione. Ta opcja jest przydatna do rozwiązywania problemów z rozpoznawaniem symboli.|
|**PakietySymbole**|Zapisuje symbole w pliku danych profilowania (vsp), aby symbol (.* pdb*) pliki nie są wymagane do analizy.|
|**Dane wyjściowe:** *ścieżka*&#124;*nazwa pliku*|Określa alternatywną lokalizację dla wygenerowanych plików raportu. Domyślnie raporty są tworzone w bieżącym katalogu.|
|**Podsumowanie Plik**|Analizowanie i zapisywanie analizowanych informacji w pliku podsumowania vsps.|
|**Znaki druku**|Pokaż nazwy i sygnatury czasowe dla wszystkich znaczników w określonym pliku raportu.|
|**?**|Wyświetla informacje o użytkowaniu.|
|**NoLogo ( NoLogo )**|Ukrywa informacje o wersji, gdy raport jest uruchomiony.|
|**UserRulesDirectory**|Określa katalog zawierający reguły wydajności zdefiniowane przez użytkownika [Jeszcze nie zaimplementowane].|

## <a name="filter-options"></a>Opcje filtru
 W poniższej tabeli opisano opcje filtrowania dostępnych danych.

|Opcje|Opis|
|-------------|-----------------|
|**JustMyCode****:**[`caller`: [`callee`][, ]]|Pokaż tylko wywołania funkcji aplikacji użytkownika; ukryć wywołania systemowe.<br /><br /> - Brak parametrów - ukryj wszystkie funkcje systemowe.<br />-   `caller`- pokaż jeden poziom funkcji systemowych, które wywołują funkcje aplikacji.<br />-   `callee`- pokaż jeden poziom funkcji systemowych, które są wywoływane przez funkcje aplikacji użytkownika.|
|**Czas rozpoczęcia:**[*wartość*]|Pokaż tylko dane zebrane po wartości (w milisekundach).|
|**Czas zakończenia:**[*wartość*]|Pokaż tylko dane zebrane przed wartością (w milisekundach).|
|**Plik filtra:**`VSPFFile`|Określa lokalizację pliku filtru wygenerowanego z okna Raport wydajności programu Visual Studio.|
|**MsFilter:**[*czas rozpoczęcia, czas trwania*]|Dane są `starttime` wyświetlane tylko `duration` od momentu (w milisekundach).|
|**Proces:**[*pid*]|Pokaż tylko dane z określonego procesu.|
|**Wątek:**[*threadid*]|Pokaż tylko dane z określonego wątku.|
|**Wątek:**[*threadid,processid*]|Pokaż tylko dane z określonego wątku skojarzonego z określonym procesem.|

## <a name="difference-report-options"></a>Opcje raportu różnicy
 W poniższej tabeli opisano opcje porównywania plików raportów.

|Opcje|Opis|
|-------------|-----------------|
|**Różn**  `vspfile1 vspfile2`|Porównaj dwa pliki raportu (.* vsp* lub . *vsps*) Pliki. Opcje podsumowania zostaną zignorowane przy użyciu opcji różnicowej.|
|**Diff:**[*wartość*]|Poniżej tej wartości progowej różnica między dwiema wartościami nie zostanie uwzględniona. Ponadto nowe dane z wartościami poniżej tego progu nie będą wyświetlane.|
|**Tabela różnicowa:**[*nazwa tabeli*]|Ta określona tabela służy do porównywania plików. Wartością domyślną jest tabela funkcji.|
|**DiffColumn:**[*nazwa kolumny*]|Użyj tej określonej kolumny porównać wartości. Wartość domyślna to kolumna procentu próbek wyłącznych.|
|**QueryDiffTables (Tabele rozproszone w kwerendzie)**|Wyświetl prawidłowe tabele i kolumny dla dwóch dostarczonych plików raportu.|

## <a name="see-also"></a>Zobacz też
- [Widoki raportu o skuteczności](../profiling/performance-report-views.md)
