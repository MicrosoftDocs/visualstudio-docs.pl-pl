---
title: 'Błąd: nie można nawiązać połączenia z maszyną &lt;name &gt;. Nie można odnaleźć maszyny w sieci. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736834"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: nie można nawiązać połączenia z maszyną &lt;name &gt;. Nie można odnaleźć maszyny w sieci.
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