---
title: Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety
description: Dowiedz się, jak dodać program obsługi zdarzeń kliknięcia do każdej etykiety.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f37d0f89ad5124956198df1bde94bdb6cf54f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950682"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety

Gra w dopasowywanie działa w następujący sposób:

1. Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.

2. Następnie gracz wybiera inną ukrytą ikonę.

3. Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.

   Aby program działał w ten sposób, należy dodać <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, który zmienia kolor wybranej etykiety.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać program obsługi zdarzeń kliknięcia do każdej etykiety

1. Otwórz formularz w **Projektant formularzy systemu Windows**. W **Eksplorator rozwiązań** wybierz pozycję *Form1.cs* lub *Form1. vb*. Na pasku menu wybierz polecenie Projektant **widoków**  >  .

2. Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie naciśnij i przytrzymaj klawisz **Ctrl** podczas wybierania każdej z pozostałych etykiet, aby je wybrać. Pamiętaj, że każda etykieta jest zaznaczona.

3. Wybierz przycisk **zdarzenia** na pasku narzędzi w oknie **Właściwości** , aby wyświetlić stronę **zdarzenia** w oknie **Właściwości** . Przewiń w dół do zdarzenia **kliknij** i wprowadź **label_Click** w polu, jak pokazano na poniższym zrzucie ekranu.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_labelclick.png)

4. Wybierz klawisz **Enter** . IDE dodaje `Click` procedurę obsługi zdarzeń o nazwie `label_Click()` do kodu i przechwytuje ją do każdej etykiety w formularzu.

5. Wypełnij resztę kodu w następujący sposób:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Jeśli skopiujesz i wkleisz `label_Click()` blok kodu zamiast ręcznie wprowadzić kod, pamiętaj, aby zastąpić istniejący `label_Click()` kod. W przeciwnym razie otrzymasz zduplikowany blok kodu.

    > [!NOTE]
    > Można rozpoznać `object sender` w górnej części programu obsługi zdarzeń jako ten sam użyty w [samouczku 2: Tworzenie samouczka matematycznego z limitem czasu](../ide/tutorial-2-create-a-timed-math-quiz.md) . Ponieważ podłączono różne zdarzenia klikania kontrolek do pojedynczej metody obsługi zdarzeń, taka sama metoda jest wywoływana niezależnie od tego, która etykieta zostanie wybrana przez użytkownika. Metoda obsługi zdarzeń musi wiedzieć, która etykieta została wybrana, więc używa nazwy `sender` do identyfikowania kontrolki etykieta. Pierwszy wiersz metody nakazuje programowi, że nie jest to tylko obiekt generyczny, ale w oddzielnym formancie etykiety i że używa nazwy `clickedLabel` w celu uzyskania dostępu do właściwości i metod etykiet.

     Ta metoda najpierw sprawdza `clickedLabel` , czy pomyślnie przeprowadzono konwersję (CAST) z obiektu do kontrolki etykieta. Jeśli nie powiedzie się, ma wartość `null` (C#) lub `Nothing` (Visual Basic) i nie chcesz wykonywać pozostałej części kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety przy użyciu właściwości **ForeColor** etykiety. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (To `return` wykonuje instrukcja: informuje program, aby zatrzymał wykonywanie metody). W przeciwnym razie ikona nie została wybrana, dlatego program zmienia kolor tekstu etykiety na czarny.

6. Na pasku menu wybierz kolejno opcje **plik**  >  **Zapisz wszystko** , aby zapisać postęp, a następnie na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** , aby uruchomić program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3. przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).
