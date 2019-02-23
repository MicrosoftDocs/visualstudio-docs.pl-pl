---
title: Zastosowanie zmian w trybie przerwania z funkcją Edytuj i Kontynuuj | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d885cdc3d4321737541cd178d546c37e71ce42b7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684185"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Instrukcje: Zastosowanie zmian w trybie przerwania za pomocą Edytuj i Kontynuuj (Visual Basic)
Edytuj i Kontynuuj umożliwia edytowanie kodu w trybie przerwania, a następnie kontynuuj bez zatrzymywania i ponownego uruchamiania wykonywania.

Ograniczenia dotyczące używania Edytuj i Kontynuuj podczas debugowania, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Do edycji kodu w trybie przerwania

1.  Tryb przerwania, wykonując jedną z następujących czynności:

    -   Ustaw punkt przerwania w kodzie, a następnie wybierz **Rozpocznij debugowanie** z **debugowania** menu i zaczekaj, aż ją w dotarciu do punktu przerwania.

         —lub—

    -   Rozpocznij debugowanie, a następnie wybierz **Przerwij wszystko** z **debugowania** menu.

         —lub—

    -   Gdy wystąpi wyjątek, wybierz pozycję **Włącz edytowanie** na **Asystenta wyjątków**.

2.  Wprowadź wszelkie zmiany kodu żądaną i objęty pomocą techniczną.

     Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    >  Jeśli spróbujesz kodu, zmiany, które nie jest dozwolona przez Edytuj i Kontynuuj, zmiany będą podkreślone purpurowa linia falista i zadania pojawi się na liście zadań. Nie można kontynuować wykonywania kodu, chyba że można cofnąć zmiany kodu niedozwolony.

3.  Na **debugowania** menu, kliknij przycisk **Kontynuuj** można wznowić wykonywania.

     Kod wykonuje teraz stosowane edycji włączone do projektu.

## <a name="see-also"></a>Zobacz też
- [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
