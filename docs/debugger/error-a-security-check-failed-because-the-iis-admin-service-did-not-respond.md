---
title: 'Błąd: Sprawdzanie zabezpieczeń nie powiodło się, ponieważ administrator usług IIS nie odpowiada. | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21329a89e5ca6971143de9cf76d357be0f86e9ab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992597"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Błąd: Sprawdzanie zabezpieczeń nie powiodło się, ponieważ administrator usług IIS nie odpowiada.
Ten błąd występuje, gdy administrator usług IIS nie odpowiada. Zwykle oznacza to, że występuje problem z instalacją usług IIS. Po pierwsze sprawdzenie, czy usługa jest uruchomiona przy użyciu **usług** narzędzia z **narzędzia administracyjne**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ponowne zainstalowanie usług IIS, przy użyciu **apletu Dodaj lub usuń programy** Panelu sterowania.  
  
-   —lub—  
  
-   Usuwanie usług IIS z komputera, przy użyciu apletu Dodaj lub usuń programy w Panelu sterowania. Jeśli usunięto usług IIS i nadal występują problemy, sprawdź rejestru i upewnij się, że ten klucz nie istnieje:  
  
    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`  
  
     —lub—  
  
-   Wyłącz Administrator usług IIS, za pomocą Panelu sterowania narzędzia administracyjne. Spowoduje to wyłączenie usług IIS na komputerze.  
  
     Po wykonaniu dowolnej z tych trzech kroków, uruchom ponownie komputer.  
  
     Aby uzyskać dodatkowe informacje Zobacz dokumentację usług IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)