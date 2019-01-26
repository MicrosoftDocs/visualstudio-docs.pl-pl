---
title: Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a5c208c1ee73808622e30834c1dadb3dfdde497
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961442"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety

Gra w dopasowywanie działa w następujący sposób:

1. Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.

2. Następnie gracz wybiera inną ukrytą ikonę.

3. Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.

   Aby uzyskać program umożliwiał pracę w ten sposób, należy dodać <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, który zmienia kolor wybranej etykiety.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać obsługę zdarzeń kliknięcia do każdej etykiety

1.  Otwórz formularz w **Windows Forms Designer**. W **Eksploratora rozwiązań**, wybierz *Form1.cs* lub *Form1.vb*. Na pasku menu wybierz **widoku** > **projektanta**.

2.  Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie przytrzymaj naciśnięty **Ctrl** klucza wciśnięty pozostałe etykiety, aby je wybrać. Pamiętaj, że każda etykieta jest zaznaczona.

3.  Wybierz **zdarzenia** przycisk na pasku narzędzi w **właściwości** okna, aby wyświetlić **zdarzenia** strony w **właściwości** okna. Przewiń w dół do **kliknij** zdarzeń, a następnie wprowadź **label_Click** w polu, jak pokazano na poniższej ilustracji.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_labelclick.png)

4.  Wybierz **Enter** klucza. IDE dodaje `Click` wywołuje program obsługi zdarzeń `label_Click()` z kodem i przyczepia go do każdej etykiety w formularzu.

5.  Wypełnij resztę kodu w następujący sposób:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

    > [!NOTE]
    > Jeśli skopiujesz i wkleisz `label_Click()` blok kodu, a nie wprowadzasz kod ręcznie, upewnij się zastąpić istniejącą `label_Click()` kodu. W przeciwnym razie otrzymasz zduplikowany blok kodu.

    > [!NOTE]
    > Być może rozpoznajesz `object sender` w górnej części programu obsługi zdarzeń jako ten sam używany w [samouczek 2: Utwórz quiz matematyczny](../ide/tutorial-2-create-a-timed-math-quiz.md) samouczka. Możesz podłączone kontrolą inną etykietę zdarzenia do metody obsługi pojedynczego zdarzenia kliknięcia, wywoływana jest metoda ten sam, niezależnie od tego, którą etykietę wybierze użytkownik. Metoda obsługi zdarzeń musi wiedzieć, którą etykietę wybrano, więc używa nazwy `sender` Aby zidentyfikować formant etykiety. Pierwszy wiersz metody mówi programowi, że nie jest obiekt rodzajowy, ale konkretnie formant etykiety i że używa on nazwy `clickedLabel` dostęp do właściwości i metod etykiety.

     Metoda ta najpierw sprawdza, czy `clickedLabel` został pomyślnie przekonwertowany (rzutowany) z obiektu na formant etykiety. Jeśli nie, ma wartość `null` (C#) lub `Nothing` (Visual Basic), a nie chcesz wykonać pozostałej części kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety za pomocą etykiety **ForeColor** właściwości. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (Właśnie to `return` wykonuje instrukcja: Mówi programowi, aby zatrzymał wykonywanie metody.) W przeciwnym razie ikona nie została wybrana, więc program zmienia kolor tekstu etykiety na czarny.

6.  Na pasku menu wybierz **pliku** > **Zapisz wszystko** Aby zapisać postęp, a następnie na pasku menu wybierz **debugowania** > **Start Debugowanie** Aby uruchomić program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).
