---
title: 'Krok 5: Dodawanie odniesień do etykiet'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de89d7194425e1a8cba9e11f2734372d80b256b3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579328"
---
# <a name="step-5-add-label-references"></a>Krok 5: Dodawanie odniesień do etykiet
Program musi śledzić, który label kontroluje gracz wybiera. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledzić, który formant etykiety jest wybrany jako pierwszy, a który jest wybierany jako drugi za pomocą *zmiennych referencyjnych*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Te zmienne referencyjne wyglądają podobnie do instrukcji używanych <xref:System.Collections.Generic.List%601> wcześniej do <xref:System.Random> dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiekty, obiekty i obiekty) do formularza. Jednak te instrukcje nie powodują dwa dodatkowe Label formantów do `new` wyświetlenia w formularzu, ponieważ nie ma słowa kluczowego używane w jednej z dwóch instrukcji. Bez `new` słowa kluczowego nie jest tworzony żaden obiekt. Dlatego `firstClicked` i `secondClicked` są nazywane zmienne referencyjne: Po prostu śledzić (lub, odnoszą się do) Label obiektów.

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość `null` zastrzeżoną: `Nothing` w języku C# i w języku Visual Basic. Tak więc, gdy program `firstClicked` uruchamia, zarówno i `secondClicked` są ustawione na `null` lub `Nothing`, co oznacza, że zmienne nie są śledzenie niczego.

2. Zmodyfikuj <xref:System.Windows.Forms.Control.Click> program `firstClicked` obsługi zdarzeń, aby użyć nowej zmiennej referencyjnej. Usuń ostatnią instrukcję `label_Click()` w metodzie obsługi zdarzeń`clickedLabel.ForeColor = Color.Black;` `if` ( ) i zastąp ją następującą instrukcją. (Upewnij się, że dodasz `if` komentarz i całe oświadczenie).

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program jest już śledzenie pierwszej etykiety, że gracz `firstClicked` wybrał, więc `null` nie jest `Nothing` równa w języku C# lub visual basic. Gdy `if` instrukcja `firstClicked` sprawdza, czy jest `null` równa `Nothing`lub , stwierdza, że nie jest i nie wykonuje `if` instrukcji w instrukcji. Tak więc tylko pierwsza wybrana ikona zmienia kolor na czarny, a pozostałe ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Gra w dopasowywanie pokazująca jedną ikonę](../ide/media/express_tut4step5.png)<br/>
***Pasująca gra*** *z jedną ikoną*

     Naprawisz tę sytuację w następnym kroku samouczka, dodając kontrolkę **timera.**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 4: Dodawanie programu obsługi zdarzeń Click do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).
