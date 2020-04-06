---
title: Funkcje interfejsu API wtyczki kontroli źródła | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699920"
---
# <a name="source-control-plug-in-api-functions"></a>Funkcje interfejsu API wtyczki kontroli źródła
Interfejs API wtyczki kontroli źródła zawiera następujące funkcje, które muszą być zaimplementowane przez wtyczkę kontroli źródła zgodnie z tym interfejsem API. Podpisy każdej funkcji i semantyki skojarzone z flagami bitowymi i innymi parametrami są szczegółowo opisane w tym odwołaniu.

## <a name="initialization-and-housekeeping-functions"></a>Funkcje inicjowania i sprzątania

|Funkcja|Opis|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zamyka projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Monituje użytkownika o zaawansowane opcje dla danego polecenia.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Zwraca wersję wtyczki kontroli źródła.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicjuje wtyczkę kontroli źródła. Jest wywoływana raz dla każdego wystąpienia wtyczki.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otwiera projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funkcja ogólna używana do ustawiania szerokiej gamy opcji. Każda opcja rozpoczyna `SCC_OPT_xxx` się i ma swój własny zdefiniowany zestaw wartości.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wywoływana raz, gdy wtyczka kontroli źródła musi zostać odłączona.|

## <a name="core-source-control-functions"></a>Podstawowe funkcje sterowania źródłem

|Funkcja|Opis|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Dodaje tablicę plików określonych przez w pełni kwalifikowane nazwy ścieżek do systemu kontroli źródła.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umożliwia użytkownikowi przeglądanie plików, które są już w systemie kontroli źródła, a następnie uczynić te pliki częścią bieżącego projektu.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Sprawdza w tablicy plików.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Wyewidencjonowywki tablicy plików.|
|[SccDiff](../extensibility/sccdiff-function.md)|Pokazuje różnice między plikiem użytkownika lokalnego określonym przez w pełni kwalifikowaną nazwę ścieżki a wersją pod kontrolą źródła.|
|[SccGet](../extensibility/sccget-function.md)|Pobiera kopię zestawu plików tylko do odczytu.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Sprawdza stan plików, o które poprosił rozmówca (za pośrednictwem `SccQueryInfo`).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Powoduje, że wtyczka formantu źródła monituje użytkownika o ścieżkę projektu, która ma znaczenie dla wtyczki.|
|[SccHistory](../extensibility/scchistory-function.md)|Pokazuje historię tablicy w pełni kwalifikowanych nazw plików lokalnych.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Sprawdza listę plików pod kątem ich bieżącego stanu. Ponadto używa `pfnPopulate` tej funkcji do powiadamiania rozmówcy, gdy plik nie `nCommand`spełnia kryteriów programu .|
|[SccProperties](../extensibility/sccproperties-function.md)|Pokazuje właściwości w pełni kwalifikowanego pliku.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Sprawdza listę w pełni kwalifikowanych plików pod kątem ich bieżącego stanu.|
|[SccRemove](../extensibility/sccremove-function.md)|Usuwa tablicę w pełni kwalifikowanych plików z systemu kontroli źródła.|
|[SccRename](../extensibility/sccrename-function.md)|Zmienia nazwę danego pliku na nową nazwę w systemie kontroli źródła.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Uzyskuje dostęp do pełnego zakresu funkcji systemu kontroli źródła.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Cofa wyewidencjonowanie tablicy plików.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkcje obsługujące dodatkowe możliwości (wersja 1.2 interfejsu API wtyczki kontroli źródła)
 Ta grupa funkcji definiuje dodatkowe funkcje zawarte w wersji 1.2 interfejsu API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji kontroli źródła i możliwości.

|Funkcja|Opis|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Rozpoczyna operację wsadową.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Tworzy podprojekt o podanej nazwie w ramach istniejącego projektu nadrzędnego.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Pokazuje różnice między katalogiem użytkownika lokalnego określonym przez w pełni kwalifikowaną nazwę ścieżki a lokalizacją bazy danych kontroli źródła.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Sprawdza listę w pełni kwalifikowanych katalogów pod kątem ich bieżącego stanu.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Kończy operację wsadową.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Zwraca ścieżkę nadrzędną danego projektu (projekt musi istnieć).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Sprawdza, czy wiele wyewidencjonowania w pliku są dozwolone.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Sprawdza, czy wtyczka utworzy MSSCCPRJ. pliki SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkcje obsługujące zaawansowane możliwości (wersja 1.3 interfejsu API wtyczki kontroli źródła)
 Ta grupa funkcji definiuje dodatkowe funkcje zawarte w wersji 1.3 interfejsu API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji kontroli źródła i możliwości.

|Funkcja|Opis|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dodaje listę plików z kontroli źródła do bieżącego projektu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Pobiera listę plików z kontrolki źródła bez interfejsu użytkownika.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Pobiera listę plików w formancie źródłowym, które różnią się od plików lokalnych.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Pobiera flagi, które określają rozszerzone możliwości obsługiwane przez wtyczkę kontroli źródła.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Pobiera opcje specyficzne dla użytkownika.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Sprawdza listę katalogów i plików w projekcie lub projektach, które są pod kontrolą źródła. Każda znaleziona nazwa katalogu i pliku jest przekazywana do funkcji wywołania zwrotnego.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Sprawdza zmiany nazw wprowadzone na liście plików. Każda nazwa pliku jest przekazywana do funkcji wywołania zwrotnego ze stanem zmiany.|

## <a name="requirements"></a>Wymagania
 Nagłówek: scc.h

 (Dostarczany w zestawie SDK środowiska zawiera folder, domyślnie *[drive]* \Program Files\VSIP 8.0\EnvSDK\common\inc; również dostarczany w folderze VSIP z próbką MSSCCI, *[drive]* \Program Files\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)
