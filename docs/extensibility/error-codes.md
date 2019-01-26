---
title: Kody błędów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f05a28ab046c1c0221162bce623a2ccf983f3d43
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958150"
---
# <a name="error-codes"></a>Kody błędów
Po powrocie z funkcji API wtyczki kontroli źródła wystąpił błąd oczekuje się jedną z następujących kodów błędów. Wszystkie błędy są negatywne, ostrzeżenia i kody błędów informacyjny dodatnia, i sukcesu ma wartość 0.  
  
|Kod błędu|Wartość|Opis|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Wtyczka obsługuje dodawanie plików z kontroli źródła w dwóch krokach. Aby uzyskać więcej informacji, zobacz [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Pliku lokalnego różni się od pliku w bazie danych kontroli źródła (na przykład [SccDiff](../extensibility/sccdiff-function.md) może zwracać tej wartości).|  
|`SCC_I_RELOADFILE`|5|Plik lokalny został zmieniony podczas operacji kontroli źródła; IDE należy ponownie załadować plik, jeśli jest to możliwe.|  
|`SCC_I_FILENOTAFFECTED`|4|Plik nie ma wpływu.|  
|`SCC_I_PROJECTCREATED`|3|Projekt został utworzony podczas operacji kontroli źródła (na przykład podczas wywoływania [SccOpenProject](../extensibility/sccopenproject-function.md) podczas `SCC_OP_CREATEIFNEW` określono flagę).|  
|`SCC_I_OPERATIONCANCELED`|2|Operacja została anulowana.|  
|`SCC_I_ADV_SUPPORT`|1|Wtyczka obsługuje zaawansowane opcje dla określonego polecenia. Aby uzyskać więcej informacji, zobacz [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Powodzenie.|  
|`SCC_E_INITIALIZEFAILED`|-1|Błąd: nie można zainicjować.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Błąd: projekt jest nieznany.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Błąd: nie można utworzyć projektu.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Błąd: plik jest nie wyewidencjonowany.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Błąd: plik został już wyewidencjonowany.|  
|`SCC_E_FILEISLOCKED`|-6|Błąd: plik jest zablokowany.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Błąd: plik jest wyewidencjonowany.|  
|`SCC_E_ACCESSFAILURE`|-8|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|`SCC_E_CHECKINCONFLICT`|-9|Błąd: Wystąpił konflikt podczas ewidencjonowania.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Błąd: plik już istnieje.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Błąd: plik nie jest pod kontrolą źródła.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Błąd: plik został wyewidencjonowany.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Błąd: określona wersja jest.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Błąd: operacja nie jest obsługiwana.|  
|`SCC_E_NONSPECIFICERROR`|-15|Nieokreślony błąd.|  
|`SCC_E_OPNOTPERFORMED`|-16|Błąd, operacja nie została wykonana.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Błąd: typ pliku, na przykład binarny, nie jest obsługiwany przez system kontroli kodu źródłowego.|  
|`SCC_E_VERIFYMERGE`|-18|Plik został scalony automatycznie, ale nie została sprawdzona ponieważ Weryfikacja oczekujące użytkownika.|  
|`SCC_E_FIXMERGE`|-19|Plik został scalony automatycznie, ale nie został zaewidencjonowany ze względu na konflikt scalania, które należy ręcznie rozwiązać.|  
|`SCC_E_SHELLFAILURE`|-20|Błąd z powodu błędu powłoki.|  
|`SCC_E_INVALIDUSER`|-21|Błąd: użytkownik jest nieprawidłowy.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Błąd: projekt jest już otwarty.|  
|`SCC_E_PROJSYNTAXERR`|-23|Błąd składniowy projektu.|  
|`SCC_E_INVALIDFILEPATH`|-24|Błąd: ścieżka pliku jest nieprawidłowa.|  
|`SCC_E_PROJNOTOPEN`|-25|Błąd: projekt nie jest otwarty.|  
|`SCC_E_NOTAUTHORIZED`|-26|Błąd: użytkownik nie ma uprawnień do wykonania tej operacji.|  
|`SCC_E_FILESYNTAXERR`|-27|Błąd składniowy w pliku.|  
|`SCC_E_FILENOTEXIST`|-28|Błąd, plik lokalny nie istnieje.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Błąd: Wystąpił błąd połączenia.|  
|`SCC_E_UNKNOWNERROR`|-30|Nieznany błąd.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operacja pobierania w tle jest obecnie w toku.|  
  
## <a name="macros-provided-for-quick-checking"></a>Makra przewidziane szybkie sprawdzanie  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie funkcje interfejsu API wtyczki kontroli źródła (z wyjątkiem [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), i [SccDiff](../extensibility/sccdiff-function.md)) oczekuje się pomyślnie, gdy są pliki lokalne, które są przekazywane jako argumenty nie istnieje w folderze roboczym. Na przykład, środowisko IDE może wydać wywołanie [SccCheckout](../extensibility/scccheckout-function.md) lub [SccUncheckout](../extensibility/sccuncheckout-function.md) w pliku, który nie istnieje w folderze roboczym, ale istnieje w systemie kontroli źródła. To wywołanie powiedzie się. Tylko wtedy, gdy nie ma pliku w folderze roboczym lub w systemie kontroli źródła jest Oczekiwano funkcji nie powiedzie się.  
  
 Niektóre funkcje, takie jak `SccAdd` i `SccCheckin`, w szczególności powinna zwrócić `SCC_E_FILENOTEXIST` gdy plik w folderze roboczym nie istnieje. Oczekuje się pomyślnie, gdy nie ma plików roboczych, jeśli funkcje działają na prawidłową nazwę pliku w systemie kontroli źródła, inne funkcje.  
  
 Wtyczka do kontroli źródła należy wprowadzić żadnych założeń dotyczących uprawnień do pliku w folderze roboczym, nawet wtedy, gdy wtyczki było oznaczone jako plik tylko do odczytu podczas operacji. Pliku w folderze roboczym można przenieść, usunięte i zmodyfikowane poza wtyczki w kontroli.  
  
## <a name="see-also"></a>Zobacz także  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)