---
title: Funkcje interfejsu API wtyczki kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699920"
---
# <a name="source-control-plug-in-api-functions"></a>Funkcje interfejsu API wtyczki kontroli źródła
Interfejs API wtyczki kontroli źródła udostępnia następujące funkcje, które muszą zostać zaimplementowane przez wtyczkę kontroli źródła zgodnie z tym interfejsem API. Sygnatury każdej funkcji i semantyki skojarzonej z flagami bitowymi i innymi parametrami są szczegółowo opisane w tym odwołaniu.

## <a name="initialization-and-housekeeping-functions"></a>Funkcje inicjacji i dla gospodarstw domowych

|Funkcja|Opis|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zamyka projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Monituje użytkownika o opcje zaawansowane dla danego polecenia.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Zwraca wersję wtyczki kontroli źródła.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicjuje wtyczkę kontroli źródła. Jest wywoływana jednokrotnie dla każdego wystąpienia wtyczki.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otwiera projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funkcja ogólna używana do ustawiania szerokiej gamy opcji. Każda opcja rozpoczyna się od `SCC_OPT_xxx` i ma swój własny zdefiniowany zestaw wartości.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wywoływana raz, gdy wtyczka kontroli źródła musi być odłączona.|

## <a name="core-source-control-functions"></a>Podstawowe funkcje kontroli źródła

|Funkcja|Opis|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Dodaje tablicę plików określoną za pomocą w pełni kwalifikowanych nazw ścieżek do systemu kontroli źródła.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła, a następnie stanowią część tego pliku w bieżącym projekcie.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Sprawdza tablicę plików.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Sprawdza tablicę plików.|
|[SccDiff](../extensibility/sccdiff-function.md)|Pokazuje różnice między plikiem użytkownika lokalnego określonym za pomocą w pełni kwalifikowanej nazwy ścieżki i wersji pod kontrolą źródła.|
|[SccGet](../extensibility/sccget-function.md)|Pobiera kopię zestawu plików tylko do odczytu.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Sprawdza stan plików, na które prosi obiekt wywołujący (za pośrednictwem `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Powoduje, że wtyczka do kontroli źródła monituje użytkownika o ścieżkę projektu, która ma znaczenie dla wtyczki.|
|[SccHistory](../extensibility/scchistory-function.md)|Pokazuje historię tablicy w pełni kwalifikowanych lokalnych nazw plików.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Bada listę plików do ich bieżącego stanu. Ponadto program używa `pfnPopulate` funkcji do powiadamiania wywołującego, gdy plik jest niezgodny z kryteriami dla `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Pokazuje właściwości w w pełni kwalifikowany plik.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Bada listę w pełni kwalifikowanych plików dla ich bieżącego stanu.|
|[SccRemove](../extensibility/sccremove-function.md)|Usuwa tablicę w pełni kwalifikowanych plików z systemu kontroli źródła.|
|[SccRename](../extensibility/sccrename-function.md)|Zmienia nazwę danego pliku na nową nazwę w systemie kontroli źródła.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Uzyskuje dostęp do pełnego zakresu funkcji systemu kontroli źródła.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Cofa wyewidencjonowanie tablicy plików.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują dodatkową możliwość (wersja 1,2 interfejsu API wtyczki kontroli źródła)
 Ta grupa funkcji definiuje dodatkowe funkcje dostępne w wersji 1,2 interfejsu API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji i możliwości kontroli źródła.

|Funkcja|Opis|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Uruchamia operację wsadową.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Tworzy podprojekt o podaną nazwę w istniejącym projekcie nadrzędnym.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Pokazuje różnice między katalogiem użytkownika lokalnego określonym przy użyciu w pełni kwalifikowanej nazwy ścieżki i lokalizacji bazy danych kontroli źródła.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Bada listę w pełni kwalifikowanych katalogów dla ich bieżącego stanu.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Zamyka operację wsadową.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Zwraca ścieżkę nadrzędną danego projektu (projekt musi istnieć).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Sprawdza, czy jest dozwolone wielokrotne wyewidencjonowanie pliku.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Sprawdza, czy wtyczka utworzy MSSCCPRJ. Pliki SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują funkcję zaawansowaną (wersja 1,3 interfejsu API wtyczki kontroli źródła)
 Ta grupa funkcji definiuje dodatkowe funkcje dostępne w wersji 1,3 interfejsu API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji i możliwości kontroli źródła.

|Funkcja|Opis|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dodaje listę plików z kontroli źródła do bieżącego projektu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Pobiera listę plików z kontroli źródła bez interfejsu użytkownika.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Pobiera listę plików w kontroli źródła, które różnią się od plików lokalnych.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Pobiera flagi określające rozszerzone możliwości obsługiwane przez wtyczkę kontroli źródła.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Pobiera opcje specyficzne dla użytkownika.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Bada listę katalogów i plików w projekcie lub projektach, które znajdują się pod kontrolą źródła. Każdy znaleziony katalog i nazwa pliku są przesyłane do funkcji wywołania zwrotnego.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Bada zmiany nazw wprowadzone do listy plików. Każda nazwa pliku jest przenoszona do funkcji wywołania zwrotnego ze stanem zmiany.|

## <a name="requirements"></a>Wymagania
 Nagłówek: SCC. h

 (Dostarczane w folderze typowego zestawu SDK środowiska, domyślnie *[dysk]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc;, także dostarczone w folderze VSIP z przykładem MSSCCI *[dysk]* \Program Files\VSIP 8.0 \ MSSCCI).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)
