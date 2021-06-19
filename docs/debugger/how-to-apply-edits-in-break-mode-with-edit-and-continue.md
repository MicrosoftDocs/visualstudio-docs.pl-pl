---
title: Stosowanie edycji w trybie przerwania za pomocą edytowania i | Microsoft Docs
description: Zobacz, jak używać funkcji Edytuj i kontynuuj, aby edytować kod Visual Basic w trybie przerwania. Istnieją różne sposoby wprowadzania trybu przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e62c6a7a6e30bac6d054f3e5484498047426d96d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386803"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>How to: Apply Edits in Break Mode with Edit and Continue (Jak zastosować edycje w trybie przerwania przy użyciu edytowania i Visual Basic)
Możesz użyć funkcji Edytuj i kontynuuj, aby edytować kod w trybie przerwania, a następnie kontynuować bez zatrzymywania i ponownego uruchamiania wykonywania.

Aby uzyskać informacje o ograniczeniach dotyczących używania funkcji Edytuj i kontynuuj podczas debugowania, zobacz Obsługiwane zmiany kodu [(C# i Visual Basic).](../debugger/supported-code-changes-csharp.md)

### <a name="to-edit-code-in-break-mode"></a>Aby edytować kod w trybie przerwania

1. Wprowadź tryb przerwania, wykonując jedną z następujących czynności:

    - Ustaw punkt przerwania w kodzie, a następnie wybierz pozycję **Rozpocznij** debugowanie z menu **Debugowanie** i poczekaj, aż aplikacja trafi punkt przerwania.

         -lub-

    - Rozpocznij debugowanie, a następnie wybierz **pozycję Przerwij wszystko** z menu **Debugowanie.**

         -lub-

    - W przypadku wystąpienia wyjątku wybierz pozycję **Włącz edytowanie w** **Asystencie wyjątków.**

2. Wprowadzaj wszelkie żądane i obsługiwane zmiany kodu.

     Aby uzyskać więcej informacji, zobacz [Obsługiwane zmiany kodu (C# i Visual Basic).](../debugger/supported-code-changes-csharp.md)

    > [!NOTE]
    > Jeśli spróbujesz wprowadzić zmianę kodu, która nie jest dozwolona przez pozycję Edytuj i kontynuuj, edycja zostanie podkreślona fioletową linią falistą, a zadanie pojawi się w Lista zadań. Nie będzie można kontynuować wykonywania kodu, chyba że cofniesz niedozwoloną zmianę kodu.

3. W menu **Debugowanie** kliknij pozycję **Kontynuuj,** aby wznowić wykonywanie.

     Kod jest teraz wykonywany z zastosowanymi edytować włączonymi do projektu.

## <a name="see-also"></a>Zobacz też
- [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
