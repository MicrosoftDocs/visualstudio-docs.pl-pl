---
title: Flagi możliwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 958cbc17c843ba4d23ac83b928f7b517ada93080
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922130"
---
# <a name="capability-flags"></a>Flagi możliwości
SCC_CAP_*xxx* flagi są flag bitowych służy do wskazywania możliwości wtyczki kontroli źródła. SCC_EXCAP_*xxx* flagi są przyrostowe flagi, które wskazują rozszerzone możliwości i prowadzić do liczb całkowitych.  
  
|Kod funkcji|Wartość|Opis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Obsługuje [SccRemove](../extensibility/sccremove-function.md) i polecenia.|  
|`SCC_CAP_RENAME`|0x00000002L|Obsługuje [SccRename](../extensibility/sccrename-function.md) i polecenia.|  
|`SCC_CAP_DIFF`|0x00000004L|Obsługuje [SccDiff](../extensibility/sccdiff-function.md) i polecenia.|  
|`SCC_CAP_HISTORY`|0x00000008L|Obsługuje [SccHistory](../extensibility/scchistory-function.md) i polecenia.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Obsługuje [SccProperties](../extensibility/sccproperties-function.md) i polecenia.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Obsługuje [SccRunScc](../extensibility/sccrunscc-function.md) i polecenia.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Obsługuje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i polecenia.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Obsługuje [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i polecenia.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Obsługuje [SccGetEvents](../extensibility/sccgetevents-function.md) i polecenia.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Obsługuje [SccGetProjPath](../extensibility/sccgetprojpath-function.md) i polecenia.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Obsługuje [SccAddFromScc](../extensibility/sccaddfromscc-function.md) i polecenia.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Obsługuje komentarz wyewidencjonowania.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Obsługuje komentarza zaewidencjonowania.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Obsługuje Dodaj komentarz.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Obsługuje komentarz na usunięcie.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapisuje tekst funkcji IDE — pod warunkiem danych wyjściowych.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Obsługuje przechowywanie plików bez różnic.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Obsługuje wiele historii plików.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Obsługuje porównania bez uwzględniania wielkości liter pliku.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Obsługuje plików porównanie, które ignoruje biały znak.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Obsługuje znajdowanie dodatkowych plików.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Obsługuje komentarze dotyczące tworzenia projektu.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Obsługuje różnic w wszystkie stany, jeśli komputer znajduje się pod kontrolą.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Wtyczka nie obsługuje interfejsu użytkownika dla Get, ale IDE nadal może wywołać [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Dodatek jest współużytkowane i metodą o bezpiecznych wątkach. W wersji 1.0 nie dodatków plug-in zakłada się, że współużytkowane i metodą o bezpiecznych wątkach. Jeśli 1.1 wtyczka ustawia ten bit, host może otwierać wiele projektów równolegle.|  
  
## <a name="capability-bits-added-in-version-12"></a>Usługa bits możliwości dodane w wersji 1.2  
  
|Kod funkcji|Wartość|Opis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Obsługuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Obsługuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Obsługuje [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Obsługuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Obsługuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Obsługuje wiele operacji wyewidencjonowania w pliku i [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Obsługuje *MSSCCPRJ.SCC* pliku (zależnie od użytkownika/administratora zastąpienie) i [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Usługa bits możliwości dodane w wersji 1.3  
 Te flagi są przekazywane pojedynczo do [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) funkcję, aby ustalić, czy ta funkcja jest obsługiwana.  
  
|Rozszerzone możliwości kodu|Wartość|Opis|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Obsługuje `SCC_CHECKOUT_LOCALVER` opcji dla operacji wyewidencjonowania.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Obsługuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Obsługuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Obsługuje znajdowanie dodatkowych katalogów.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Obsługuje wyliczania zmian w plikach.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Obsługuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Obsługuje [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Obsługuje wywołanie SccQueryInfo w wielu wątkach.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Obsługuje funkcję SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Można usunąć pliki wyewidencjonowany.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Można zmienić nazwy plików wyewidencjonowany.|  
  
## <a name="see-also"></a>Zobacz także  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)