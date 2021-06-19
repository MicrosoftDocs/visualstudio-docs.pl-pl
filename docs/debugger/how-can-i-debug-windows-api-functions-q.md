---
title: Debugowanie funkcji interfejsu API systemu Windows | Microsoft Docs
description: Dowiedz się, jak debugować funkcję interfejsu API systemu Windows, która ma załadowane symbole NT. W kodzie 32-bitowym punkt przerwania jest ustawiany przy użyciu dekoracyjnej formy nazwy funkcji.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89fdbcf9d18a7794e1fb2520384db0f9bcec3147
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386946"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Aby debugować funkcję interfejsu API systemu Windows, która ma załadowane symbole NT, należy wykonać następujące czynności.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows z załadowanych symboli NT

- W punkcie [przerwania funkcji](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)wprowadź nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja (zobacz [operator kontekstu](../debugger/context-operator-cpp.md)). W kodzie 32-bitowym użyj dekoracyjną postaci nazwy funkcji. Aby na przykład ustawić punkt przerwania w **programie MessageBeep,** należy wprowadzić następujące informacje.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Aby uzyskać nazwę dekoracyjną, zobacz [Wyświetlanie nazwami dekoracyjną.](/previous-versions/5x49w699(v=vs.140))

     Możesz przetestować dekoracyjną nazwę i wyświetlić ją w kodzie dezmiseracyjną. Po wstrzymaniu w funkcji w Visual Studio debugerze kliknij prawym przyciskiem myszy funkcję w edytorze kodu lub oknie stosu wywołań i wybierz polecenie **Przejdź do dezasembletu.**

- W kodzie 64-bitowym można użyć nazwy nieskoedytowanych.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
