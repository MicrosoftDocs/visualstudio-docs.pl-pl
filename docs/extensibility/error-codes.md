---
title: Kody błędów | Microsoft Docs
description: Ten artykuł zawiera listę kodów błędów, wartości i opisy funkcji interfejsu API wtyczki kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c9706f7c9cd5b25a3644af2f324fda01f448fa17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883405"
---
# <a name="error-codes"></a>Kody błędów
Gdy funkcja interfejsu API wtyczki kontroli źródła zwraca błąd, oczekiwany jest jeden z następujących kodów błędów. Wszystkie błędy są negatywne, ostrzeżenia lub kody błędów informacyjnych są pozytywne, a powodzenie to 0.

|Kod błędu|Wartość|Opis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Wtyczka obsługuje dodawanie plików z kontroli źródła w dwóch krokach. Aby uzyskać więcej informacji, zobacz [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Plik lokalny różni się od pliku w bazie danych kontroli źródła (na przykład [SccDiff](../extensibility/sccdiff-function.md) może zwrócić tę wartość).|
|`SCC_I_RELOADFILE`|5|Plik lokalny został zmieniony podczas operacji kontroli źródła; IDE powinien ponownie załadować plik, jeśli jest to możliwe.|
|`SCC_I_FILENOTAFFECTED`|4|Nie ma to żadnego oddziaływania na plik.|
|`SCC_I_PROJECTCREATED`|3|Projekt został utworzony podczas operacji kontroli źródła (na przykład podczas wywołania [SccOpenProject](../extensibility/sccopenproject-function.md) , gdy `SCC_OP_CREATEIFNEW` flaga jest określona).|
|`SCC_I_OPERATIONCANCELED`|2|Operacja została anulowana.|
|`SCC_I_ADV_SUPPORT`|1|Wtyczka obsługuje opcje zaawansowane dla określonego polecenia. Aby uzyskać więcej informacji, zobacz [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Powodzenie.|
|`SCC_E_INITIALIZEFAILED`|-1|Błąd: inicjowanie nie powiodło się.|
|`SCC_E_UNKNOWNPROJECT`|-2|Błąd: projekt jest nieznany.|
|`SCC_E_COULDNOTCREATEPROJECT`|–3|Błąd: nie można utworzyć projektu.|
|`SCC_E_NOTCHECKEDOUT`|-4|Błąd: plik nie został wyewidencjonowany.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Błąd: plik jest już wyewidencjonowany.|
|`SCC_E_FILEISLOCKED`|-6|Błąd: plik jest zablokowany.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Błąd: plik jest wyewidencjonowany na wyłączność.|
|`SCC_E_ACCESSFAILURE`|-8|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|`SCC_E_CHECKINCONFLICT`|-9|Błąd: podczas zaewidencjonowania wystąpił konflikt.|
|`SCC_E_FILEALREADYEXISTS`|-10|Błąd: plik już istnieje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Błąd: plik nie znajduje się pod kontrolą źródła.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Błąd: plik jest wyewidencjonowany.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Błąd: nie ma określonej wersji.|
|`SCC_E_OPNOTSUPPORTED`|-14|Błąd: operacja nie jest obsługiwana.|
|`SCC_E_NONSPECIFICERROR`|-15|Błąd nieokreślony.|
|`SCC_E_OPNOTPERFORMED`|-16|Błąd, operacja nie została wykonana.|
|`SCC_E_TYPENOTSUPPORTED`|– 17|Błąd: typ pliku, na przykład Binary, nie jest obsługiwany przez system kontroli kodu źródłowego.|
|`SCC_E_VERIFYMERGE`|-18|Plik został scalony z autoscalaniem, ale nie został sprawdzony, ponieważ oczekuje na weryfikację użytkownika.|
|`SCC_E_FIXMERGE`|-19|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który należy ręcznie rozwiązać.|
|`SCC_E_SHELLFAILURE`|-20|Błąd spowodowany niepowodzeniem powłoki.|
|`SCC_E_INVALIDUSER`|-21|Błąd: użytkownik jest nieprawidłowy.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Błąd: projekt jest już otwarty.|
|`SCC_E_PROJSYNTAXERR`|-23|Błąd składniowy projektu.|
|`SCC_E_INVALIDFILEPATH`|-24|Błąd: ścieżka pliku jest nieprawidłowa.|
|`SCC_E_PROJNOTOPEN`|-25|Błąd: projekt nie jest otwarty.|
|`SCC_E_NOTAUTHORIZED`|-26|Błąd: użytkownik nie ma autoryzacji do wykonania tej operacji.|
|`SCC_E_FILESYNTAXERR`|-27|Błąd składniowy pliku.|
|`SCC_E_FILENOTEXIST`|-28|Błąd, plik lokalny nie istnieje.|
|`SCC_E_CONNECTIONFAILURE`|-29|Błąd: Wystąpił błąd połączenia.|
|`SCC_E_UNKNOWNERROR`|–30|Nieznany błąd.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operacja pobrania w tle jest obecnie w toku.|

## <a name="macros-provided-for-quick-checking"></a>Makra udostępniane do szybkiego sprawdzania

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Uwagi
 Wszystkie funkcje interfejsu API dodatków plug-in kontroli źródła (z wyjątkiem [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)i [SccDiff](../extensibility/sccdiff-function.md)) oczekują na pomyślne, gdy pliki lokalne, które są przekazane jako argumenty nie istnieją w folderze roboczym. Na przykład IDE może wydać wywołanie [SccCheckout](../extensibility/scccheckout-function.md) lub [SccUncheckout](../extensibility/sccuncheckout-function.md) w pliku, który nie istnieje w folderze roboczym, ale istnieje w systemie kontroli źródła. To wywołanie zakończyło się pomyślnie. Tylko wtedy, gdy nie ma pliku w folderze roboczym lub w systemie kontroli źródła nie jest oczekiwana funkcja.

 Niektóre funkcje, takie jak `SccAdd` i `SccCheckin` , powinny zwrócić uwagę, `SCC_E_FILENOTEXIST` gdy plik w folderze roboczym nie istnieje. Inne funkcje oczekiwanie na pomyślne, gdy plik roboczy nie istnieje, jeśli funkcje działają na prawidłowej nazwie pliku w systemie kontroli źródła.

 Wtyczka do kontroli źródła nie powinna wprowadzać żadnych założeń dotyczących uprawnień do pliku w folderze roboczym, nawet jeśli wtyczka oznaczył plik tylko do odczytu podczas niektórych operacji. Plik w folderze roboczym można przenieść, usunąć i zmienić poza kontrolką wtyczki.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
