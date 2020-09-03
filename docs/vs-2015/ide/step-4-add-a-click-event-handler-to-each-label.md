---
title: Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b78a1757586dfaf6087711eaf1ed6001155a3b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671803"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gra w dopasowywanie działa w następujący sposób:

1. Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.

2. Następnie gracz wybiera inną ukrytą ikonę.

3. Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.

   Aby program umożliwiał pracę w ten sposób, dodaj program obsługi zdarzeń Kliknięcie, który zmienia kolor wybranej etykiety.

### <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać program obsługi zdarzeń Kliknięcie do każdej etykiety

1. Otwórz formularz w programie Windows Forms Designer. W oknie Eksploratora rozwiązań wybierz Form1.cs lub Form1.vb. Na pasku menu wybierz **Widok**, **Projektant**.

2. Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie trzymaj wciśnięty klawisz CTRL, zaznaczając pozostałe etykiety. Pamiętaj, że każda etykieta jest zaznaczona.

3. Wybierz przycisk **zdarzenia** na pasku narzędzi w oknie **Właściwości** , aby wyświetlić stronę **zdarzenia** w oknie **Właściwości** . Przewiń w dół do zdarzenia **kliknij** i wprowadź **label_Click** w polu, jak pokazano na poniższej ilustracji.

     ![Okno właściwości pokazać zdarzenia kliknięcia](../ide/media/express-labelclick.png "Express_labelClick") okno Właściwości pokazać zdarzenia kliknięcia

4. Wybierz klawisz ENTER. IDE dodaje procedurę obsługi zdarzeń kliknięcia o nazwie `label_Click()` do kodu i przechwytuje ją do każdej etykiety w formularzu.

5. Wypełnij resztę kodu w następujący sposób:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]

    > [!NOTE]
    > Jeśli skopiujesz i wkleisz `label_Click()` blok kodu zamiast ręcznie wprowadzić kod, pamiętaj, aby zastąpić istniejący `label_Click()` kod. W przeciwnym razie otrzymasz zduplikowany blok kodu.

    > [!NOTE]
    > Można rozpoznać `object sender` w górnej części programu obsługi zdarzeń jako ten sam użyty w [samouczku 2: Tworzenie samouczka matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md) . Ponieważ podłączyłeś inne zdarzenie Kliknij formantu etykiety do metody obsługi pojedynczego zdarzenia, ta sama metoda jest wywoływana, niezależnie od tego, którą etykietę wybierze użytkownik. Metoda obsługi zdarzeń musi wiedzieć, która etykieta została wybrana, więc używa **nadawcy** nazwy do identyfikacji kontrolki etykieta. Pierwszy wiersz metody informuje program, że nie jest tylko obiektem ogólnym, ale w oddzielnym formancie etykiety i używa nazwy **clickedLabel** w celu uzyskania dostępu do właściwości i metod etykiet.

     Ta metoda najpierw sprawdza, czy **clickedLabel** został pomyślnie przekonwertowany (rzutowany) z obiektu na kontrolkę etykieta. Jeśli nie powiedzie się, ma wartość `null` (C#) lub `Nothing` (Visual Basic) i nie chcesz wykonywać pozostałej części kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety przy użyciu właściwości **ForeColor** etykiety. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (To `return` wykonuje instrukcja: informuje program, aby zatrzymał wykonywanie metody). W przeciwnym razie ikona nie została wybrana, dlatego program zmienia kolor tekstu etykiety na czarny.

6. Na pasku menu wybierz kolejno opcje **plik**, **Zapisz wszystko** , aby zapisać postęp, a następnie na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** , aby uruchomić program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3. przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).
