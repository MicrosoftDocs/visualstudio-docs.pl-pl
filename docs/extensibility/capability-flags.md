---
title: Flagi możliwości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739866"
---
# <a name="capability-flags"></a>Flagi możliwości
Flagi SCC_CAP_*xxx* są flagami bitowymi używanymi do wskazywania możliwości wtyczki kontroli źródła. Flagi SCC_EXCAP_*xxx* są flagami przyrostowymi, które wskazują rozszerzone możliwości i rozwiązują wartości całkowite.

|Kod możliwości|Wartość|Opis|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Obsługuje [SccRemove](../extensibility/sccremove-function.md) i polecenia.|
|`SCC_CAP_RENAME`|0x00000002L|Obsługuje [SccRename](../extensibility/sccrename-function.md) i polecenia.|
|`SCC_CAP_DIFF`|0x00000004L|Obsługuje [SccDiff](../extensibility/sccdiff-function.md) i polecenia.|
|`SCC_CAP_HISTORY`|0x00000008L|Obsługuje [SccHistory](../extensibility/scchistory-function.md) i polecenia.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Obsługuje [właściwości SccProperties](../extensibility/sccproperties-function.md) i polecenia.|
|`SCC_CAP_RUNSCC`|0x00000020L|Obsługuje [SccRunScc](../extensibility/sccrunscc-function.md) i polecenia.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Obsługuje [SccGetComdOptions](../extensibility/sccgetcommandoptions-function.md) i polecenia.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Obsługuje [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i polecenia.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Obsługuje [SccGetEvents](../extensibility/sccgetevents-function.md) i polecenia.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Obsługuje [SccGetProjPath](../extensibility/sccgetprojpath-function.md) i polecenia.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Obsługuje [polecenie SccAddFromScc](../extensibility/sccaddfromscc-function.md) i polecenie.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Obsługuje komentarz do realizacji transakcji.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Obsługuje komentarz w sprawie zaewidencjonowania.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Obsługuje komentarz na Dodaj.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Obsługuje komentarz na Usuń.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapisuje tekst do funkcji wyjściowej dostarczonej przez IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Obsługuje przechowywanie plików bez różnic.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Obsługuje wiele historii plików.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Obsługuje porównanie plików bez uwzględniania wielkości liter.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Obsługuje porównywanie plików, które ignoruje biały znak.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Obsługuje znajdowanie dodatkowych plików.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Obsługuje komentarze dotyczące tworzenia projektu.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Obsługuje różnice we wszystkich stanach, jeśli są pod kontrolą.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Wtyczka nie obsługuje interfejsu użytkownika get, ale IDE może nadal wywoływać [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Wtyczka jest reentrant i gwinty bezpieczne. W wersji 1.0 nie zakładano, że wtyczki są reentrant i bezpieczne dla wątków. Jeśli wtyczka 1.1 ustawia ten bit, host może otwierać wiele projektów równolegle.|

## <a name="capability-bits-added-in-version-12"></a>Bity możliwości dodane w wersji 1.2

|Kod możliwości|Wartość|Opis|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Obsługuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Obsługuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Obsługuje [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Obsługuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Obsługuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Obsługuje wiele wyewidencjonowania w pliku i [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Obsługuje plik *MSSCCPRJ.SCC* (z zastrzeżeniem zastąpienia użytkownika/administratora) i [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bity możliwości dodane w wersji 1.3
 Flagi te są przekazywane po jednym na raz do [funkcji SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) w celu ustalenia, czy możliwości są obsługiwane.

|Rozszerzony kod możliwości|Wartość|Opis|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Obsługuje `SCC_CHECKOUT_LOCALVER` opcję dla wyewidencjonowania.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Obsługuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Obsługuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Obsługuje znajdowanie dodatkowych katalogów.|
|`SCC_EXCAP_QUERYCHANGES`|5|Obsługuje wyliczanie zmian plików.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Obsługuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Obsługuje [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Obsługuje wywoływanie SccQueryInfo w wielu wątkach.|
|`SCC_EXCAP_REMOVE_DIR`|9|Obsługuje funkcję SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Można usunąć wyewidencjonowane pliki.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Można zmienić nazwę wyewidencjonowanych plików.|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
