---
title: 'Błąd: Sprawdzanie zabezpieczeń nie powiodło się, ponieważ administrator usług IIS nie odpowiada. | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65eb724d14123292a0694623bf46859f8a3966f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197086"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Błąd: Sprawdzenie zabezpieczeń nie powiodło się, ponieważ usługa administracyjna IIS nie odpowiedziała
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy administrator usług IIS nie odpowiada. Zwykle oznacza to, że występuje problem z instalacją usług IIS. Po pierwsze sprawdzenie, czy usługa jest uruchomiona przy użyciu **usług** narzędzia z **narzędzia administracyjne**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ponowne zainstalowanie usług IIS, przy użyciu **apletu Dodaj lub usuń programy** Panelu sterowania.  
  
- —lub—  
  
- Usuwanie usług IIS z komputera, przy użyciu apletu Dodaj lub usuń programy w Panelu sterowania. Jeśli usunięto usług IIS i nadal występują problemy, sprawdź rejestru i upewnij się, że ten klucz nie istnieje:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     —lub—  
  
- Wyłącz Administrator usług IIS, za pomocą Panelu sterowania narzędzia administracyjne. Spowoduje to wyłączenie usług IIS na komputerze.  
  
     Po wykonaniu dowolnej z tych trzech kroków, uruchom ponownie komputer.  
  
     Aby uzyskać dodatkowe informacje Zobacz dokumentację usług IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
