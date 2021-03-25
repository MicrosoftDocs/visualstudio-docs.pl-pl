---
title: Flagi możliwości | Microsoft Docs
description: Dowiedz się więcej na temat SCC_CAP_xxx flag, które wskazują możliwości wtyczki kontroli źródła i SCC_EXCAP_xxx flagi wskazujące rozszerzone możliwości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12acefb99de787d55bc0f932757dde5ea928c6cb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094929"
---
# <a name="capability-flags"></a>Flagi możliwości
Flagi SCC_CAP_ *XXX* są flagami bitowymi używanymi do wskazywania możliwości wtyczki kontroli źródła. Flagi SCC_EXCAP_ *XXX* są flagami przyrostowymi, które wskazują rozszerzone możliwości i rozwiązują wartości całkowite.

|Kod możliwości|Wartość|Opis|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001|Obsługuje [SccRemove](../extensibility/sccremove-function.md) i polecenie.|
|`SCC_CAP_RENAME`|0x00000002L|Obsługuje [SccRename](../extensibility/sccrename-function.md) i polecenie.|
|`SCC_CAP_DIFF`|0x00000004L|Obsługuje [SccDiff](../extensibility/sccdiff-function.md) i polecenie.|
|`SCC_CAP_HISTORY`|0x00000008L|Obsługuje [SccHistory](../extensibility/scchistory-function.md) i polecenie.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Obsługuje [SccProperties](../extensibility/sccproperties-function.md) i polecenie.|
|`SCC_CAP_RUNSCC`|0x00000020L|Obsługuje [SccRunScc](../extensibility/sccrunscc-function.md) i polecenie.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Obsługuje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i polecenie.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Obsługuje [SccQueryInfo](../extensibility/sccqueryinfo-function.md) i polecenie.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Obsługuje [SccGetEvents](../extensibility/sccgetevents-function.md) i polecenie.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Obsługuje [SccGetProjPath](../extensibility/sccgetprojpath-function.md) i polecenie.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Obsługuje [SccAddFromScc](../extensibility/sccaddfromscc-function.md) i polecenie.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Obsługuje komentarz dotyczący wyewidencjonowania.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Obsługuje komentarz dotyczący zaewidencjonowania.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Obsługuje komentarz po dodaniu.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Obsługuje komentarz po usunięciu.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapisuje tekst do funkcji wyjściowej dostarczonej przez IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Obsługuje przechowywanie plików bez różnic.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Obsługuje wiele historii plików.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Obsługuje Porównanie plików bez uwzględniania wielkości liter.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Obsługuje Porównanie plików, które ignoruje biały znak.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Obsługuje wyszukiwanie dodatkowych plików.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Obsługuje komentarze w programie Create Project.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Program obsługuje różnice we wszystkich stanach, jeśli są objęte kontrolką.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Wtyczka nie obsługuje interfejsu użytkownika do pobrania, ale środowisko IDE może nadal wywoływać [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Wtyczka jest współużytkowana i bezpieczna wątkowo. W wersji 1,0 nie założono, że wtyczki są współużytkowane i bezpieczne wątkowo. Jeśli wtyczka 1,1 ustawia ten bit, host może otworzyć wiele projektów równolegle.|

## <a name="capability-bits-added-in-version-12"></a>Liczba bitów możliwości dodanych w wersji 1,2

|Kod możliwości|Wartość|Opis|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Obsługuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Obsługuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Obsługuje [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Obsługuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Obsługuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Obsługuje wiele wyewidencjonowania dla pliku i [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Obsługuje plik *MSSCCPRJ. SCC* (podlega przesłonięciu użytkownika/administratora) i [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Liczba bitów możliwości dodanych w wersji 1,3
 Te flagi są przesyłane pojedynczo do funkcji [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) , aby określić, czy możliwość jest obsługiwana.

|Rozszerzony kod możliwości|Wartość|Opis|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Obsługuje `SCC_CHECKOUT_LOCALVER` opcję wyewidencjonowania.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Obsługuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Obsługuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Obsługuje Znajdowanie dodatkowych katalogów.|
|`SCC_EXCAP_QUERYCHANGES`|5|Obsługuje wyliczanie zmian plików.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Obsługuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Obsługuje [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Obsługuje wywoływanie SccQueryInfo na wielu wątkach.|
|`SCC_EXCAP_REMOVE_DIR`|9|Obsługuje funkcję SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Może usuwać wyewidencjonowane pliki.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Można zmienić nazwy wyewidencjonowanych plików.|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
