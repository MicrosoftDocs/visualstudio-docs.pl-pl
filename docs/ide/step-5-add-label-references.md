---
title: Krok 5. Dodawanie odwołań do etykiet
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc94660debb3d4668fb5d9d50e68466fe7631e5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109442"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić które formanty etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będą teraz przechowywać informacje o który formant etykiety został wybrany jako pierwszy, a który jako drugi przy użyciu *odwoływać się do zmiennych*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Te zmienne odwołania wyglądają podobnie do instrukcji było wcześniej używane do dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiektów <xref:System.Collections.Generic.List%601> obiekty, i <xref:System.Random> obiektów) do formularza. Jednakże te instrukcje nie powodują dwa dodatkowe formanty etykiet do wyświetlane w formularzu, ponieważ nie istnieje żadne `new` słowa kluczowego w jednym z dwóch instrukcji. Bez `new` — słowo kluczowe, zostanie utworzony żaden obiekt. Dlatego `firstClicked` i `secondClicked` są nazywane zmiennymi odwołania: Oni po prostu śledzić (lub odwoływać się do) etykiety obiektów.

     Jeśli zmienna nie jest rejestrowanie informacji o obiekcie, jest ustawiona na specjalną zarezerwowaną wartość: `null` w języku Visual C# i `Nothing` w języku Visual Basic. Tak, po uruchomieniu programu, zarówno `firstClicked` i `secondClicked` są ustawione na `null` lub `Nothing`, co oznacza, że zmienne nie są utrzymywanie o wszystkim.

2. Zmodyfikuj swoje <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby użyć nowego `firstClicked` zmienną odwołania. Usuń ostatnią instrukcję w `label_Click()` metody obsługi zdarzeń (`clickedLabel.ForeColor = Color.Black;`) i zastąp go wartością `if` kolejnej instrukcji. (Należy dołączyć komentarz oraz całą `if` instrukcja.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program jest już rejestrowanie informacji o pierwszą etykietę, którą wybrał gracz, więc `firstClicked` nie jest równa `null` w języku Visual C# lub `Nothing` w języku Visual Basic. Gdy Twoje `if` instrukcji kontroli `firstClicked` do określenia, czy jest równa `null` lub `Nothing`, stwierdzi, że nie jest, a więc nie wykonuje instrukcji w `if` instrukcji. Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Gra zgodne pokazująca jedną ikonę](../ide/media/express_tut4step5.png)
**gra w dopasowywanie** pokazująca jedną ikonę

     Dodając naprawisz tę sytuację w następnym kroku samouczka **czasomierza** kontroli.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodaj czasomierz](../ide/step-6-add-a-timer.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).
