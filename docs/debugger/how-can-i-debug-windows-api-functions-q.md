---
title: Debugowanie funkcji interfejsu API systemu Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: how-to
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
ms.openlocfilehash: 6fab5627f3d467c0df289969e4fee010dd3ea78b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350397"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Jeśli chcesz debugować funkcję interfejsu API systemu Windows z załadowanymi symbolami NT, należy wykonać następujące czynności.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows z załadowanymi symbolami NT

- W [punkcie przerwania funkcji](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)wprowadź nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja (zobacz [operator kontekstu](../debugger/context-operator-cpp.md)). W kodzie 32-bitowym, użyj dekoracyjnej formy nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład należy wprowadzić następujące polecenie.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Aby uzyskać nazwę dekoracyjną, zobacz [Wyświetlanie dekoracyjnych nazw](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

     Możesz przetestować dekoracyjną nazwę i wyświetlić ją w kodzie demontażu. Gdy jest wstrzymana funkcja w debugerze programu Visual Studio, kliknij prawym przyciskiem myszy funkcję w edytorze kodu lub oknie stosu wywołań i wybierz polecenie **Przejdź do demontażu**.

- W kodzie 64-bitowym można użyć niedekoracyjnej nazwy.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — Często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
