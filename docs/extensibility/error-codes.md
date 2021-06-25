---
title: Kody błędów | Microsoft Docs
description: Ten artykuł zawiera listę kodów błędów, wartości i opisów funkcji interfejsu API wtyczki kontroli kodu źródłowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898308"
---
# <a name="error-codes"></a>Kody błędów
Gdy funkcja interfejsu API wtyczki kontroli kodu źródłowego zwraca błąd, powinien to być jeden z następujących kodów błędów. Wszystkie błędy są ujemne, ostrzeżenia lub informacyjne kody błędów są dodatnie, a powodzenie wynosi 0.

|Kod błędu|Wartość|Opis|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Wtyczka obsługuje dodawanie plików z kontroli źródła w dwóch krokach. Aby uzyskać więcej informacji, zobacz [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Plik lokalny różni się od pliku w bazie danych kontroli źródła (na przykład [SccDiff](../extensibility/sccdiff-function.md) może zwrócić tę wartość).|
|`SCC_I_RELOADFILE`|5|Plik lokalny został zmieniony podczas operacji kontroli źródła; Jeśli to możliwe, w idee należy ponownie załadować plik.|
|`SCC_I_FILENOTAFFECTED`|4|Nie ma to wpływu na plik.|
|`SCC_I_PROJECTCREATED`|3|Projekt został utworzony podczas operacji kontroli źródła (na przykład podczas wywołania [SccOpenProject,](../extensibility/sccopenproject-function.md) gdy `SCC_OP_CREATEIFNEW` jest określona flaga).|
|`SCC_I_OPERATIONCANCELED`|2|Operacja została anulowana.|
|`SCC_I_ADV_SUPPORT`|1|Wtyczka obsługuje opcje zaawansowane dla określonego polecenia. Aby uzyskać więcej informacji, zobacz [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Powodzenie.|
|`SCC_E_INITIALIZEFAILED`|-1|Błąd: inicjowanie nie powiodło się.|
|`SCC_E_UNKNOWNPROJECT`|-2|Błąd: projekt jest nieznany.|
|`SCC_E_COULDNOTCREATEPROJECT`|–3|Błąd: nie można utworzyć projektu.|
|`SCC_E_NOTCHECKEDOUT`|-4|Błąd: plik nie jest wyewidencjonowany.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Błąd: plik jest już wyewidencjonowany.|
|`SCC_E_FILEISLOCKED`|-6|Błąd: plik jest zablokowany.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Błąd: plik jest wyewidencjonowany wyłącznie.|
|`SCC_E_ACCESSFAILURE`|-8|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskusją. Zaleca się ponawianie próby.|
|`SCC_E_CHECKINCONFLICT`|-9|Błąd: wystąpił konflikt podczas zaewidencji.|
|`SCC_E_FILEALREADYEXISTS`|-10|Błąd: plik już istnieje.|
|`SCC_E_FILENOTCONTROLLED`|-11|Błąd: plik nie jest pod kontrolą źródła.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Błąd: plik jest wyewidencjonowany.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Błąd: nie ma określonej wersji.|
|`SCC_E_OPNOTSUPPORTED`|-14|Błąd: operacja nie jest obsługiwana.|
|`SCC_E_NONSPECIFICERROR`|-15|Błąd nieokreślony.|
|`SCC_E_OPNOTPERFORMED`|-16|Błąd, operacja nie została wykonana.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Błąd: typ pliku, na przykład binarny, nie jest obsługiwany przez system kontroli kodu źródłowego.|
|`SCC_E_VERIFYMERGE`|-18|Plik został automatycznie scalony, ale nie został sprawdzony, ponieważ oczekuje na weryfikację użytkownika.|
|`SCC_E_FIXMERGE`|-19|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który należy rozwiązać ręcznie.|
|`SCC_E_SHELLFAILURE`|-20|Błąd spowodowany awarią powłoki.|
|`SCC_E_INVALIDUSER`|-21|Błąd: użytkownik jest nieprawidłowy.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Błąd: projekt jest już otwarty.|
|`SCC_E_PROJSYNTAXERR`|-23|Błąd składni projektu.|
|`SCC_E_INVALIDFILEPATH`|-24|Błąd: ścieżka pliku jest nieprawidłowa.|
|`SCC_E_PROJNOTOPEN`|-25|Błąd: projekt nie jest otwarty.|
|`SCC_E_NOTAUTHORIZED`|-26|Błąd: użytkownik nie ma autoryzacji do wykonania tej operacji.|
|`SCC_E_FILESYNTAXERR`|-27|Błąd składni pliku.|
|`SCC_E_FILENOTEXIST`|-28|Błąd, plik lokalny nie istnieje.|
|`SCC_E_CONNECTIONFAILURE`|-29|Błąd: wystąpił błąd połączenia.|
|`SCC_E_UNKNOWNERROR`|–30|Nieznany błąd.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operacja get w tle jest obecnie w toku.|

## <a name="macros-provided-for-quick-checking"></a>Makra dostępne do szybkiego sprawdzania

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Uwagi
 Wszystkie funkcje interfejsu API wtyczki kontroli kodu źródłowego (z wyjątkiem [funkcji SccAdd,](../extensibility/sccadd-function.md) [SccCheckin](../extensibility/scccheckin-function.md)i [SccDiff)](../extensibility/sccdiff-function.md)powinny zakończyć się powodzeniem, gdy lokalne pliki, które są przekazywane jako argumenty, nie istnieją w folderze pracy. Na przykład idee mogą wydać wywołanie [SccCheckout](../extensibility/scccheckout-function.md) lub [SccUncheckout](../extensibility/sccuncheckout-function.md) w pliku, który nie istnieje w folderze roboczych, ale istnieje w systemie kontroli źródła. To wywołanie zakończy się pomyślnie. Funkcja oczekuje awarii tylko wtedy, gdy w folderze operacyjnym lub systemie kontroli źródła nie ma pliku.

 Niektóre funkcje, takie jak i , powinny zwracać dane, gdy plik w folderze roboczych `SccAdd` `SccCheckin` nie `SCC_E_FILENOTEXIST` istnieje. Inne funkcje powinny zakończyć się powodzeniem, gdy plik roboczy nie istnieje, jeśli funkcje działają na prawidłowej nazwie pliku w systemie kontroli źródła.

 Wtyczka kontroli źródła nie powinna mieć żadnych założeń dotyczących uprawnień w pliku w folderze roboczych, nawet jeśli wtyczka oznaczyła plik tylko do odczytu podczas niektórych operacji. Plik w folderze roboczych można przenosić, usuwać i zmieniać poza kontrolą wtyczki.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
