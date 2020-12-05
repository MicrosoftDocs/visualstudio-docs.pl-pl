---
title: Generuj klasę lub typ
description: Dowiedz się, jak za pomocą menu szybkie akcje i refaktoryzacje natychmiast wygenerować kod dla klasy lub typu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fe38cacf9f33acfac6b1634b6be6a8a3e45de820
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617542"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generowanie klasy lub typu w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla klasy lub typu.

**Kiedy:** Wprowadzasz nową klasę lub typ i chcesz prawidłowo zadeklarować ją automatycznie.

**Dlaczego:** Można zadeklarować klasę lub typ przed użyciem, jednak ta funkcja spowoduje automatyczne wygenerowanie klasy lub typu.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata. Czerwona zygzakowata wskazuje klasę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/class-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij pozycję ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd klasy](media/class-preview-cs.png)

3. Wybierz jedną z opcji z menu rozwijanego:

   - Generuj klasę "*TypeName*" w nowym pliku &mdash; tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*. cs/. vb
   - Generuj klasę "*TypeName*" &mdash; tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   - Generuj zagnieżdżoną klasę "*TypeName*" &mdash; tworzy klasę o nazwie *TypeName* zagnieżdżoną w bieżącej klasie.
   - Generuj nowy typ... &mdash; Tworzy nową klasę lub strukturę ze wszystkimi określonymi właściwościami.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

4. W przypadku wybrania pozycji **Generuj nowy typ** zostanie otwarte okno dialogowe **generowanie typu** . Skonfiguruj ułatwienia dostępu, rodzaj i lokalizację nowego typu.

   ![Generuj typ](media/class-newtype-cs.png)

   Zaznaczenie | Opis
   --- | ---
   Dostęp | Ustaw typ na *domyślny*, *wewnętrzny* lub *publiczny* .
   Rodzaj | Tę wartość można ustawić jako *klasę* lub *strukturę*.
   Nazwa | Nie można jej zmienić i będzie to nazwa, która została już wpisana.
   Project | Jeśli w rozwiązaniu istnieje wiele projektów, możesz wybrać miejsce, w którym ma się pojawić Klasa/struktura.
   Nazwa pliku | Można utworzyć nowy plik lub dodać typ do istniejącego pliku.

Tworzona jest Klasa lub struktura. Dla języka C# tworzony jest również Konstruktor.

- C#

   ![Generuj wynik klasy C #](media/class-result-cs.png)

- Visual Basic

   ![Generuj wynik klasy VB](media/class-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
