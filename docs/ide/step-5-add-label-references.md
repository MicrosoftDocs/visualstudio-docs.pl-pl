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
ms.openlocfilehash: 0fdcecbdac0a866bd5c6a15a78d8c0ba2a33051a
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289682"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić, które kontrolki etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledził, który formant Etykieta jest wybierany jako pierwszy, a który jest wybierany drugi przy użyciu *zmiennych odwołania*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>0Programming — kontrola języka dla dokumentacji docs. Microsoft. com @ no__t-1 @no__t

     Te zmienne odwołania wyglądają podobnie do instrukcji użytych wcześniej do dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiektów, obiektów <xref:System.Collections.Generic.List%601> i <xref:System.Random> obiektów) do formularza. Jednak te instrukcje nie powodują, że dwie kontrolki dodatkowej etykiety są wyświetlane w formularzu, ponieważ nie istnieje słowo kluczowe `new` użyte w żadnej z dwóch instrukcji. Bez słowa kluczowego `new` nie jest tworzony żaden obiekt. Dlatego `firstClicked` i `secondClicked` są nazywane zmiennymi odwołania: Tylko śledzą obiekty etykiet (lub odwołują się do nich).

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość zarezerwowaną: `null` w wizualizacji C# i `Nothing` w Visual Basic. Tak więc, gdy program zostanie uruchomiony, obie `firstClicked` i `secondClicked` są ustawione na `null` lub `Nothing`, co oznacza, że zmienne nie śledzą niczego.

2. Zmodyfikuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click>, aby użyć nowej zmiennej odwołania `firstClicked`. Usuń ostatnią instrukcję z metody obsługi zdarzeń `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) i Zastąp ją następującą instrukcją `if`. (Pamiętaj, aby dołączyć komentarz i całą instrukcję `if`).

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program śledzi już pierwszą etykietę, którą wybrał gracz, więc `firstClicked` nie równa się `null` w wizualizacji C# lub `Nothing` w Visual Basic. Gdy instrukcja `if` sprawdza `firstClicked`, aby określić, czy jest on równy `null` czy `Nothing`, stwierdza, że nie, i nie wykonuje instrukcji w instrukcji `if`. Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     gra ![Matching z jedną ikoną @ no__t-1<br/>
**Gra w dopasowywanie** pokazująca jedną ikonę

     Tę sytuację należy rozwiązać w następnym kroku samouczka, dodając kontrolkę **czasomierz** .

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Step 6: Dodaj czasomierz @ no__t-0.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Step 4: Dodaj program obsługi zdarzeń kliknięcia do każdej etykiety @ no__t-0.
