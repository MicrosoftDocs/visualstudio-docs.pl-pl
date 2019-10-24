---
title: Debugowanie funkcji interfejsu API systemu Windows | Microsoft Docs
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
ms.openlocfilehash: e7b5f3842160f4ffc6cecd41e65dd05ab7566dd0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734346"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Jeśli chcesz debugować funkcję interfejsu API systemu Windows z załadowanymi symbolami NT, należy wykonać następujące czynności.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows z załadowanymi symbolami NT

- Wprowadź nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja. W kodzie 32-bitowym, użyj dekoracyjnej formy nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład należy wprowadzić następujące polecenie.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Aby uzyskać nazwę dekoracyjną, zobacz [Wyświetlanie dekoracyjnych nazw](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
