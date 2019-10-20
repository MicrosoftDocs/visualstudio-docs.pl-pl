---
title: Krok 5. Dodawanie odwołań do etykiet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671739"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program musi śledzić, które formanty etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledził, który formant Etykieta jest wybierany jako pierwszy, a który jest wybierany drugi przy użyciu *zmiennych odwołania*.

### <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Te zmienne odwołania wyglądają podobnie do instrukcji użytych wcześniej do dodawania obiektów (takich jak `Timer` obiektów, obiektów `List` i obiektów `Random`) do formularza. Jednak te instrukcje nie powodują, że dwie kontrolki dodatkowej etykiety są wyświetlane w formularzu, ponieważ nie ma słowa kluczowego `new` użytego w żadnej z dwóch instrukcji. Bez słowa kluczowego `new`, żaden obiekt nie jest tworzony. Dlatego `firstClicked` i `secondClicked` są nazywane zmiennymi odwołania: tylko śledzą (lub odwołują się do) obiekty `Label`.

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość zarezerwowaną: `null` w wizualizacjach C# i `Nothing` w Visual Basic. Tak więc, gdy program zostanie uruchomiony, zarówno `firstClicked`, jak i `secondClicked` są ustawione na `null` lub `Nothing`, co oznacza, że zmienne nie śledzą żadnych elementów.

2. Zmodyfikuj procedurę obsługi zdarzeń kliknięcia, aby użyć nowej zmiennej odwołania `firstClicked`. Usuń ostatnią instrukcję z metody obsługi zdarzeń `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) i Zastąp ją następującą instrukcją `if`. (Pamiętaj, aby dołączyć komentarz i całą instrukcję `if`).

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program śledzi już pierwszą etykietę, którą wybrał gracz, więc `firstClicked` nie równa się `null` w wizualizacji C# lub `Nothing` w Visual Basic. Gdy instrukcja `if` sprawdza `firstClicked`, aby określić, czy jest równa `null` lub `Nothing`, stwierdza, że nie, i nie wykonuje instrukcji w instrukcji `if`. Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Gra w dopasowywanie pokazująca jedną ikonę](../ide/media/express-tut4step5.png "Express_Tut4Step5") Gra w dopasowywanie pokazująca jedną ikonę

     Tę sytuację należy rozwiązać w następnym kroku samouczka, dodając kontrolkę **czasomierz** .

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).
