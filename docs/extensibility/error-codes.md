---
title: Kody błędów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711841"
---
# <a name="error-codes"></a>Kody błędów
Gdy funkcja interfejsu API wtyczki kontroli źródła zwraca błąd, oczekuje się, że będzie jednym z następujących kodów błędów. Wszystkie błędy są negatywne, ostrzeżenia lub kody błędów informacyjnych są dodatnie, a powodzenie wynosi 0.

|Kod błędu|Wartość|Opis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Wtyczka obsługuje dodawanie plików z kontroli źródła w dwóch krokach. Aby uzyskać więcej informacji, zobacz [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Plik lokalny różni się od pliku w bazie danych kontroli źródła (na przykład [SccDiff](../extensibility/sccdiff-function.md) może zwrócić tę wartość).|
|`SCC_I_RELOADFILE`|5|Plik lokalny został zmieniony podczas operacji kontroli źródła; IDE należy ponownie załadować plik, jeśli to możliwe.|
|`SCC_I_FILENOTAFFECTED`|4|Nie ma to wpływu na plik.|
|`SCC_I_PROJECTCREATED`|3|Projekt został utworzony podczas operacji kontroli źródła (na przykład podczas wywołania [SccOpenProject,](../extensibility/sccopenproject-function.md) gdy `SCC_OP_CREATEIFNEW` flaga jest określona).|
|`SCC_I_OPERATIONCANCELED`|2|Operacja została anulowana.|
|`SCC_I_ADV_SUPPORT`|1|Wtyczka obsługuje zaawansowane opcje dla określonego polecenia. Aby uzyskać więcej informacji, zobacz [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Powodzenie.|
|`SCC_E_INITIALIZEFAILED`|-1|Błąd: inicjowanie nie powiodło się.|
|`SCC_E_UNKNOWNPROJECT`|-2|Błąd: projekt jest nieznany.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Błąd: nie można utworzyć projektu.|
|`SCC_E_NOTCHECKEDOUT`|-4|Błąd: plik nie jest wyewidencjonowany.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Błąd: plik jest już wyewidencjonowany.|
|`SCC_E_FILEISLOCKED`|-6|Błąd: plik jest zablokowany.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Błąd: plik jest wyewidencjonowany wyłącznie.|
|`SCC_E_ACCESSFAILURE`|-8|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|`SCC_E_CHECKINCONFLICT`|-9|Błąd: podczas odprawy wystąpił konflikt.|
|`SCC_E_FILEALREADYEXISTS`|-10|Błąd: plik już istnieje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Błąd: plik nie jest pod kontrolą źródła.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Błąd: plik jest wyewidencjonowany.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Błąd: nie ma określonej wersji.|
|`SCC_E_OPNOTSUPPORTED`|-14|Błąd: operacja nie jest obsługiwana.|
|`SCC_E_NONSPECIFICERROR`|-15|Błąd niespecyficzne.|
|`SCC_E_OPNOTPERFORMED`|-16|Błąd, operacja nie została wykonana.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Błąd: typ pliku, na przykład binarny, nie jest obsługiwany przez system kontroli kodu źródłowego.|
|`SCC_E_VERIFYMERGE`|-18|Plik został automatycznie scalony, ale nie został sprawdzony, ponieważ oczekuje na weryfikację użytkownika.|
|`SCC_E_FIXMERGE`|-19|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który musi zostać rozwiązany ręcznie.|
|`SCC_E_SHELLFAILURE`|-20|Błąd spowodowany awarią powłoki.|
|`SCC_E_INVALIDUSER`|-21|Błąd: użytkownik jest nieprawidłowy.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Błąd: projekt jest już otwarty.|
|`SCC_E_PROJSYNTAXERR`|-23|Błąd składni projektu.|
|`SCC_E_INVALIDFILEPATH`|-24|Błąd: ścieżka pliku jest nieprawidłowa.|
|`SCC_E_PROJNOTOPEN`|-25|Błąd: projekt nie jest otwarty.|
|`SCC_E_NOTAUTHORIZED`|-26|Błąd: użytkownik nie jest autoryzowany do wykonania tej operacji.|
|`SCC_E_FILESYNTAXERR`|-27|Błąd składni pliku.|
|`SCC_E_FILENOTEXIST`|-28|Błąd, plik lokalny nie istnieje.|
|`SCC_E_CONNECTIONFAILURE`|-29|Błąd: wystąpił błąd połączenia.|
|`SCC_E_UNKNOWNERROR`|–30|Nieznany błąd.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operacja pobierz w tle jest obecnie w toku.|

## <a name="macros-provided-for-quick-checking"></a>Makra przeznaczone do szybkiego sprawdzania

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Uwagi
 Wszystkie funkcje interfejsu API dodatku Plug-in for source (z wyjątkiem [funkcji SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)i [SccDiff)](../extensibility/sccdiff-function.md)mają zakończyć się pomyślnie, gdy pliki lokalne, które są przekazywane jako argumenty, nie istnieją w folderze roboczym. Na przykład IDE może wystosować wywołanie [SccCheckout](../extensibility/scccheckout-function.md) lub [SccUncheckout](../extensibility/sccuncheckout-function.md) na plik, który nie istnieje w folderze roboczym, ale istnieje w systemie kontroli źródła. To wywołanie zakończy się pomyślnie. Tylko wtedy, gdy nie ma pliku w folderze roboczym lub w systemie kontroli źródła oczekuje się, że funkcja zakończy się niepowodzeniem.

 Niektóre funkcje, `SccAdd` `SccCheckin`takie jak i `SCC_E_FILENOTEXIST` , powinny być zwracane, gdy plik w folderze roboczym nie istnieje. Oczekuje się, że inne funkcje powiodą się, gdy plik roboczy nie istnieje, jeśli funkcje działają na prawidłowej nazwie pliku w systemie kontroli źródła.

 Wtyczka kontroli źródła nie powinna zakładać żadnych założeń dotyczących uprawnień w pliku w folderze roboczym, nawet jeśli wtyczka oznaczyła plik tylko do odczytu podczas niektórych operacji. Plik w folderze roboczym można przenosić, usuwać i zmieniać poza formantem wtyczki.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
