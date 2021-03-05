---
title: Nie można nawiązać połączenia z &lt; nazwą komputera &gt; . Nie można odnaleźć maszyny w sieci. | Microsoft Docs
description: 'Takie zachowanie występuje, gdy spełniony jest jeden z następujących warunków: (1) połączenie z komputerem zdalnym zostało przerwane. (2) Twoje konto użytkownika na komputerze zdalnym jest wyłączone. (3) Twoje hasło wygasło.'
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146434"
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

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
