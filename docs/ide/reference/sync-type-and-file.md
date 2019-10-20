---
title: Zmień nazwę pliku na zgodną z typem
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
ms.openlocfilehash: 640df80d1763a2e942b4e38b34e72e5bd4a2a7fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645206"
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

## <a name="how-to"></a>Instrukcje

1. Podświetl lub umieść kursor tekstu w nazwie typu do zsynchronizowania:

   - C#:

       ![Wyróżniony kod —C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/synctype-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę pliku na *TypeName*. cs** z okna podręcznego okno podglądu, gdzie *TypeName* jest nazwą wybranego typu.
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Zmień nazwę typu na _filename_**  w oknie podręcznym okna podglądu, gdzie *filename* jest nazwą bieżącego pliku.
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę pliku na *TypeName*. cs** z okna podręcznego okno podglądu, gdzie *TypeName* jest nazwą wybranego typu.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zmień nazwę typu na _filename_**  w menu podręcznym okna podglądu, gdzie *filename* jest nazwą bieżącego pliku.

   Zmieniono nazwę typu lub pliku.

   - C#: W poniższym przykładzie nazwa **MyClass.cs** pliku została zmieniona na **MyNewClass.cs** , aby odpowiadała nazwie typu.

       ![Wynik wbudowanyC#](media/synctype-result-cs.png)

   - Visual Basic: w poniższym przykładzie zmieniono nazwę pliku **Employee. vb** na **Person. vb** na zgodną z nazwą typu.

       ![Visual Basic wyników wbudowanych](media/synctype-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
