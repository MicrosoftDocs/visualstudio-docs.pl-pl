---
title: Generowanie klasy lub typu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595634"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generowanie klasy lub typu w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla klasy lub typu.

**Kiedy:** Wprowadzasz nową klasę lub typ i chcesz poprawnie zadeklarować, automatycznie.

**Dlaczego?** Można zadeklarować klasy lub typu przed użyciem go, jednak ta funkcja wygeneruje klasę lub typ automatycznie.

## <a name="how-to"></a>Porady

1. Umieść kursor na linii, w której znajduje się czerwona falista. Czerwony squiggle wskazuje klasę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/class-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

      ![Generowanie podglądu klasy](media/class-preview-cs.png)

3. Wybierz jedną z opcji z menu rozwijanego:

   - Generowanie klasy '*TypeName*' w nowym pliku&mdash;Tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*.cs/.vb
   - Generuj klasę&mdash;'*TypeName*' Tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   - Generowanie klasy zagnieżdżonej '*TypeName*'&mdash;Tworzy klasę o nazwie *TypeName* zagnieżdżoną wewnątrz bieżącej klasy.
   - Wygeneruj nowy typ... &mdash;Tworzy nową klasę lub strukturę ze wszystkimi właściwościami, które określisz.

   > [!TIP]
   > Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.

4. Jeśli wybrano pozycję **Generowanie nowego elementu typu,** zostanie otwarte okno dialogowe **Generowanie typu.** Skonfiguruj dostępność, rodzaj i lokalizację nowego typu.

   ![Generowanie typu](media/class-newtype-cs.png)

   Wybór | Opis
   --- | ---
   Dostęp | Ustaw typ jako *domyślny,* *wewnętrzny* lub *publiczny.*
   Rodzaj | Można to ustawić jako *klasę* lub *strukturę*.
   Nazwa | Nie można tego zmienić i będzie to nazwa, którą już wpisano.
   Project | Jeśli istnieje wiele projektów w rozwiązaniu, można wybrać, gdzie mają być dostępne klasy/struktury.
   Nazwa pliku | Można utworzyć nowy plik lub dodać ten typ do istniejącego pliku.

Klasa lub struktura jest tworzona. Dla języka C#jest również tworzony konstruktor.

- C#

   ![Generowanie wyniku klasy C #](media/class-result-cs.png)

- Visual Basic

   ![Generowanie wyników klasy VB](media/class-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
