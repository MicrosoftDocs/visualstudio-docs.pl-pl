---
title: Krok 5. Dodawanie kontrolek do formularza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8c261d903868df887d99c10182ed134c79c552b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671770"
---
# <a name="step-5-add-controls-to-your-form"></a>Krok 5. Dodawanie formantów do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku dodasz kontrolki, takie jak kontrolka `PictureBox` i kontrolka `CheckBox` do formularza. Następnie Dodaj do formularza przyciski.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 2](http://go.microsoft.com/fwlink/?LinkId=205211) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# pliku wideo 2](http://go.microsoft.com/fwlink/?LinkId=205200). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-add-controls-to-your-form"></a>Aby dodać kontrolki do formularza

1. Przejdź do karty przybornik (znajdującej się po lewej stronie środowiska IDE programu Visual Studio) i rozwiń grupę **formanty wspólne** . Pokazuje najczęściej używane kontrolki, które są widoczne w formularzach.

2. Wybierz formant TableLayoutPanel w formularzu. Aby sprawdzić, czy TableLayoutPanel jest zaznaczone, upewnij się, że jego nazwa jest wyświetlana w polu listy rozwijanej w górnej części okna **Właściwości** . Możesz również wybrać kontrolki formularz za pomocą pola listy rozwijanej w górnej części okna **Właściwości** . Wybór kontrolki w ten sposób może być często łatwiejszy niż wybór niewielkiej kontroli z myszą.

3. Kliknij dwukrotnie element **PictureBox** , aby dodać formant PictureBox do formularza. Ponieważ TableLayoutPanel jest zadokowane, aby wypełnić formularz, IDE dodaje formant PictureBox do pierwszej pustej komórki (górny lewy róg).

