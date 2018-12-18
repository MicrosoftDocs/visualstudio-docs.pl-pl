---
title: Zmień nazwę, nazwa_pliku, aby dopasować typ
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bfc1a88091fa30bceea15a3f8e1b78df5cc7a87c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054790"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Wpisz nazwę pliku lub nazwę pliku do refaktoryzacji typu synchronizacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** pozwala zmienić nazwę typu, aby dopasować nazwę pliku lub zmienić nazwę pliku, który będzie pasował do typu, które zawiera.

**Kiedy:** zmieniono nazwę pliku lub typ i nie zostały jeszcze zaktualizowane odpowiedniego pliku lub typ do dopasowania.

**Dlaczego:** umieszczenie typu w pliku o innej nazwie lub odwrotnie, go, które są trudne do znalezienia, czego szukasz. Zmieniając typ lub nazwa pliku, kod staje się bardziej czytelny i łatwiejszą nawigacją.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu do synchronizowania:

   - C#:

       ![Wyróżniony kod-C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/synctype-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** do wyzwalacza **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę pliku do *TypeName*.cs** z okna podręcznego okna (wersja zapoznawcza), gdzie *TypeName* to nazwa wybranego typu.
      - Naciśnij klawisz **Ctrl**+**.** do wyzwalacza **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zmienić nazwę typu do _Filename_**  z okna podręcznego okna (wersja zapoznawcza), gdzie *Filename* jest nazwa bieżącego pliku.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę pliku do *TypeName*.cs** z okna podręcznego okna (wersja zapoznawcza), gdzie *TypeName* to nazwa wybranego typu.
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zmienić nazwę typu do _Filename_**  z okna podręcznego okna (wersja zapoznawcza), gdzie  *Nazwa pliku* jest nazwa bieżącego pliku.

   Typ lub pliku została zmieniona.

   - C#: W przykładzie poniżej plik **MyClass.cs** została zmieniona na **MyNewClass.cs** Period z nazwą typu.

       ![Wynik wbudowaneC#](media/synctype-result-cs.png)

   - Visual Basic: W przykładzie poniżej plik **Employee.vb** została zmieniona na **Person.vb** Period z nazwą typu.

       ![Wynik wbudowanego Visual Basic](media/synctype-result-vb.png)

> ! [UWAGA] Ta Refaktoryzacja nie jest jeszcze dostępne dla projektów .NET Standard i .NET Core.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
