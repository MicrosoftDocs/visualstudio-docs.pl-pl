---
title: Debugowanie funkcji interfejsu API Windows | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17e0c76e45dccb657b90fa0b36934061944cac0b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700084"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Jeśli chcesz debugować funkcja interfejsu API Windows, która zawiera symbole NT załadowane, wykonaj następujące czynności.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji Windows API z symbole NT załadowane

-   Podaj nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja. W 32-bitowego kodu formularz dekorowane nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład, należy wprowadzić następujące czynności.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Aby uzyskać nazwę z atrybutami, zobacz [wyświetlania nazw Ozdobionych](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
