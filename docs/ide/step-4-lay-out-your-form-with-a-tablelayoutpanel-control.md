---
title: 'Krok 4: Rozmieść formularz za pomocą kontrolki TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579384"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4: Rozmieść formularz za pomocą kontrolki TableLayoutPanel

W tym kroku należy <xref:System.Windows.Forms.TableLayoutPanel> dodać formant do formularza. Panel TableLayout pomaga prawidłowo wyrównać formanty w formularzu, który zostanie dodany później.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Jak ułożyć formularz za pomocą formantu TableLayoutPanel

1. Po lewej stronie środowiska IDE programu Visual Studio wybierz kartę **Przybornik** (alternatywnie wybierz pozycję **Wyświetl** > **przybornik** z paska menu lub naciśnij klawisz **Ctrl**+**Alt**+**X).**

1. Wybierz mały symbol trójkąta obok grupy **Kontenery,** aby go otworzyć, jak pokazano na poniższym zrzucie ekranu.

     ![Grupa Kontenery](../ide/media/express_toolbox.png)<br>
***Grupa Kontenery*** *group*

1. Do formularza można dodawać kontrolki, takie jak przyciski, pola wyboru i etykiety. Kliknij dwukrotnie kontrolkę TableLayoutPanel w **przyborniku**. (Można też przeciągnąć formant z przybornika na formularz). Po wykonaniu tej czynności IDE dodaje TableLayoutPanel formant do formularza, jak pokazano na poniższym zrzucie ekranu.

     ![TableLayoutPanel — formant](../ide/media/express_formtablelayout.png)<br>
***Kontrolka TableLayoutPanel*** *control*

    > [!NOTE]
    > Po dodaniu panelu TableLayoutPanel, jeśli wewnątrz formularza pojawi się okno z tytułem **TableLayoutPanel Tasks,** wybierz dowolne miejsce wewnątrz formularza, aby go zamknąć. Więcej informacji o tym oknie dowiesz się w dalszej części samouczka.

     Zwróć uwagę, jak **przybornik** rozszerza się, aby pokryć formularz po wybraniu jego karty, i zamyka się po wybraniu dowolnego miejsca poza nim. To funkcja Auto Hide w IDE. Można go włączyć lub wyłączyć dla dowolnego okna, wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączyć funkcję Auto Hide i zablokować ją na swoim miejscu. Ikona pinezmy jest wyświetlana w następujący sposób.

     ![Ikona pinezci](../ide/media/express_pushpintoolbox.png)<br>
***Ikona pinezci*** *icon*

1. Upewnij się, że tablelayoutpanel jest zaznaczony, wybierając go. Formant jest zaznaczony, patrząc na listę rozwijaną u góry okna **Właściwości,** jak pokazano na poniższym zrzucie ekranu.

     ![Okno Właściwości z kontrolką TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
Okno ***Właściwości*** *z kontrolką* ***TableLayoutPanel*** *control*

1. Wybierz przycisk **Alfabetyczny** na pasku narzędzi w oknie **Właściwości.** To sortuje listę właściwości w oknie **Właściwości** w kolejności alfabetycznej, co ułatwia zlokalizowanie właściwości w tym samouczku.

1. Selektor formantu jest listą rozwijaną u góry okna **Właściwości.** W tym przykładzie pokazuje, `tableLayoutPanel1` że formant wywoływany jest zaznaczony. Formanty można wybrać, wybierając obszar w **programie Windows Forms Designer** lub wybierając z selektora formantu.

   Teraz, gdy wybrano TableLayoutPanel, znajdź **Dock** właściwości i wybierz **Dock**, który powinien być ustawiony na **Brak**. Należy zauważyć, że obok wartości pojawi się strzałka rozwijana. Wybierz strzałkę, a następnie wybierz przycisk **Wypełnienie** (duży przycisk w środku), jak pokazano na poniższym zrzucie ekranu.

     ![Okno Właściwości z zaznaczoną wybraną wybraną wybraną wybran](../ide/media/express_docktable.png)<br>
Okno ***Właściwości*** *z zaznaczoną* *wybraną wybraną wybraną wybran* ***Fill***

     *Dokowanie* w programie Visual Studio odnosi się do gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład okno **Właściwości** można oddokować,&mdash;czyli niepodłączone i swobodnie&mdash;pływające w programie Visual Studio lub może być zadokowane względem **Eksploratora rozwiązań.**

1. Po ustawieniu właściwości TableLayoutPanel **Dock** na **Wypełnienie**należy zauważyć, że panel wypełnia cały formularz. Jeśli ponownie zmienić rozmiar formularza, TableLayoutPanel pozostaje zadokowany i zmienia rozmiar, aby dopasować.

    > [!NOTE]
    > Panel TableLayoutpanel działa jak tabela w programie Microsoft Office Word: ma wiersze i kolumny, a pojedyncza komórka może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jeden formant (np. przycisk, pole wyboru lub etykieta). Panel TableLayout powinien mieć <xref:System.Windows.Forms.PictureBox> formant obejmujący cały <xref:System.Windows.Forms.CheckBox> górny wiersz, formant w <xref:System.Windows.Forms.Button> lewej dolnej komórce i cztery formanty w prawej dolnej komórce.

1. Obecnie TableLayoutPanel ma dwa wiersze o równym rozmiarze i dwie kolumny o równym rozmiarze. Zmienić ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W **programie Windows Forms Designer**wybierz panel TableLayoutPanel. W prawym górnym rogu znajduje się mały czarny przycisk trójkąta, który pojawia się w następujący sposób.

     ![Przycisk Trójkąt](../ide/media/express_iconblacktriangle.gif)<br>
***Przycisk Trójkąt*** *button*

     Ten przycisk wskazuje, że formant ma zadania, które pomagają ustawić jego właściwości automatycznie.

1. Wybierz trójkąt, aby wyświetlić listę zadań formantu, jak pokazano na poniższym zrzucie ekranu.

     ![Zadania TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Zadania TableLayoutPanel*** *tasks*

1. Wybierz zadanie **Edytuj wiersze i kolumny,** aby wyświetlić okno **Style kolumn i wierszy.** Wybierz **kolumnę1**i ustaw jej rozmiar na 15 procent, upewniając się, że przycisk **Procent** jest zaznaczony i wprowadzając **15** w polu **Procent.** (To jest <xref:System.Windows.Forms.NumericUpDown> formant, który będzie używany w późniejszym samouczku.) Wybierz **kolumnę2** i ustaw ją na 85 procent. Nie wybieraj jeszcze przycisku **OK,** ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz ponownie otworzyć go przy użyciu listy zadań).

     ![Style kolumn i wierszy TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
Style *kolumn i wierszy* ***TableLayoutPanel***

1. Z listy rozwijanej **Pokaż** u góry okna **Style kolumn i wierszy** wybierz pozycję **Wiersze**. Ustaw **wiersz1** na 90 procent i **Row2** na 10 procent.

1. Wybierz przycisk **OK.** Panel TableLayout Powinien mieć teraz duży górny rząd, mały dolny rząd, małą lewą kolumnę i dużą prawą kolumnę. (Można zmienić rozmiar wierszy i kolumn w tableLayoutPanel, wybierając **tableLayoutPanel1** w formularzu, a następnie przeciągając jego obramowania wierszy i kolumn).

     ![Formularz1 z panelem TableLayoutPanel o przesunienia](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** (Picture Viewer) z panelem ***TableLayoutPanel*** *o przesunienia*

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 5: Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
