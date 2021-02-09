---
title: Zastąp zmienną tymczasową wartością
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby usunąć zmienną tymczasową i zastąpić ją wartością.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ebe062d5dd569ae1d2162ea7334f91d8b82decdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852378"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Wewnętrznie Refaktoryzacja zmiennej tymczasowej

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie zmiennej tymczasowej i zastąpienie jej wartością.

**Kiedy:** Użycie zmiennej tymczasowej sprawia, że kod jest trudniejszy do zrozumienia.

**Dlaczego:** Usunięcie zmiennej tymczasowej może ułatwić odczytywanie kodu.

## <a name="how-to"></a>Porady

1. Zaznacz lub umieść kursor tekstowy wewnątrz zmiennej tymczasowej, która ma zostać zakreślona:

   - C#:

       ![Wyróżniony kod — C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/inline-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

3. W menu podręcznym okna podglądu wybierz pozycję **wbudowana zmienna tymczasowa** .

   Zmienna jest usuwana, a jej zastosowania zostały zastąpione przez wartość zmiennej.

   - C#:

      ![Wynik wbudowany-C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
