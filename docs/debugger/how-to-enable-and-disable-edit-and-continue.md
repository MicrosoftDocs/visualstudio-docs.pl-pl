---
title: Włączanie i wyłączanie funkcji Edytuj i kontynuuj | Microsoft Docs
description: Dowiedz się, jak wyłączyć i włączyć opcję Edytuj i kontynuuj w Visual Studio opcje w czasie projektowania. Funkcje Edytuj i Kontynuuj działa tylko w kompilacjach debugowania.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 261963cbc1aee63374d6a9c147f42678208c39ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384710"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Jak włączyć i wyłączyć edytuj i kontynuuj (C#, VB, C++)

Możesz wyłączyć lub włączyć **opcję Edytuj**  i kontynuuj w oknie dialogowym Opcje Visual Studio w czasie projektowania. **Funkcje Edytuj i Kontynuuj** działa tylko w kompilacjach debugowania. Aby uzyskać więcej informacji, zobacz [Edit and Continue (Edytuj i kontynuuj).](../debugger/edit-and-continue.md)

W przypadku natywnego języka C++ **opcja Edytuj i kontynuuj** wymaga użycia opcji `/INCREMENTAL` . Aby uzyskać więcej informacji na temat wymagań dotyczących funkcji w języku C++, zobacz ten wpis w [blogu](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) i [temat Edytuj i kontynuuj (C++).](../debugger/edit-and-continue-visual-cpp.md)

**Aby włączyć lub wyłączyć funkcję Edytuj i kontynuuj:**

1. Jeśli jesteś w sesji debugowania, zatrzymaj debugowanie **(Debugowanie**  >  **zatrzymaj debugowanie** lub **Shift** + **F5).**

1. Na **stronie** Opcje  >  **>** (lub Opcje   >  debugowania) > **debugowania** Ogólne wybierz pozycję Edytuj i  >  kontynuuj w okienku po prawej stronie. 

    > [!NOTE]
    > Jeśli funkcja IntelliTrace jest włączona i zbierane są zarówno zdarzenia IntelliTrace, jak i informacje o wywołaniach, funkcje Edytuj i Kontynuuj są wyłączone. Aby uzyskać więcej informacji, zobacz [IntelliTrace](../debugger/intellitrace.md).

1. W przypadku kodu W  języku C++ upewnij się, że wybrano opcje Włącz edycję natywną i Kontynuuj, a następnie ustaw dodatkowe opcje:
    - **Stosowanie zmian przy kontynuowaniu (tylko natywne)**

      Jeśli ta opcja Visual Studio automatycznie kompiluje i stosuje zmiany kodu podczas kontynuowania debugowania ze stanu przerwania. W przeciwnym razie możesz zastosować zmiany przy użyciu polecenia  >  **Debuguj stosowanie zmian kodu.**

    - **Ostrzegaj o nieodświeżonym kodzie (tylko natywne)**

      Jeśli ta opcja jest zaznaczona, powoduje ostrzeżenia o nieodświeżonym kodzie.

1. Kliknij przycisk **OK**.
