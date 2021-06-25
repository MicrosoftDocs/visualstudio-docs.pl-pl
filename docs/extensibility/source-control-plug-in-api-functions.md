---
title: Funkcje interfejsu API wtyczki kontroli kodu źródłowego | Microsoft Docs
description: Dowiedz się więcej o funkcjach zapewnianych przez interfejs API wtyczki kontroli kodu źródłowego, które muszą być implementowane przez wtyczkę kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f93ddff78aa151218d0b46d017e4631d9489e44
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899605"
---
# <a name="source-control-plug-in-api-functions"></a>Funkcje interfejsu API wtyczki kontroli źródła
Interfejs API wtyczki kontroli kodu źródłowego udostępnia następujące funkcje, które muszą być implementowane przez wtyczkę kontroli źródła zgodnie z tym interfejsem API. Podpisy poszczególnych funkcji oraz semantyka skojarzona z flagami bitów i innymi parametrami zostały szczegółowo opisane w tym odwołaeniu.

## <a name="initialization-and-housekeeping-functions"></a>Inicjowanie i utrzymanie funkcji

|Funkcja|Opis|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zamyka projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Monituje użytkownika o opcje zaawansowane dla danego polecenia.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Zwraca wersję wtyczki kontroli źródła.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicjuje wtyczkę kontroli źródła. Jest ona wywoływana raz dla każdego wystąpienia wtyczki.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otwiera projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funkcja ogólna używana do ustawienia szerokiej gamy opcji. Każda opcja rozpoczyna się `SCC_OPT_xxx` od i ma własny zdefiniowany zestaw wartości.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wywoływana raz, gdy wtyczka kontroli źródła musi zostać odpięta.|

## <a name="core-source-control-functions"></a>Podstawowe funkcje kontroli źródła

|Funkcja|Opis|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Dodaje tablicę plików określoną przez w pełni kwalifikowane nazwy ścieżek do systemu kontroli źródła.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umożliwia użytkownikowi przeglądanie plików, które znajdują się już w systemie kontroli źródła, a następnie uczynić te pliki częścią bieżącego projektu.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Sprawdza tablicę plików.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Sprawdza tablicę plików.|
|[SccDiff](../extensibility/sccdiff-function.md)|Przedstawia różnice między plikiem użytkownika lokalnego określonym przez w pełni kwalifikowaną nazwę ścieżki i wersję pod kontrolą źródła.|
|[SccGet](../extensibility/sccget-function.md)|Pobiera kopię tylko do odczytu zestawu plików.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Sprawdza stan plików, o które pytał wywołujący (za pośrednictwem `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Powoduje, że wtyczka kontroli źródła monituje użytkownika o ścieżkę projektu zrozumiałą dla wtyczki.|
|[SccHistory](../extensibility/scchistory-function.md)|Przedstawia historię tablicy w pełni kwalifikowanych nazw plików lokalnych.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Sprawdza listę plików dla ich bieżącego stanu. Ponadto funkcja używa funkcji do powiadamiania wywołującego, gdy plik nie spełnia `pfnPopulate` kryteriów `nCommand` dla .|
|[SccProperties](../extensibility/sccproperties-function.md)|Wyświetla właściwości w pełni kwalifikowanego pliku.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Sprawdza listę w pełni kwalifikowanych plików dla ich bieżącego stanu.|
|[SccRemove](../extensibility/sccremove-function.md)|Usuwa tablicę w pełni kwalifikowanych plików z systemu kontroli źródła.|
|[SccRename](../extensibility/sccrename-function.md)|Zmienia nazwę danego pliku na nową nazwę w systemie kontroli źródła.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Uzyskuje dostęp do pełnego zakresu funkcji systemu kontroli źródła.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Cofa wyewidencjonowanie tablicy plików.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują dodatkową możliwość (wersja 1.2 interfejsu API wtyczki kontroli kodu źródłowego)
 Ta grupa funkcji definiuje dodatkowe funkcje dostępne w wersji 1.2 interfejsu API wtyczki kontroli kodu źródłowego. Zapewniają one dostęp do bardziej zaawansowanych funkcji i możliwości kontroli źródła.

|Funkcja|Opis|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Uruchamia operację wsadowa.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Tworzy podprojekt o podanej nazwie w ramach istniejącego projektu nadrzędnego.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Przedstawia różnice między katalogiem użytkownika lokalnego określonym przez w pełni kwalifikowaną nazwę ścieżki i lokalizację bazy danych kontroli źródła.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Sprawdza listę w pełni kwalifikowanych katalogów dla ich bieżącego stanu.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Kończy operację wsadowa.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Zwraca ścieżkę nadrzędną danego projektu (projekt musi istnieć).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Sprawdza, czy wiele wyewidencjonowań w pliku jest dozwolonych.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Sprawdza, czy wtyczka utworzy konto MSSCCPRJ. Pliki SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują zaawansowane możliwości (wersja 1.3 interfejsu API wtyczki kontroli kodu źródłowego)
 Ta grupa funkcji definiuje dodatkowe funkcje dostępne w wersji 1.3 interfejsu API wtyczki kontroli kodu źródłowego. Zapewniają one dostęp do bardziej zaawansowanych funkcji i możliwości kontroli źródła.

|Funkcja|Opis|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dodaje listę plików z kontroli źródła do bieżącego projektu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Pobiera listę plików z kontroli źródła bez interfejsu użytkownika.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Pobiera listę plików w kontroli źródła, które różnią się od plików lokalnych.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Pobiera flagi określające rozszerzone możliwości obsługiwane przez wtyczkę kontroli źródła.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Pobiera opcje specyficzne dla użytkownika.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Sprawdza listę katalogów i plików w projekcie lub projektach, które są pod kontrolą źródła. Każdy znaleziony katalog i nazwa pliku są przekazywane do funkcji wywołania zwrotnego.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Sprawdza zmiany nazw wprowadzone do listy plików. Każda nazwa pliku jest przekazywana do funkcji wywołania zwrotnego ze stanem zmiany.|

## <a name="requirements"></a>Wymagania
 Nagłówek: scc.h

 (Podany w folderze common includes zestawu SDK środowiska domyślnie znajduje się *folder [drive]* \Program Files\VSIP 8.0\EnvSDK\common\inc; również udostępniony w folderze VSIP z przykładowym plikiem MSSCCI, *[drive]* \Program Files\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)
