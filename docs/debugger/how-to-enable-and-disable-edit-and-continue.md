---
title: 'Instrukcje: Włączanie i wyłączanie funkcji Edytuj i Kontynuuj | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: b0a10d720e911f80aa5ef7b4a42f521bfd9c31bd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070414"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Instrukcje: Włączanie i wyłączanie funkcji Edytuj i Kontynuuj (C#, VB, C++)

Można wyłączyć lub włączyć **Edytuj i Kontynuuj** w programie Visual Studio **opcje** okno dialogowe, w czasie projektowania. **Edytuj i Kontynuuj** kompilacje działa tylko podczas debugowania. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

Dla natywnych języka C++ **Edytuj i Kontynuuj** wymaga użycia `/INCREMENTAL` opcji. Aby uzyskać więcej informacji na temat wymagań funkcji w języku C++, zobacz ten [wpis w blogu](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) i [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

**Aby włączyć lub wyłączyć Edytuj i Kontynuuj:**

1. Jeśli pracujesz w sesji debugowania, Zatrzymaj debugowanie (**debugowania** > **Zatrzymaj debugowanie** lub **Shift**+**F5**) .

1. W **narzędzia** > **opcje** > (lub **debugowania** > **opcje**) > **debugowania**  >  **Ogólne**, wybierz opcję **Edytuj i Kontynuuj** w okienku po prawej stronie.

    > [!NOTE]
    >  Jeśli zbieranie zdarzeń IntelliTrace i informacje o wywołaniach funkcji IntelliTrace jest włączony, Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [IntelliTrace](../debugger/intellitrace.md).

1. Dla kodu C++, upewnij się, **Włączanie natywnego Edytuj i Kontynuuj** jest zaznaczone, a także określ dodatkowe opcje:
    - **Zastosuj zmiany przy kontynuowaniu (tylko natywne)**

      Jeśli zaznaczone, Visual Studio automatycznie kompiluje i ma zastosowanie zmian w kodzie, jeśli będziesz kontynuować debugowanie od teraz w stanie przerwania. W przeciwnym razie użytkownik może zastosować zmiany, przy użyciu **debugowania** > **zastosowanie zmian kodu**.

    - **Ostrzeżenie o nieodświeżonym kodzie (tylko natywne)**

      Jeśli zaznaczone, umożliwia ostrzeżenia o nieodświeżonym kodzie.

1. Kliknij przycisk **OK**.
