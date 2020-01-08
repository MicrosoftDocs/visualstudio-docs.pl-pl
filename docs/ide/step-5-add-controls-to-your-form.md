---
title: Krok 5. Dodawanie kontrolek do formularza
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77b8fc1f1f9f34a5b19756b7cf1370522f74075e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589971"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5. Dodawanie kontrolek do formularza

W tym kroku dodasz kontrolki, takie jak kontrolka <xref:System.Windows.Forms.PictureBox> i kontrolka <xref:System.Windows.Forms.CheckBox> do formularza. Następnie możesz dodać kontrolki <xref:System.Windows.Forms.Button> do formularza.

## <a name="how-to-add-controls-to-your-form"></a>Jak dodać kontrolki do formularza

1. Wybierz kartę **Przybornik** po lewej stronie środowiska IDE programu Visual Studio (lub naciśnij klawisz **Ctrl**+**Alt**+**X**), a następnie rozwiń grupę **formanty wspólne** . Pokazuje najczęściej używane kontrolki, które są widoczne w formularzach.

1. Kliknij dwukrotnie element **PictureBox** , aby dodać formant PictureBox do formularza. Ponieważ TableLayoutPanel jest zadokowane, aby wypełnić formularz, IDE dodaje formant PictureBox do pierwszej pustej komórki (górny lewy róg).

