---
title: Funkcje interfejsu API wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02e2c7ee92ab138de7bee0d58835898f3bd0a58b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160617"
---
# <a name="source-control-plug-in-api-functions"></a>Funkcje interfejsu API wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interfejs API wtyczki kontroli źródła zapewnia następujące funkcje, które muszą być zaimplementowane przez wtyczka do kontroli źródła zgodnie z tego interfejsu API. Podpisy każdej funkcji i semantyka skojarzone z flag bitowych, i inne parametry zostały szczegółowo opisane w tym dokumencie.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicjowanie i celów funkcji  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zamknięcie projektu.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Monituje użytkownika o zaawansowane opcje dla danego polecenia.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Zwraca wersję do kontroli źródła wtyczek.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicjuje wtyczka do kontroli źródła. Jest on wywoływany raz dla każdego wystąpienia wtyczki.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Zostanie otwarty projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funkcja ogólna, używane do ustawiania szeroką gamę opcji. Każda opcja zaczyna się od `SCC_OPT_xxx` i ma swój własny zestaw zdefiniowanych wartości.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wywołuje się, gdy po wtyczki kontroli źródła musi zostać odłączone.|  
  
## <a name="core-source-control-functions"></a>Podstawowe funkcje kontroli źródła  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Dodaje tablicę plików określone przez nazwy w pełni kwalifikowana ścieżka do systemu kontroli źródła.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła, a następnie wprowadź tych plików będących częścią bieżącego projektu.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Sprawdza, czy w tablicy plików.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Wyewidencjonowuje tablicę plików.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Przedstawiono różnice między użytkownika lokalnego pliku, określonego przez nazwę pełną ścieżkę i wersji pod kontrolą źródła.|  
|[SccGet](../extensibility/sccget-function.md)|Pobiera kopię grupy plików tylko do odczytu.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Umożliwia sprawdzenie stanu plików, które obiekt wywołujący poprosił o (za pośrednictwem `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Powoduje, że wtyczka na monitowanie użytkownika o ścieżkę projektu, która jest zrozumiały dla dodatku typu plug-in do kontroli źródła.|  
|[SccHistory](../extensibility/scchistory-function.md)|Przedstawia historię tablicę nazw FQDN pliku lokalnego.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Sprawdza, czy lista plików dla ich bieżący stan. Ponadto używa `pfnPopulate` funkcję, aby powiadomić obiekt wywołujący, gdy plik jest niezgodny z kryteriami, które dla `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zawiera właściwości pliku w pełni kwalifikowana.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Sprawdza, czy lista plików w pełni kwalifikowaną dla ich bieżący stan.|  
|[SccRemove](../extensibility/sccremove-function.md)|Usuwa tablicy w pełni kwalifikowaną plików z systemu kontroli źródła.|  
|[SccRename](../extensibility/sccrename-function.md)|Zmienia nazwę danego pliku pod nową nazwą w systemie kontroli źródła.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Uzyskuje dostęp do pełnego zakresu funkcji systemu kontroli źródła.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Cofa wyewidencjonowanie tablicy plików.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują dodatkowe możliwości (wersja 1.2 interfejsu API wtyczki kontroli źródła)  
 Ta grupa funkcji określa dodatkowe funkcje uwzględnione w wersji 1.2 API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji kontroli źródła i możliwości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Rozpoczyna operację usługi batch.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Utworzenie podprojektu o podanej nazwie w ramach istniejącego nadrzędnego projektu.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Przedstawiono różnice między katalogu lokalnego użytkownika określonego przez nazwę pełną ścieżkę i lokalizację bazy danych kontroli źródła.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Sprawdza, czy lista katalogów w pełni kwalifikowaną ich bieżący stan.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Kończy operację usługi batch.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Zwraca nadrzędny ścieżkę danego projektu (projekt musi istnieć).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Sprawdza, czy wiele operacji wyewidencjonowania w pliku są dozwolone.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Sprawdza, czy wtyczka utworzy MSSCCPRJ. Pliki SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują zaawansowane możliwości (wersja 1.3 interfejsu API wtyczki kontroli źródła)  
 Ta grupa funkcji określa dodatkowe funkcje uwzględnione w wersji 1.3 API wtyczki kontroli źródła. Zapewniają one dostęp do bardziej zaawansowanych funkcji kontroli źródła i możliwości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Lista plików z kontroli źródła są dodawane do bieżącego projektu.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Pobiera listę plików z kontroli źródła bez interfejsu użytkownika.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Pobiera listę plików w kontroli źródła, które różnią się od plików lokalnych.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Pobranie flagi określające, rozszerzone możliwości obsługiwany przez wtyczka do kontroli źródła.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Pobiera opcje specyficzne dla użytkownika.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Sprawdza, czy lista katalogów i plików w projekcie, lub projekty, które są pod kontrolą źródła. Każdy katalog oraz nazwę pliku znaleziono jest przekazywany do funkcji wywołania zwrotnego.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Sprawdza, czy zmiany nazwy plików. Każda nazwa pliku jest przekazywany do funkcji wywołania zwrotnego z jego zmiana stanu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: scc.h  
  
 (Dostarczone w zestawie SDK środowiska wspólnego folderu, domyślnie zawiera *[dysk]* \Program Files\VSIP 8.0\EnvSDK\common\inc; również podane w folderze VSIP z przykładem MSSCCI *[dysk]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)
