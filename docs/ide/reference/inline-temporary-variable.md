---
title: Zastąp zmienną tymczasową wartością
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8b758407dc5500630157050c10f881a6515e1216
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661012"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Wewnętrznie Refaktoryzacja zmiennej tymczasowej

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie zmiennej tymczasowej i zastąpienie jej wartością.

**Kiedy:** Użycie zmiennej tymczasowej sprawia, że kod jest trudniejszy do zrozumienia.

**Dlaczego:** Usunięcie zmiennej tymczasowej może ułatwić odczytywanie kodu.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstowy wewnątrz zmiennej tymczasowej, która ma zostać zakreślona:

   - C#:

       ![Wyróżniony kod —C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/inline-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

3. W menu podręcznym okna podglądu wybierz pozycję **wbudowana zmienna tymczasowa** .

   Zmienna jest usuwana, a jej zastosowania zostały zastąpione przez wartość zmiennej.

   - C#:

      ![Wynik wbudowany —C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)