---
title: 'Błąd: Sprawdzanie zabezpieczeń nie powiodło się, ponieważ usługa administratora usług IIS nie odpowiada | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197086"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Błąd: Sprawdzanie zabezpieczeń nie powiodło się ponieważ usługa administratora nie odpowiada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy usługa administratora usług IIS nie odpowiada. Zazwyczaj oznacza to, że występuje problem z instalacją usług IIS. Najpierw sprawdź, czy usługa jest uruchomiona przy użyciu narzędzia **usług** z **narzędzi administracyjnych**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ponownie zainstaluj usługi IIS przy użyciu apletu **Dodaj lub usuń programy** w panelu sterowania.  
  
- -lub-  
  
- Usuń usługi IIS z maszyny za pomocą panelu sterowania Dodaj lub usuń programy. Jeśli usługi IIS zostały usunięte i nadal występują problemy, sprawdź rejestr i upewnij się, że ten klucz już nie istnieje:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -lub-  
  
- Wyłącz usługę administratora usług IIS przy użyciu panelu sterowania narzędzia administracyjne. Spowoduje to wyłączenie usług IIS na komputerze.  
  
     Po wykonaniu któregoś z tych trzech kroków ponownie uruchom maszynę.  
  
     Dodatkowe informacje znajdują się w dokumentacji usług IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
