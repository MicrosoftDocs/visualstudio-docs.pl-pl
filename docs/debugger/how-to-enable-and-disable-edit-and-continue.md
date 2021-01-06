---
title: Włącz i Wyłącz funkcję Edytuj i Kontynuuj | Microsoft Docs
description: Informacje na temat sposobu wyłączania i włączania opcji Edytuj i Kontynuuj w programie Visual Studio w czasie projektowania. Polecenie Edytuj i Kontynuuj działa tylko w kompilacjach debugowania.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 02356a407acc97b60f05641359c32305323f162e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903535"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Instrukcje: Włączanie i wyłączanie Edytuj i Kontynuuj (C#, VB, C++)

Można wyłączyć lub włączyć opcję **Edytuj i Kontynuuj** w oknie dialogowym **Opcje** programu Visual Studio w czasie projektowania. Polecenie **Edytuj i Kontynuuj** działa tylko w kompilacjach debugowania. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

W przypadku natywnego języka C++ **Edycja i kontynuowanie** wymaga użycia `/INCREMENTAL` opcji. Aby uzyskać więcej informacji na temat wymagań funkcji w języku C++, zobacz ten [wpis w blogu](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) i [Edytuj i Kontynuuj (C++)](../debugger/edit-and-continue-visual-cpp.md).

**Aby włączyć lub wyłączyć funkcję Edytuj i Kontynuuj:**

1. Jeśli jesteś w sesji debugowania, Zatrzymaj debugowanie (**Debuguj**  >  **Zatrzymaj debugowanie** lub **SHIFT** + **F5**).

1. W obszarze **Narzędzia**  >  **Opcje** > ( lub  >  **Opcje** debugowania) > **debugowania**  >  **Ogólne** wybierz opcję **Edytuj i Kontynuuj** w okienku po prawej stronie.

    > [!NOTE]
    > Jeśli IntelliTrace jest włączona i zbierasz zarówno zdarzenia IntelliTrace, jak i informacje o wywołaniu, funkcja Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [IntelliTrace](../debugger/intellitrace.md).

1. W przypadku kodu C++ upewnij się, że jest zaznaczona opcja **Włącz natywne edytowanie i kontynuowanie** , a następnie ustaw opcje dodatkowe:
    - **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)**

      W przypadku wybrania tej możliwości program Visual Studio automatycznie kompiluje i stosuje zmiany kodu w przypadku kontynuowania debugowania ze stanu przerwania. W przeciwnym razie możesz zastosować zmiany, używając **debugowania**  >  **zmiany kodu**.

    - **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**

      W przypadku wybrania tej informacji program wyświetla ostrzeżenia o nieodświeżonym kodzie.

1. Kliknij przycisk **OK**.
