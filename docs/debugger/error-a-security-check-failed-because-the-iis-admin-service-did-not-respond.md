---
description: Ten błąd występuje, gdy usługa administratora usług IIS nie odpowiada.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42c0a5a1a1fdb3a997f46a6933df9c8681fe0498
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147085"
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

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
