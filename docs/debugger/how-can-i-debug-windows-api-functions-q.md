---
title: Debugowanie funkcji interfejsu API systemu Windows | Microsoft Docs
description: Dowiedz się, jak debugować funkcję interfejsu API systemu Windows z załadowanymi symbolami NT. W 32-bitowym kodzie używasz formularza o nazwie funkcji, aby ustawić punkt przerwania.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: d84bdc20ab4601798e1f967c1352468e750fa9bd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155216"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Jeśli chcesz debugować funkcję interfejsu API systemu Windows z załadowanymi symbolami NT, należy wykonać następujące czynności.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows z załadowanymi symbolami NT

- W [punkcie przerwania funkcji](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)wprowadź nazwę funkcji wraz z nazwą biblioteki DLL, w której znajduje się funkcja (zobacz [operator kontekstu](../debugger/context-operator-cpp.md)). W kodzie 32-bitowym, użyj dekoracyjnej formy nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład należy wprowadzić następujące polecenie.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Aby uzyskać nazwę dekoracyjną, zobacz [Wyświetlanie dekoracyjnych nazw](/previous-versions/5x49w699(v=vs.140)).

     Możesz przetestować dekoracyjną nazwę i wyświetlić ją w kodzie demontażu. Gdy jest wstrzymana funkcja w debugerze programu Visual Studio, kliknij prawym przyciskiem myszy funkcję w edytorze kodu lub oknie stosu wywołań i wybierz polecenie **Przejdź do demontażu**.

- W kodzie 64-bitowym można użyć niedekoracyjnej nazwy.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Zobacz też
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
