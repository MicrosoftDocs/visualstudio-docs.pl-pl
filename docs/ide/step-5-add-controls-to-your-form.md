---
title: 'Krok 5: Dodawanie kontrolek do formularza'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579362"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5: Dodawanie kontrolek do formularza

W tym kroku należy dodać formanty, takie jak <xref:System.Windows.Forms.PictureBox> formant i <xref:System.Windows.Forms.CheckBox> formant, do formularza. Następnie należy <xref:System.Windows.Forms.Button> dodać formanty do formularza.

## <a name="how-to-add-controls-to-your-form"></a>Jak dodać formanty do formularza

1. Wybierz kartę **Przybornik** po lewej stronie środowiska IDE programu Visual Studio (lub naciśnij klawisz **Ctrl**+**Alt**+**X),** a następnie rozwiń grupę **Typowe formanty.** Spowoduje to wyświetlone najbardziej typowe formanty widoczne w formularzach.

1. Kliknij dwukrotnie element **PictureBox,** aby dodać kontrolkę PictureBox do formularza. Ponieważ TableLayoutPanel jest zadokowany, aby wypełnić formularz, IDE dodaje picturebox kontrolki do pierwszej pustej komórki (w lewym górnym rogu).

1. Wybierz nowy formant **PictureBox,** aby go zaznaczyć, a następnie wybierz czarny trójkąt na nowym formancie PictureBox, aby wyświetlić listę zadań, jak pokazano na poniższym zrzucie ekranu.

    ![Zadania PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox*** *zadania**

    > [!NOTE]
    > Jeśli przypadkowo dodać niewłaściwy typ formantu do TableLayoutPanel, można go usunąć. Kliknij prawym przyciskiem myszy formant, a następnie w menu kontekstowym wybierz polecenie **Usuń.** Formanty można również usunąć z formularza za pomocą paska menu. Na pasku menu wybierz pozycję **Edytuj** > **cofnij**lub **Edytuj** > **usuń**.

1. W menu **Zadania picturebox** z kontrolki **PictureBox** wybierz łącze **Dok w kontenerze nadrzędnym.** Spowoduje to automatyczne ustawienie właściwości **PictureBox Dock** na **Fill**. Aby to zobaczyć, wybierz kontrolkę **PictureBox,** aby ją **zaznaczyć,** przejdź do okna Właściwości i upewnij się, że właściwość **Dock** jest **ustawiona**na Wypełnienie .

1. Upewnij się PictureBox obejmują obie kolumny, zmieniając jego **ColumnSpan** właściwości. W **picturebox**wybierz **picturebox** kontrolki i ustawić jego **ColumnSpan** właściwość **na 2**. Ponadto, gdy PictureBox jest pusty, chcesz pokazać pustą ramkę. Ustaw jego **BorderStyle** właściwość **Fixed3D**.

    > [!NOTE]
    > Jeśli nie widzisz **ColumnSpan** właściwości dla PictureBox, to jest prawdopodobne, że PictureBox został dodany do formularza, a nie TableLayoutPanel. Aby rozwiązać ten problem, wybierz **picturebox**, usuń go, wybierz **TableLayoutPanel**, a następnie dodaj nowy PictureBox.

1. Wybierz **panel TableLayout w** formularzu, a następnie dodaj kontrolkę Pole wyboru do formularza. Kliknij dwukrotnie element **Pola wyboru** w **przyborniku,** aby dodać nowy kontrolkę CheckBox do następnej bezpłatnej komórki w tabeli. Ponieważ PictureBox zajmuje pierwsze dwie komórki w TableLayoutPanel, CheckBox formant jest dodawany do lewej dolnej komórki. Wybierz **właściwość Tekst** i wpisz wyraz **Rozciągnij**, jak pokazano na poniższej ilustracji.

    ![Formant TextBox z właściwością Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***Formant TextBox*** *z* *właściwością* ***Stretch***

1. Wybierz **TableLayoutPanel** w formularzu, a następnie przejdź do grupy **Kontenery** w **przyborniku** (gdzie masz kontrolkę TableLayoutPanel) i kliknij dwukrotnie element **FlowLayoutPanel,** aby dodać nowy formant do ostatniej komórki (w prawym dolnym rogu). Następnie zadokuj panel FlowLayout w panelu TableLayoutPanel. Można to zrobić, wybierając dock **w kontenerze nadrzędnym** na czarnej liście zadań FlowLayoutPanel lub ustawiając właściwość **Dok w** pliku FlowLayoutPanel na **Wypełnienie**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> jest kontenerem, który rozmieszcza inne formanty w wierszu, jeden po drugim. Podczas ponownego rozmiaru FlowLayoutPanel, określa wszystkie jego formanty w jednym wierszu, jeśli ma na to miejsce. W przeciwnym razie układa je w wierszach, jeden na drugim. <br/><br/>W tym miejscu użyjesz FlowLayoutPanel do przechowywania czterech przycisków. Jeśli przyciski rozmieszczają jeden na drugim podczas dodawania, przed dodaniem przycisków upewnij się, że wybrano panel FlowLayoutPanel. <br/><br/>(Zazwyczaj każda komórka zawiera tylko jedną formant. W tym przykładzie dolna komórka tablelayoutPanel zawiera cztery formanty przycisku. Dlaczego?  Ponieważ FlowLayoutPanel jest formantem kontenera, który jest formantem w komórce, która przechowuje inne formanty.)

## <a name="to-add-buttons"></a>Aby dodać przyciski

1. Wybierz nowy panel FlowLayoutPanel, który został dodany. Przejdź do **pozycji Typowe formanty** w **przyborniku** i kliknij dwukrotnie element **Przycisku,** aby dodać kontrolkę **przycisku** o nazwie button1 do panelu FlowLayoutPanel. Powtórz tę czynność, aby dodać kolejny przycisk. IDE określa, że istnieje już przycisk o nazwie **button1** i wywołuje następny **przycisk2**.

1. Zazwyczaj inne przyciski można dodać za pomocą **przybornika**. Tym razem wybierz **button2**, a następnie z paska menu wybierz polecenie **Edytuj** > **kopię** (lub naciśnij klawisz **Ctrl**+**C**). Następnie wybierz polecenie **Edytuj** > **wklej** z paska menu (lub naciśnij klawisz **Ctrl**+**V),** aby wkleić kopię przycisku. Teraz wklej go ponownie. Należy zauważyć, że IDE dodaje **button3** i **button4** do FlowLayoutPanel.

    > [!NOTE]
    > Można skopiować i wkleić dowolną formant. IDE nazwy i umieszcza nowe formanty w logiczny sposób. Jeśli wklejasz formant do kontenera, IDE wybiera następne miejsce logiczne do umieszczenia.

1. Wybierz pierwszy przycisk i ustaw jego **text** właściwość **pokaż obraz**. Następnie ustaw właściwości **Tekst** następnych trzech przycisków, aby **wyczyścić obraz**, **Ustaw kolor tła**i **Zamknij**.

1. Dodajmy przyciski i ułóżmy je tak, aby były wyrównane do prawej strony panelu. Wybierz **FlowLayoutPanel** i spójrz na jego **Właściwość FlowDirection.** Zmień go tak, aby był ustawiony na **RightToLeft**.

   Przyciski powinny wyrównać się po prawej stronie komórki i odwrócić ich kolejność, tak aby przycisk **Pokaż obraz** znajduje się po prawej stronie.

    > [!NOTE]
    > Jeśli przyciski są nadal w niewłaściwej kolejności, można przeciągnąć przyciski wokół FlowLayoutPanel, aby zmienić ich kolejność. Możesz wybrać przycisk i przeciągnąć go w lewo lub w prawo.

1. Wybierz przycisk **Zamknij,** aby go zaznaczyć. Następnie, aby wybrać resztę przycisków w tym samym czasie, naciśnij i przytrzymaj klawisz **Ctrl** i wybierz je.

   Po wybraniu wszystkich przycisków przejdź do okna **Właściwości** i przewiń w górę do właściwości **AutoSize.** Ta właściwość mówi przycisk, aby automatycznie zmienić rozmiar się dopasować do wszystkich jego tekstu. Ustaw go na **True**.

   Przyciski powinny być teraz odpowiednio dobrane i być w odpowiedniej kolejności. (Tak długo, jak wszystkie cztery przyciski są zaznaczone, można zmienić wszystkie cztery **właściwości AutoSize** w tym samym czasie.) Na poniższej ilustracji przedstawiono cztery przyciski.

    ![Przeglądarka obrazów z czterema przyciskami](../ide/media/express_autosize.png)<br/>***Przeglądarka obrazów*** *z czterema przyciskami*

1. Teraz uruchom program ponownie, aby zobaczyć zmiany.

   Zauważ, że przyciski i pole wyboru&mdash;nie robią jeszcze nic, ale wkrótce.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 6: Nadaj nazw przyciskom .](../ide/step-6-name-your-button-controls.md)**

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 4: Rozmieść formularz za pomocą kontrolki TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