4. Wybierz nowy formant PictureBox, aby go zaznaczyć, a następnie wybierz czarny trójkąt w nowym formancie PictureBox, aby wyświetlić jego listę zadań, jak pokazano na poniższej ilustracji.

     ![PictureBox — zadania](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks") PictureBox — zadania

    > [!NOTE]
    > Jeśli przypadkowo dodasz niewłaściwy typ kontrolki do TableLayoutPanel, możesz go usunąć. Kliknij prawym przyciskiem myszy kontrolkę, a następnie wybierz polecenie **Usuń** w menu kontekstowym. Można również usunąć kontrolki z formularza przy użyciu paska menu. Na pasku menu wybierz kolejno opcje **Edytuj**, **Cofnij**lub **Edytuj**i **Usuń**.

5. Wybierz łącze **Zadokuj w kontenerze nadrzędnym** . Spowoduje to automatyczne ustawienie właściwości **Dock dokowania** do **wypełnienia**. Aby to zobaczyć, wybierz formant PictureBox, aby go zaznaczyć, przejdź do okna **Właściwości** i upewnij się, że właściwość **Dock** jest ustawiona na **Fill**.

6. Ustaw element PictureBox w obu kolumnach, zmieniając jego właściwość **ColumnSpan** . Wybierz formant PictureBox i ustaw jego właściwość **ColumnSpan** na **2**. Ponadto, gdy element PictureBox jest pusty, chcesz wyświetlić pustą ramkę. Ustaw właściwość **BorderStyle** na **Fixed3D**.

    > [!NOTE]
    > Jeśli właściwość **ColumnSpan** nie jest widoczna dla elementu PictureBox, prawdopodobnie element PictureBox został dodany do formularza zamiast TableLayoutPanel. Aby rozwiązać ten problem, wybierz element PictureBox, usuń go, wybierz TableLayoutPanel, a następnie Dodaj nowy PictureBox.

7. Wybierz TableLayoutPanel w formularzu, a następnie Dodaj kontrolkę **pola wyboru** do formularza. Kliknij dwukrotnie element **CheckBox** w przyborniku, aby dodać nową kontrolkę CheckBox do następnej wolnej komórki w tabeli. Ponieważ element PictureBox przyjmuje pierwsze dwie komórki w TableLayoutPanel, formant CheckBox zostanie dodany do lewej dolnej komórki. Wybierz właściwość **Text** i wpisz **ciąg Rozciągnij**, jak pokazano na poniższej ilustracji.

     ![TextBox — formant z właściwością rozciągania](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox") TextBox — formant z właściwością rozciągania

8. Wybierz TableLayoutPanel w formularzu, a następnie przejdź do grupy **kontenery** w przyborniku (gdzie masz formant TableLayoutPanel), a następnie kliknij dwukrotnie element **FlowLayoutPanel** , aby dodać nową kontrolkę do ostatniej komórki elementu PictureBox (dół z prawej strony. Następnie zadokuj FlowLayoutPanel w elemencie TableLayoutPanel (wybierając pozycję **Dock w kontenerze nadrzędnym** na liście zadań na czarnym trójkącie FlowLayoutPanel) lub ustawiając właściwość **Dock** FlowLayoutPanel na **Fill**.

    > [!NOTE]
    > FlowLayoutPanel jest kontenerem, który rozmieszcza inne kontrolki w wierszach, w kolejności. W przypadku zmiany rozmiaru FlowLayoutPanel, jeśli ma miejsce na rozmieszczenie wszystkich formantów w pojedynczym wierszu, robi to. W przeciwnym razie Rozmieść je w wierszach, jeden na drugim. Będziesz używać FlowLayoutPanel do przechowywania czterech przycisków. Jeśli przyciski układają się po raz pierwszy po dodaniu, upewnij się, że wybrano FlowLayoutPanel przed dodaniem przycisków. Mimo że został wcześniej ustalony, że każda komórka może zawierać tylko jeden formant, Dolna prawa komórka TableLayoutPanel ma cztery kontrolki przycisku. Dzieje się tak, ponieważ w komórce, która zawiera inne kontrolki, można umieścić formant. Ten rodzaj kontrolki nosi nazwę kontenera, a FlowLayoutPanel jest kontenerem.

### <a name="to-add-buttons"></a>Aby dodać przyciski

1. Wybierz nowo dodany FlowLayoutPanel. Przejdź do obszaru **wspólne kontrolki** w przyborniku i kliknij dwukrotnie element **Button** , aby dodać kontrolkę przycisku o nazwie **Button1** do FlowLayoutPanel. Powtarzaj, aby dodać inny przycisk. IDE Określa, że istnieje już przycisk o nazwie **Button1** i wywołuje następną **Button2**.

2. Zazwyczaj należy dodać inne przyciski przy użyciu przybornika. Tym razem wybierz pozycję **Button2**, a następnie na pasku menu wybierz polecenie **Edytuj**, **Kopiuj** (lub naciśnij klawisze CTRL + C). Na pasku menu wybierz polecenie **Edytuj**, **Wklej** (lub naciśnij klawisze CTRL + V), aby wkleić kopię przycisku. Teraz wklej je ponownie. IDE dodał teraz **button3** i **button4** do FlowLayoutPanel.

    > [!NOTE]
    > Można kopiować i wklejać dowolną kontrolkę. Nazwy IDE i umieszczają w sposób logiczny nowe kontrolki. W przypadku wklejenia kontrolki do kontenera IDE wybiera następne miejsce logiczne dla umieszczania.

3. Wybierz pierwszy przycisk i ustaw jego właściwość **Text** , aby **wyświetlić obraz**. Następnie ustaw właściwości **tekst** dla kolejnych trzech przycisków, aby **wyczyścić obraz**, **Ustaw kolor tła**i **Zamknij**.

4. Następnym krokiem jest zmiana rozmiaru przycisków i rozmieszczenie ich w celu ich dopasowania do prawej strony panelu. Wybierz FlowLayoutPanel i przyjrzyj się jego właściwości **FlowDirection** . Zmień to ustawienie na wartość **RightToLeft**. Po wykonaniu tych czynności przyciski powinny być wyrównane do prawej strony komórki i odwrócić ich kolejność, aby przycisk **Pokaż obraz** był po prawej stronie.

    > [!NOTE]
    > Jeśli przyciski są nadal w niewłaściwej kolejności, możesz przeciągnąć przyciski wokół FlowLayoutPanel, aby zmienić ich kolejność w dowolnej kolejności. Możesz wybrać przycisk i przeciągnąć go w lewo lub w prawo.

5. Wybierz przycisk **Zamknij** , aby go zaznaczyć. Przytrzymaj wciśnięty klawisz CTRL i wybierz pozostałe trzy przyciski, aby były zaznaczone. Gdy zaznaczone są wszystkie przyciski, przejdź do okna **Właściwości** i przewiń do właściwości **AutoSize** . Ta właściwość nakazuje przyciskowi automatyczną zmianę rozmiaru w celu dopasowania do całego tekstu. Ustaw dla niego **wartość true**. Przyciski powinny mieć teraz rozmiar prawidłowy i być w odpowiedniej kolejności. (Pod warunkiem, że wszystkie cztery przyciski są zaznaczone, można zmienić wszystkie cztery właściwości **autorozmiaru** w tym samym czasie). Na poniższej ilustracji przedstawiono cztery przyciski.

     ![Przeglądarka obrazów z czterema przyciskami](../ide/media/express-autosize.png "Express_AutoSize") Przeglądarka obrazów z czterema przyciskami

6. Teraz ponownie uruchom program, aby zobaczyć nowo ustanowiony formularz. Wybranie przycisków i pola wyboru nie wykonuje jeszcze żadnych czynności, ale wkrótce będzie to możliwe.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 6. nazwa kontrolek przycisku](../ide/step-6-name-your-button-controls.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4. układ formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
