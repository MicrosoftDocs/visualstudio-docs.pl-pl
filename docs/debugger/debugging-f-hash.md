---
title: Debugowanie F# | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f50c3a107f9796e4fbb661f303bfcabf284cc6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710100"
---
# <a name="debugging-f"></a>Debugowanie F#
Debugowanie F# jest podobne do debugowania jakiegokolwiek języka zarządzanego, z pewnymi wyjątkami:

-   **Autos** nie są wyświetlane w oknie F# zmiennych.

-   Edytuj i Kontynuuj nie jest obsługiwana dla F#. Edytowanie F# kodu podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany w kodzie nie są stosowane podczas sesji debugowania, edytowanie F# kodu podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowany kod.

-   Debuger nie może rozpoznać F# wyrażenia. Wprowadzenia wyrażenia, w oknie debugera lub okno dialogowe podczas F# profilowanie, musi przetłumaczyć wyrażenia w C# składni. Podczas translacji F# wyrażenie C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania dla równości, które F# używa pojedynczego =.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
