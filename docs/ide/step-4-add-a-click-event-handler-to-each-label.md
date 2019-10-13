---
title: Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b60f9bb1fffb9fb36311ad3fda504c1ff2260ce
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289687"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety

Gra w dopasowywanie działa w następujący sposób:

1. Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.

2. Następnie gracz wybiera inną ukrytą ikonę.

3. Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.

   Aby program działał w ten sposób, Dodaj program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click>, który zmienia kolor wybranej etykiety.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać program obsługi zdarzeń kliknięcia do każdej etykiety

1. Otwórz formularz w **Projektant formularzy systemu Windows**. W **Eksplorator rozwiązań**wybierz pozycję *Form1.cs* lub *Form1. vb*. Na pasku menu wybierz **widok** > **Designer**.

2. Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie naciśnij i przytrzymaj klawisz **Ctrl** podczas wybierania każdej z pozostałych etykiet, aby je wybrać. Pamiętaj, że każda etykieta jest zaznaczona.

3. Wybierz przycisk **zdarzenia** na pasku narzędzi w oknie **Właściwości** , aby wyświetlić stronę **zdarzenia** w oknie **Właściwości** . Przewiń w dół do zdarzenia kliknij, a **następnie** wprowadź **label_Click** w polu, jak pokazano na poniższej ilustracji.

     ![Okno Właściwości pokazujące zdarzenie Kliknij](../ide/media/express_labelclick.png)

4. Wybierz klawisz **Enter** . IDE dodaje procedurę obsługi zdarzeń `Click` o nazwie `label_Click()` do kodu i przechwytuje ją do każdej etykiety w formularzu.

5. Wypełnij resztę kodu w następujący sposób:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>0Programming — kontrola języka dla dokumentacji docs. Microsoft. com @ no__t-1 @no__t

    > [!NOTE]
    > Jeśli skopiujesz i wkleisz blok kodu `label_Click()` zamiast ręcznie wprowadzić kod, pamiętaj, aby zastąpić istniejący kod `label_Click()`. W przeciwnym razie otrzymasz zduplikowany blok kodu.

    > [!NOTE]
    > Możesz rozpoznać `object sender` w górnej części programu obsługi zdarzeń jako ten sam użyty w [Tutorial 2: Utwórz Quiz matematyczny z terminami @ no__t-0. Ponieważ podłączono różne zdarzenia klikania kontrolek do pojedynczej metody obsługi zdarzeń, taka sama metoda jest wywoływana niezależnie od tego, która etykieta zostanie wybrana przez użytkownika. Metoda obsługi zdarzeń musi wiedzieć, która etykieta została wybrana, więc używa nazwy `sender`, aby zidentyfikować kontrolkę etykieta. Pierwszy wiersz metody instruuje program, że nie jest tylko obiektem ogólnym, ale w oddzielnym formancie etykiety i używa nazwy `clickedLabel` w celu uzyskania dostępu do właściwości i metod etykiet.

     Ta metoda najpierw sprawdza, czy `clickedLabel` został pomyślnie przekonwertowany (rzutowany) z obiektu na kontrolkę etykieta. Jeśli nie powiedzie się, ma wartość `null` (C#) lub `Nothing` (Visual Basic) i nie chcesz wykonywać pozostałej części kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety przy użyciu właściwości **ForeColor** etykiety. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (To jest instrukcja `return`: Mówi, że program zatrzymał wykonywanie metody.) W przeciwnym razie ikona nie została wybrana, więc program zmienia kolor tekstu etykiety na czarny.

6. Na pasku menu wybierz kolejno opcje **plik** > **Zapisz wszystko** , aby zapisać postęp, a następnie na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie** , aby uruchomić program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Step 5: Dodaj odwołania do etykiet @ no__t-0.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Step 3: Przypisz losowo ikonę do każdej etykiety @ no__t-0.
