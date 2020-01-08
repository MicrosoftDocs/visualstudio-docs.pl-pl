---
title: Krok 4. układ formularza przy użyciu kontrolki TableLayoutPanel
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f4ca58506e99331c48b33717903d1925874912
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590023"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. układ formularza przy użyciu kontrolki TableLayoutPanel

W tym kroku dodasz kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> do formularza. TableLayoutPanel pomaga prawidłowo wyrównywać kontrolki w formularzu, który zostanie dodany później.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Jak określić układ formularza przy użyciu kontrolki TableLayoutPanel

1. Po lewej stronie środowiska IDE programu Visual Studio wybierz kartę **Przybornik** . (możesz też wybrać polecenie **Wyświetl** > **przybornika** z paska menu lub naciśnij **klawisze CTRL**+**Alt**+**X**).

1. Wybierz mały trójkątny symbol obok grupy **kontenery** , aby go otworzyć, jak pokazano na poniższym zrzucie ekranu.

     ](../ide/media/express_toolbox.png) grupy kontenerów ![<br>
*Grupa* ***kontenerów***

1. Kontrolki, takie jak przyciski, pola wyboru i etykiety, można dodawać do formularza. Kliknij dwukrotnie formant TableLayoutPanel w **przyborniku**. (Możesz też przeciągnąć kontrolkę z przybornika na formularz). Gdy to zrobisz, IDE dodaje formant TableLayoutPanel do formularza, jak pokazano na poniższym zrzucie ekranu.

     ![formantu TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel*** — *formant*

    > [!NOTE]
    > Po dodaniu TableLayoutPanel, jeśli okno jest wyświetlane w formularzu z tytułem **zadania TableLayoutPanel**, Wybierz dowolne miejsce wewnątrz formularza, aby je zamknąć. Więcej informacji na temat tego okna znajdziesz w dalszej części tego samouczka.

     Zauważ, jak **Przybornik** rozszerza się, aby pokryć formularz po wybraniu jego karty, i jest zamykany po wybraniu dowolnego miejsca poza nim. Jest to funkcja Autoukrywanie w środowisku IDE. Można ją włączyć lub wyłączyć dla dowolnego systemu Windows, wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączyć funkcję Autoukrywanie i zablokować ją na miejscu. Ikona pinezki jest wyświetlana w następujący sposób.

     ikona pinezki ![](../ide/media/express_pushpintoolbox.png)<br>
*Ikona* ***pinezki***

1. Upewnij się, że TableLayoutPanel jest zaznaczone, wybierając ją. Można sprawdzić, jaki formant jest zaznaczony, przeglądając listę rozwijaną w górnej części okna **Właściwości** , jak pokazano na poniższym zrzucie ekranu.

     ![okno Właściwości pokazujący formant TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
*Okno* właściwości z *kontrolką* ***TableLayoutPanel***

1. Wybierz przycisk **alfabetyczny** na pasku narzędzi w oknie **Właściwości** . Spowoduje to posortowanie listy właściwości w oknie **Właściwości** w kolejności alfabetycznej, co ułatwia lokalizowanie właściwości w tym samouczku.

1. Selektor kontrolki jest listą rozwijaną u góry okna **Właściwości** . W tym przykładzie pokazuje, że wybrano kontrolkę o nazwie `tableLayoutPanel1`. Możesz wybrać kontrolki, wybierając obszar w **Projektant formularzy systemu Windows** lub wybierając z selektora kontrolki.

   Teraz, gdy wybrano TableLayoutPanel, Znajdź właściwość **Dock** i wybierz opcję **Dock**, która powinna mieć wartość **none**. Zauważ, że obok wartości zostanie wyświetlona strzałka listy rozwijanej. Wybierz strzałkę, a następnie wybierz przycisk **wypełnienie** (duży przycisk w środku), jak pokazano na poniższym zrzucie ekranu.

     ![okno Właściwości z wybranym kolorem Wypełnij](../ide/media/express_docktable.png)<br>
Okno ***Właściwości*** *z* *wybranym* ***wypełnieniem***

     *Dokowanie* w programie Visual Studio odnosi się do sytuacji, gdy okno jest dołączone do innego okna lub obszaru w IDE. Na przykład okno **Właściwości** może być oddokowane&mdash;, które jest, niedołączone i nieruchome w programie Visual Studio&mdash;lub może być zadokowane względem **Eksplorator rozwiązań**.

1. Po ustawieniu właściwości **Dock dokowania** na **wypełnienie**należy zauważyć, że panel wypełnia cały formularz. Jeśli zmienisz rozmiar formularza ponownie, TableLayoutPanel zostanie zadokowane i dopasowuje się do dopasowania.

    > [!NOTE]
    > TableLayoutPanel działa jak tabela w Microsoft Office Word: zawiera wiersze i kolumny, a pojedyncza komórka może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jedną kontrolkę (na przykład przycisk, pole wyboru lub etykietę). Obiekt TableLayoutPanel powinien mieć kontrolkę <xref:System.Windows.Forms.PictureBox> obejmującą cały górny wiersz, kontrolkę <xref:System.Windows.Forms.CheckBox> w swojej lewej dolnej komórce i cztery <xref:System.Windows.Forms.Button> kontrolki w swojej prawej dolnej komórce.

1. Obecnie TableLayoutPanel ma dwa wiersze o równym rozmiarze i dwie kolumny o równym rozmiarze. Zmieńmy ich rozmiar, aby górny wiersz i prawa kolumna były znacznie większe. W **Projektant formularzy systemu Windows**wybierz TableLayoutPanel. W prawym górnym rogu znajduje się mały czarny trójkątny przycisk, który pojawia się w następujący sposób.

     przycisk ![Trójkąty](../ide/media/express_iconblacktriangle.gif)<br>
*Przycisk* ***trójkąta***

     Ten przycisk oznacza, że Kontrolka zawiera zadania, które ułatwiają automatyczne ustawianie jego właściwości.

1. Wybierz Trójkąt, aby wyświetlić listę zadań kontrolki, jak pokazano na poniższym zrzucie ekranu.

     ![zadania TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
*Zadania* TableLayoutPanel

1. Wybierz zadanie **Edytuj wiersze i kolumny** , aby wyświetlić okno **Style kolumn i wierszy** . Wybierz pozycję **Kolumna1**, a następnie ustaw jej rozmiar na 15 procent, upewniając się, że jest zaznaczony przycisk **procent** i wprowadzając wartość **15** w polu **procent** . (To jest formant <xref:System.Windows.Forms.NumericUpDown>, którego będziesz używać w kolejnym samouczku). Wybierz pozycję **Kolumna2** i ustaw ją na 85 procent. Nie wybieraj jeszcze przycisku **OK** , ponieważ okno zostanie zamknięte. (Ale jeśli to zrobisz, możesz otworzyć go ponownie za pomocą listy zadań).

     ![kolumny TableLayoutPanel i style wierszy](../ide/media/vs_tablelayoutpanel_setup.png)<br>
Kolumny ***TableLayoutPanel*** *i style wierszy*

1. Z listy rozwijanej **Pokaż** w górnej części okna **Style kolumn i wierszy** wybierz pozycję **wiersze**. Ustaw wartość **row1** na 90% i **Row2** na 10 procent.

1. Wybierz **OK** przycisku. Obiekt TableLayoutPanel powinien teraz mieć duży górny wiersz, mały dolny wiersz, małą lewą kolumnę i dużą prawą kolumnę. (Możesz zmienić rozmiar wierszy i kolumn w TableLayoutPanel, wybierając **tableLayoutPanel1** w formularzu, a następnie przeciągając obramowania wierszy i kolumn).

     ![Form1 ze zmienionym rozmiarem TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png)<br>
***Formularz Form1*** *(przeglądarka obrazów) ze zmienionym rozmiarem* ***TableLayoutPanel***

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 5: Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md)** .

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Ustawianie właściwości formularza](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
