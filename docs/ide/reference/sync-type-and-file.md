---
title: Zmienianie nazwy pliku w celu dopasowania do typu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5b7a42a174fecd078e804f2ab3c35fbe442364a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594399"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchronizowanie typu z nazwami plików lub nazwy pliku z refaktoryzacją typu

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia zmianę nazwy typu w celu dopasowania nazwy pliku lub zmianę nazwy pliku w celu dopasowania go do typu.

**Kiedy:** Zmieniono nazwę pliku lub typu i nie zaktualizowano jeszcze odpowiedniego pliku lub typu, aby dopasować go.

**Dlaczego?** Umieszczenie typu w pliku o innej nazwie lub odwrotnie, trudno jest znaleźć to, czego szukasz. Zmieniając nazwę typu lub nazwy pliku, kod staje się bardziej czytelny i łatwiejszy w nawigacji.

> [!NOTE]
> Ta refaktoryzowania nie jest jeszcze dostępna dla projektów .NET Standard i .NET Core.

## <a name="how-to"></a>Porady

1. Wyróżnij lub umieść kursor tekstowy wewnątrz nazwy typu do synchronizacji:

   - C#:

       ![Wyróżniony kod - C #](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/synctype-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania** i wybrać **opcję Zmień nazwę pliku na *TypeName*.cs** z okna podglądu, gdzie *Nazwa type jest* nazwą wybranego typu.
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania** i wybrać **opcję Zmień nazwę typu na Nazwa _pliku_ ** z okna podglądu , gdzie *nazwa pliku* jest nazwą bieżącego pliku.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz **polecenie Zmień nazwę pliku na *TypeName*.cs** w oknie podglądu, gdzie *Nazwa typename* jest nazwą wybranego typu.
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz **polecenie Zmień nazwę typu Nazwa _pliku_ ** w oknie podglądu, gdzie *nazwa pliku* jest nazwą bieżącego pliku.

   Nazwa typu lub pliku została zmieniona.

   - C#: W poniższym przykładzie **nazwa pliku MyClass.cs** została zmieniona na **MyNewClass.cs,** aby dopasować nazwę typu.

       ![Wynik wbudowany C #](media/synctype-result-cs.png)

   - Visual Basic: W poniższym przykładzie plik **Employee.vb** został przemianowany na **Person.vb,** aby dopasować nazwę typu.

       ![Wynik wbudowany Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
