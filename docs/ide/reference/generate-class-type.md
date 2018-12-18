---
title: Generowanie klasy lub typu
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4f7d722669ddf51715b21ddaf1f253fb0668dfaa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065477"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generowanie klasy lub typu w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** pozwala natychmiast generowania kodu dla klasy lub typu.

**Kiedy:** wprowadzenie nowej klasy lub typu i aby poprawnie Zadeklaruj go, automatycznie.

**Dlaczego:** można zadeklarować klasy lub typu przed użyciem, ale ta funkcja zostanie wygenerowana klasa lub wpisz automatycznie.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w wierszu gdzie znajduje się czerwona fala. Czerwona fala wskazuje klasę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C#](media/class-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony Kod VB](media/class-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) Ikona wyświetlana.
      - Kliknij ikonę ![Żarówka](media/bulb-cs.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

      ![Generowanie klasy (wersja zapoznawcza)](media/class-preview-cs.png)

3. Z menu rozwijanego wybierz jedną z opcji:

   - Generowanie klasy*TypeName*"w nowym pliku&mdash;tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*.cs/.vb
   - Generowanie klasy*TypeName*"&mdash;tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   - Generowanie klasy zagnieżdżonej*TypeName*"&mdash;tworzy klasę o nazwie *TypeName* zagnieżdżonych w bieżącej klasie.
   - Generuj nowy typ... &mdash;Tworzy nowe klasy lub struktury, ze wszystkimi właściwościami, można określić.

   > [!TIP]
   > Użyj **podgląd zmian** link w dolnej części okna podglądu [Aby wyświetlić wszystkie zmiany](../../ide/preview-changes.md) , zostaną wprowadzone przed dokonaniem wyboru.

4. W przypadku wybrania **Generuj nowy typ** elementu **Generowanie typu** zostanie otwarte okno dialogowe. Skonfiguruj dostępność, rodzaj i lokalizację nowego typu.

   ![Generuj typ](media/class-newtype-cs.png)

   Wybór | Opis
   --- | ---
   Access | Ustaw typ mieć *domyślne*, *wewnętrzne* lub *publicznych* dostępu.
   rodzaj | To może być ustawiona jako *klasy* lub *struktury*.
   Nazwa | Nie można zmienić i będzie można już wpisana nazwa.
   Projekt | W przypadku wielu projektów w rozwiązaniu, wybierz polecenie, w której chcesz klasie/strukturze na żywo.
   Nazwa pliku | Można utworzyć nowy plik, lub typu można dodać do istniejącego pliku.

Klasy lub struktury jest tworzony. Aby uzyskać C#, tworzona jest również konstruktora.

- C#

   ![Generowanie klasy wynikC#](media/class-result-cs.png)

- Visual Basic

   ![Generowanie klasy wynik VB](media/class-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)