---
title: Krok 5. Dodawanie odwołań do etykiet
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fbe9b0005ce190eda6a88dea2f6b5f80890743c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562942"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić, które kontrolki etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledził, który formant Etykieta jest wybierany jako pierwszy, a który jest wybierany drugi przy użyciu *zmiennych odwołania*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>Kontrolka języka ![Programming dla Docs.Microsoft.com ](../ide/media/docs-programming-language-control.png)

     Te zmienne odwołania wyglądają podobnie do instrukcji użytych wcześniej do dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiektów, obiektów <xref:System.Collections.Generic.List%601> i obiektów <xref:System.Random>) do formularza. Jednak te instrukcje nie powodują, że dwie kontrolki dodatkowej etykiety są wyświetlane w formularzu, ponieważ nie ma słowa kluczowego `new` użytego w żadnej z dwóch instrukcji. Bez słowa kluczowego `new`, żaden obiekt nie jest tworzony. Dlatego `firstClicked` i `secondClicked` są nazywane zmiennymi odwołania: tylko śledzą obiekty etykiet (lub odwołują się do nich).

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość zarezerwowaną: `null` w C# i `Nothing` w Visual Basic. Tak więc, gdy program zostanie uruchomiony, zarówno `firstClicked`, jak i `secondClicked` są ustawione na `null` lub `Nothing`, co oznacza, że zmienne nie śledzą żadnych elementów.

2. Zmodyfikuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click>, aby użyć nowej zmiennej odwołania `firstClicked`. Usuń ostatnią instrukcję z metody obsługi zdarzeń `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) i Zastąp ją następującą instrukcją `if`. (Pamiętaj, aby dołączyć komentarz i całą instrukcję `if`).

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program śledzi już pierwszą etykietę, którą wybrał gracz, więc `firstClicked` nie równa się `null` w C# lub `Nothing` w Visual Basic. Gdy instrukcja `if` sprawdza `firstClicked`, aby określić, czy jest równa `null` lub `Nothing`, stwierdza, że nie, i nie wykonuje instrukcji w instrukcji `if`. Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Matching gra pokazująca jedną ikonę ](../ide/media/express_tut4step5.png)<br/>
**Gra w dopasowywanie** pokazująca jedną ikonę

     Tę sytuację należy rozwiązać w następnym kroku samouczka, dodając kontrolkę **czasomierz** .

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).
