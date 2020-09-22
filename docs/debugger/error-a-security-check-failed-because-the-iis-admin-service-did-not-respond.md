---
title: Sprawdzenie zabezpieczeń nie powiodło się, ponieważ usługa administratora usług IIS nie odpowiadała | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 015a159f8d4910a2cc9bfbd97a50ebe01253d011
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852813"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Błąd: Sprawdzanie zabezpieczeń nie powiodło się ponieważ usługa administratora nie odpowiada
Ten błąd występuje, gdy usługa administratora usług IIS nie odpowiada. Zazwyczaj oznacza to, że występuje problem z instalacją usług IIS. Najpierw sprawdź, czy usługa jest uruchomiona przy użyciu narzędzia **usług** z **narzędzi administracyjnych**.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Ponownie zainstaluj usługi IIS przy użyciu apletu **Dodaj lub usuń programy** w panelu sterowania.

- -lub-

- Usuń usługi IIS z maszyny za pomocą panelu sterowania Dodaj lub usuń programy. Jeśli usługi IIS zostały usunięte i nadal występują problemy, sprawdź rejestr i upewnij się, że ten klucz już nie istnieje:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -lub-

- Wyłącz usługę administratora usług IIS przy użyciu panelu sterowania narzędzia administracyjne. Spowoduje to wyłączenie usług IIS na komputerze.

     Po wykonaniu któregoś z tych trzech kroków ponownie uruchom maszynę.

     Dodatkowe informacje znajdują się w dokumentacji usług IIS.

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)