1. Wybierz nowy formant **PictureBox** , aby go zaznaczyć, a następnie wybierz czarny trójkąt w nowym formancie PictureBox, aby wyświetlić jego listę zadań, jak pokazano na poniższym zrzucie ekranu.

    ![zadania PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox * * * *zadania**

    > [!NOTE]
    > Jeśli przypadkowo dodasz niewłaściwy typ kontrolki do TableLayoutPanel, możesz go usunąć. Kliknij prawym przyciskiem myszy kontrolkę, a następnie wybierz polecenie **Usuń** w menu kontekstowym. Można również usunąć kontrolki z formularza przy użyciu paska menu. Na pasku menu wybierz polecenie **edytuj** > **cofnij**lub **Edytuj** > **Usuń**.

1. W menu **zadania PictureBox** w formancie **PictureBox** wybierz łącze **Dock w kontenerze nadrzędnym** . Spowoduje to automatyczne ustawienie właściwości **Dock dokowania** do **wypełnienia**. Aby to zobaczyć, wybierz formant **PictureBox** , aby go zaznaczyć, przejdź do okna **Właściwości** i upewnij się, że właściwość **Dock** jest ustawiona na **Fill**.

1. Ustaw element PictureBox w obu kolumnach, zmieniając jego właściwość **ColumnSpan** . W elemencie **PictureBox**wybierz formant **PictureBox** i ustaw jego właściwość **ColumnSpan** na **2**. Ponadto, gdy element PictureBox jest pusty, chcesz wyświetlić pustą ramkę. Ustaw właściwość **BorderStyle** na **Fixed3D**.

    > [!NOTE]
    > Jeśli właściwość **ColumnSpan** nie jest widoczna dla elementu PictureBox, prawdopodobnie element PictureBox został dodany do formularza zamiast TableLayoutPanel. Aby rozwiązać ten problem, wybierz element **PictureBox**, usuń go, wybierz **TableLayoutPanel**, a następnie Dodaj nowy PictureBox.

1. Wybierz **TableLayoutPanel** w formularzu, a następnie Dodaj kontrolkę pola wyboru do formularza. Kliknij dwukrotnie element **CheckBox** w **przyborniku** , aby dodać nową kontrolkę CheckBox do następnej wolnej komórki w tabeli. Ponieważ element PictureBox przyjmuje pierwsze dwie komórki w TableLayoutPanel, formant CheckBox zostanie dodany do lewej dolnej komórki. Wybierz właściwość **Text** i wpisz **ciąg Rozciągnij**, jak pokazano na poniższej ilustracji.

    ![kontrolka TextBox z właściwością rozciągania](../ide/media/express_pictureviewercheckbox.png)<br/>***TextBox*** — *formant z* *właściwością* ***rozciągania***

1. Wybierz **TableLayoutPanel** w formularzu, a następnie przejdź do grupy **kontenery** w **przyborniku** (gdzie masz formant TableLayoutPanel), a następnie kliknij dwukrotnie element **FlowLayoutPanel** , aby dodać nową kontrolkę do ostatniej komórki (prawy dolny). Następnie zadokuj FlowLayoutPanel w TableLayoutPanel. Możesz to zrobić, wybierając pozycję **Dock w kontenerze nadrzędnym** na liście zadań czarny trójkąta FlowLayoutPanel lub ustawiając właściwość **Dock** FlowLayoutPanel na **Fill**.

    > [!NOTE]
    > <xref:System.Windows.Forms.FlowLayoutPanel> jest kontenerem, który rozmieszcza inne kontrolki w wierszu, jeden po drugim. Zmiana rozmiaru FlowLayoutPanel powoduje, że wszystkie kontrolki są układane w jednym wierszu, jeśli ma to miejsce. W przeciwnym razie Rozmieść je w wierszach, jeden na drugim. <br/><br/>W tym miejscu będziesz używać FlowLayoutPanel do przechowywania czterech przycisków. Jeśli przyciski są układane na drugim, podczas dodawania ich, przed dodaniem przycisków upewnij się, że wybrano FlowLayoutPanel. <br/><br/>(Zazwyczaj każda komórka zawiera tylko jeden formant. W tym przykładzie Dolna prawa komórka TableLayoutPanel zawiera cztery kontrolki przycisku. Dlaczego?  Ponieważ FlowLayoutPanel jest kontrolką kontenera, która jest kontrolką w komórce, która zawiera inne kontrolki.

## <a name="to-add-buttons"></a>Aby dodać przyciski

1. Wybierz nowo dodany FlowLayoutPanel. Przejdź do obszaru **wspólne kontrolki** w **przyborniku** i kliknij dwukrotnie element **Button** , aby dodać kontrolkę przycisku o nazwie **Button1** do FlowLayoutPanel. Powtarzaj, aby dodać inny przycisk. IDE Określa, że istnieje już przycisk o nazwie **Button1** i wywołuje następną **Button2**.

1. Zazwyczaj należy dodać inne przyciski przy użyciu **przybornika**. Tym razem wybierz pozycję **Button2**, a następnie na pasku menu wybierz polecenie **Edytuj** > **Kopiuj** (lub naciśnij klawisz **Ctrl**+**C**). Następnie wybierz pozycję **edytuj** > **Wklej** na pasku menu (lub naciśnij klawisz **Ctrl**+**V**), aby wkleić kopię przycisku. Teraz wklej je ponownie. Należy zauważyć, że IDE dodaje **button3** i **button4** do FlowLayoutPanel.

    > [!NOTE]
    > Można kopiować i wklejać dowolną kontrolkę. Nazwy IDE i umieszczają w sposób logiczny nowe kontrolki. W przypadku wklejenia kontrolki do kontenera IDE wybiera następne miejsce logiczne dla umieszczania.

1. Wybierz pierwszy przycisk i ustaw jego właściwość **Text** , aby **wyświetlić obraz**. Następnie ustaw właściwości **tekst** dla kolejnych trzech przycisków, aby **wyczyścić obraz**, **Ustaw kolor tła**i **Zamknij**.

1. Zmień rozmiar przycisków i rozmieść je tak, aby były wyrównane do prawej strony panelu. Wybierz **FlowLayoutPanel** i przyjrzyj się jego właściwości **FlowDirection** . Zmień to ustawienie na wartość **RightToLeft**.

   Przyciski powinny być wyrównane do prawej strony komórki i odwrotnie w kolejności, w której przycisk **Pokaż obraz** znajduje się po prawej stronie.

    > [!NOTE]
    > Jeśli przyciski są nadal w niewłaściwej kolejności, możesz przeciągnąć przyciski wokół FlowLayoutPanel, aby zmienić ich kolejność w dowolnej kolejności. Możesz wybrać przycisk i przeciągnąć go w lewo lub w prawo.

1. Wybierz przycisk **Zamknij** , aby go zaznaczyć. Aby wybrać pozostałe przyciski w tym samym czasie, naciśnij i przytrzymaj klawisz **Ctrl** i wybierz je.

   Po wybraniu wszystkich przycisków przejdź do okna **Właściwości** i przewiń do właściwości **AutoSize** . Ta właściwość nakazuje przyciskowi automatyczną zmianę rozmiaru w celu dopasowania do całego tekstu. Ustaw dla niego **wartość true**.

   Przyciski powinny mieć teraz rozmiar prawidłowy i być w odpowiedniej kolejności. (Pod warunkiem, że wszystkie cztery przyciski są zaznaczone, można zmienić wszystkie cztery właściwości **autorozmiaru** w tym samym czasie). Na poniższej ilustracji przedstawiono cztery przyciski.

    ![Podgląd obrazów z czterema przyciskami](../ide/media/express_autosize.png)<br/>***Przeglądarka obrazów*** *z czterema przyciskami*

1. Teraz ponownie uruchom program, aby zobaczyć zmiany.

   Zauważ, że przyciski i pole wyboru nie wykonują jeszcze&mdash;, ale wkrótce.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

* Aby przejść do następnego kroku samouczka, zobacz **[krok 6. nazwa kontrolek przycisku](../ide/step-6-name-your-button-controls.md)** .

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4. układ formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
