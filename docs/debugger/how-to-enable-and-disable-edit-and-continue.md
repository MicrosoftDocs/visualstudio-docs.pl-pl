---
title: 'Instrukcje: Włączanie i wyłączanie Edytuj i Kontynuuj | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430533"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Instrukcje: Włączanie i wyłączanie Edytuj i Kontynuuj (C#, VB,) C++

Można wyłączyć lub włączyć opcję **Edytuj i Kontynuuj** w oknie dialogowym **Opcje** programu Visual Studio w czasie projektowania. Polecenie **Edytuj i Kontynuuj** działa tylko w kompilacjach debugowania. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

W przypadku C++aplikacji natywnych opcja **Edytuj i Kontynuuj** wymaga użycia opcji `/INCREMENTAL`. Aby uzyskać więcej informacji na temat wymagań C++funkcji w programie, zobacz ten [wpis w blogu](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) i [Edytuj iC++Kontynuuj ()](../debugger/edit-and-continue-visual-cpp.md).

**Aby włączyć lub wyłączyć funkcję Edytuj i Kontynuuj:**

1. Jeśli jesteś w sesji debugowania, Zatrzymaj debugowanie (**debuguj** > **Zatrzymaj debugowanie** lub **SHIFT**+**F5**).

1. W obszarze **narzędzia**@no__t-**1 opcje** > (lub **Debuguj** > **Opcje**) > **debugowanie** > **Ogólne**, wybierz opcję **Edytuj i Kontynuuj** w okienku po prawej stronie.

    > [!NOTE]
    > Jeśli IntelliTrace jest włączona i zbierasz zarówno zdarzenia IntelliTrace, jak i informacje o wywołaniu, funkcja Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [IntelliTrace](../debugger/intellitrace.md).

1. W C++ przypadku kodu upewnij się, że jest zaznaczona opcja **Włącz natywne edytowanie i kontynuowanie** , a następnie ustaw opcje dodatkowe:
    - **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)**

      W przypadku wybrania tej możliwości program Visual Studio automatycznie kompiluje i stosuje zmiany kodu w przypadku kontynuowania debugowania ze stanu przerwania. W przeciwnym razie można wybrać opcję zastosowania zmian przy użyciu @no__t **debugowania**-1.**Zastosuj zmiany kodu**.

    - **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**

      W przypadku wybrania tej informacji program wyświetla ostrzeżenia o nieodświeżonym kodzie.

1. Kliknij przycisk **OK**.
