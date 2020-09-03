---
title: Zmień nazwę pliku na zgodną z typem
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594399"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchronizuj typ do nazwy pliku lub nazwę pliku z refaktoryzacją typu

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Pozwala zmienić nazwę typu na zgodną z nazwą pliku lub zmienić nazwę pliku na zgodną z typem, który zawiera.

**Kiedy:** Zmieniono nazwę pliku lub typ i nie zaktualizowano jeszcze odpowiedniego pliku lub typu do dopasowania.

**Dlaczego:** Umieszczenie typu w pliku o innej nazwie lub odwrotnie, trudno znaleźć to, czego szukasz. Zmiana nazwy typu lub nazwy pliku, kod jest bardziej czytelny i łatwiejszy do nawigowania.

> [!NOTE]
> Ta refaktoryzacja nie jest jeszcze dostępna dla projektów .NET Standard i .NET Core.

## <a name="how-to"></a>Porady

1. Podświetl lub umieść kursor tekstu w nazwie typu do zsynchronizowania:

   - C#:

       ![Wyróżniony kod — C #](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/synctype-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę pliku na *TypeName*. cs** z okna podręcznego okno podglądu, gdzie *TypeName* jest nazwą wybranego typu.
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Zmień nazwę typu na _filename_ ** w oknie podręcznym okna podglądu, gdzie *filename* jest nazwą bieżącego pliku.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę pliku na *TypeName*. cs** z okna podręcznego okno podglądu, gdzie *TypeName* jest nazwą wybranego typu.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę typu na _filename_ ** w menu podręcznym okna podglądu, gdzie *filename* jest nazwą bieżącego pliku.

   Zmieniono nazwę typu lub pliku.

   - C#: w poniższym przykładzie nazwa **MyClass.cs** pliku została zmieniona na **MyNewClass.cs** , aby odpowiadała nazwie typu.

       ![Wynik w wierszu C #](media/synctype-result-cs.png)

   - Visual Basic: w poniższym przykładzie zmieniono nazwę pliku **Employee. vb** na **Person. vb** na zgodną z nazwą typu.

       ![Visual Basic wyników wbudowanych](media/synctype-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
