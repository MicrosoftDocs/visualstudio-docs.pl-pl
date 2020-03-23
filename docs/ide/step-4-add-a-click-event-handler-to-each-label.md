---
title: 'Krok 4: Dodaj program obsługi zdarzeń kliknięć do każdej etykiety'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7049271dddb4e763bf5ecb3760358bdd63e38df5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579349"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Dodaj program obsługi zdarzeń kliknięć do każdej etykiety

Gra w dopasowywanie działa w następujący sposób:

1. Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.

2. Następnie gracz wybiera inną ukrytą ikonę.

3. Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.

   Aby program działał w ten sposób, <xref:System.Windows.Forms.Control.Click> należy dodać program obsługi zdarzeń, który zmienia kolor wybranej etykiety.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać program obsługi zdarzeń kliknięcia do każdej etykiety

1. Otwórz formularz w **Projektancie formularzy systemu Windows**. W **Eksploratorze rozwiązań**wybierz *opcję Form1.cs* lub *Form1.vb*. Na pasku menu wybierz pozycję **Wyświetl** > **projektanta**.

2. Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie przytrzymaj klawisz **Ctrl,** wybierając każdą z pozostałych etykiet, aby je zaznaczyć. Pamiętaj, że każda etykieta jest zaznaczona.

3. Wybierz przycisk **Zdarzenia** na pasku narzędzi w oknie **Właściwości,** aby wyświetlić stronę **Zdarzenia** w oknie **Właściwości.** Przewiń w dół do zdarzenia **Kliknij** i wprowadź **label_Click** w polu, jak pokazano na poniższym zrzucie ekranu.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_labelclick.png)

4. Wybierz klawisz **Enter.** IDE dodaje `Click` program obsługi `label_Click()` zdarzeń wywoływany do kodu i przyłącza go do każdej z etykiet w formularzu.

5. Wypełnij resztę kodu w następujący sposób:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Jeśli kopiujesz i `label_Click()` wklejasz blok kodu, zamiast ręcznie wprowadzać `label_Click()` kod, pamiętaj, aby zastąpić istniejący kod. W przeciwnym razie otrzymasz zduplikowany blok kodu.

    > [!NOTE]
    > Możesz rozpoznać `object sender` w górnej części programu obsługi zdarzeń jako ten sam, który jest używany w [samouczku 2: Tworzenie samouczka quizu matematycznego](../ide/tutorial-2-create-a-timed-math-quiz.md) z czasem. Ponieważ podłączyć różne zdarzenia kliknięcia kontroli etykiety do metody obsługi pojedynczego zdarzenia, ta sama metoda jest wywoływana bez względu na to, która etykieta użytkownik wybiera. Metoda obsługi zdarzeń musi wiedzieć, która etykieta została wybrana, więc używa nazwy `sender` do identyfikowania formantu etykiety. Pierwszy wiersz metody informuje program, że nie jest to tylko obiekt ogólny, ale w szczególności formant etykiety i że używa nazwy, `clickedLabel` aby uzyskać dostęp do właściwości i metod etykiety.

     Ta metoda najpierw `clickedLabel` sprawdza, czy został pomyślnie przekonwertowany (rzutowany) z obiektu na formant etykiety. Jeśli nie powiedzie się, ma `null` wartość `Nothing` (C#) lub (Visual Basic) i nie chcesz wykonać pozostałą część kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety przy użyciu właściwości **ForeColor** etykiety. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (To, co `return` instrukcja nie: Mówi programowi, aby zatrzymać wykonywanie metody.) W przeciwnym razie ikona nie została wybrana, więc program zmieni kolor tekstu etykiety na czarny.

6. Na pasku menu wybierz **pozycję Zapisz** > **wszystko,** aby zapisać swoje postępy, a następnie na pasku menu wybierz pozycję **Debugowanie** > **startowe debugowania,** aby uruchomić program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 3: Przypisywanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).
