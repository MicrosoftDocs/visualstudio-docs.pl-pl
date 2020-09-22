---
title: Nie można nawiązać połączenia z &lt; nazwą komputera &gt; . Nie można odnaleźć maszyny w sieci. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1ab43773b4aa9d2535eb6ac157ec39333907731
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852514"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: nie można nawiązać połączenia z &lt; nazwą komputera &gt; . Nie można odnaleźć maszyny w sieci.
Takie zachowanie występuje, gdy spełniony jest jeden z następujących warunków:

- Połączenie z komputerem zdalnym zostało przerwane.

- Twoje konto użytkownika na komputerze zdalnym jest wyłączone.

- Hasło na komputerze zdalnym wygasło.

### <a name="to-resolve-this-behavior"></a>Aby rozwiązać ten problem

- Upewnij się, że komputer lokalny i komputer zdalny znajdują się w tej samej sieci. Aby to zrobić, użyj Eksploratora Microsoft Windows (lub Eksploratora plików), aby spróbować uzyskać dostęp do komputera zdalnego.

     lub

- Upewnij się, że konto użytkownika używane do nawiązywania połączenia z komputerem zdalnym jest włączone.

     lub

- Upewnij się, że hasło używane do nawiązania połączenia z komputerem zdalnym jest prawidłowe i nie wygasło.

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)