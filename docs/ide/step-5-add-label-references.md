---
title: Krok 5. Dodawanie odwołań do etykiet
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4580fb2a4c77949825b4e84a7aed7553ceffd981
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079400"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić, które kontrolki etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledził, który formant Etykieta jest wybierany jako pierwszy, a który jest wybierany drugi przy użyciu *zmiennych odwołania*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Te zmienne odwołania wyglądają podobnie do instrukcji użytych wcześniej do dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiekty, <xref:System.Collections.Generic.List%601> obiekty i <xref:System.Random> obiekty) do formularza. Jednak te instrukcje nie powodują, że dwie kontrolki dodatkowej etykiety są wyświetlane w formularzu, ponieważ nie `new` ma słowa kluczowego użytego w żadnej z dwóch instrukcji. `new` Bez słowa kluczowego, żaden obiekt nie jest tworzony. Dlatego `firstClicked` i`secondClicked` są nazywane zmiennymi odwołania: Tylko śledzą obiekty etykiet (lub odwołują się do nich).

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość zastrzeżoną: `null` w wizualizacji C# i `Nothing` w Visual Basic. Tak więc, gdy program zostanie uruchomiony, `firstClicked` obie `secondClicked` i są ustawione `null` na `Nothing`lub, co oznacza, że zmienne nie śledzą niczego.

2. Zmodyfikuj procedurę obsługi `firstClicked` zdarzeń,abyużywała<xref:System.Windows.Forms.Control.Click> nowej zmiennej Reference. Usuń ostatnią instrukcję `label_Click()` z metody obsługi zdarzeń (`clickedLabel.ForeColor = Color.Black;`) `if` i Zastąp ją następującą instrukcją. (Pamiętaj, aby dołączyć komentarz i całą `if` instrukcję).

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program śledzi już pierwszą etykietę, którą wybrał gracz, `firstClicked` więc nie jest równa się `null` w wizualizacji C# ani `Nothing` w Visual Basic. `firstClicked` `Nothing`Gdy instrukcja sprawdzi, `if` czy jest równa lub,stwierdza,żenie,iniewykonujeinstrukcjiwinstrukcji.`null` `if` Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Gra w dopasowywanie z](../ide/media/express_tut4step5.png)
**jedną ikoną** , w której wyświetlana jest jedna ikona

     Tę sytuację należy rozwiązać w następnym kroku samouczka, dodając kontrolkę **czasomierz** .

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6. Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodaj program obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).
