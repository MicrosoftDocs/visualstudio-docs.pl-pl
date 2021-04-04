---
title: Krok 6. Nadawanie nazw kontrolkom przycisków
description: Dowiedz się, jak nazwać kontrolki przycisków.
ms.custom: SEO-VS-2020
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f69a87d923eebaea03c9c8a38496c4c379db8aba
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214216"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6. Nadawanie nazw kontrolkom przycisków

W formularzu występuje tylko jeden <xref:System.Windows.Forms.PictureBox> . Po dodaniu, IDE automatycznie nazywa go **PictureBox1**. Istnieje tylko jeden <xref:System.Windows.Forms.CheckBox> o nazwie **checkBox1**. Wkrótce napiszesz kod i ten kod będzie się odnosił do pola CheckBox i PictureBox. Ponieważ istnieje tylko jedna z tych kontrolek, wiadomo, co oznacza, gdy zobaczysz **PictureBox1** lub **checkBox1** w kodzie.

> [!TIP]
> W Visual Basic domyślną pierwszą literą każdej nazwy kontrolki jest Inicjał, więc nazwy to **PictureBox1**, **checkBox1** i tak dalej.

W formularzu znajdują się cztery przyciski i IDE o nazwie im **Button1**, **Button2**, **button3** i **button4**. Po prostu patrząc na swoje bieżące nazwy nie wiesz, który przycisk jest przyciskiem **Close** i który jest przyciskiem **Pokaż obraz** . Z tego względu, jeśli przycisk steruje bardziej informacyjnymi nazwami, pomocne są.

## <a name="to-name-your-button-controls"></a>Aby nazwać kontrolki przycisku

1. W formularzu wybierz przycisk **Zamknij** . (Jeśli nadal masz zaznaczone wszystkie przyciski, wybierz klawisz **ESC** , aby anulować wybór). Przewiń w oknie **Właściwości** do momentu wyświetlenia właściwości **(Name)** . (Właściwość **(Name)** znajduje się najbliżej góry, gdy właściwości są alfabetyczne.) Zmień nazwę na **CloseButton**, jak pokazano na poniższym zrzucie ekranu.

    ![okno Właściwości z nazwą closeButton](../ide/media/express_setnameproperty.png)<br>***Właściwości** _ _okno z * ***CloseButton**_ _name *

    > [!NOTE]
    > Spróbuj zmienić nazwę przycisku na **przycisk Zamknij**, spację między wyrazami "Zamknij" i "przycisk". Gdy to zrobisz, IDE wyświetli komunikat o błędzie: "wartość właściwości jest nieprawidłowa." Spacje (i kilka innych znaków) nie są dozwolone w nazwach kontrolek.

1. Zmień nazwy pozostałych trzech przycisków na **backgroundButton**, **clearButton** i **showButton**.
Nazwy można sprawdzić, wybierając listę rozwijaną selektor formantów w oknie **Właściwości** . Pojawią się nowe nazwy przycisków.

1. Kliknij dwukrotnie przycisk **Pokaż obraz** w formularzu. Alternatywnie wybierz przycisk **Pokaż obraz** na formularzu, a następnie naciśnij klawisz **Enter** . Gdy to zrobisz, IDE otworzy dodatkową kartę w oknie głównym o nazwie **Form1. cs**. (Jeśli używasz Visual Basic, karta nosi nazwę **Form1. vb**).

   Na tej karcie jest wyświetlany plik kodu znajdujący się za formularzem, jak pokazano na poniższym zrzucie ekranu.

    ![Karta Form1. cs z kodem&#35; języka Visual C](../ide/media/express_showbuttoncode.png)<br>
***Formularz Form1. cs** _ _tab z kodem C# *

    > [!NOTE]
    > W przypadku karty Form1. cs lub Form1. vb zamiast tego można wyświetlić **showButton** jako **showButton** .

1. Skup się na tej części kodu.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Przeglądasz kod o nazwie `showButton_Click()` (Alternatywnie `ShowButton_Click()` ). Środowisko IDE zostało dodane do kodu formularza podczas otwierania pliku kodu dla przycisku **showButton** . W czasie projektowania, gdy otworzysz plik kodu dla formantu w formularzu, kod jest generowany dla kontrolki, jeśli jeszcze nie istnieje. Ten kod, znany jako *Metoda*, jest uruchamiany po uruchomieniu aplikacji i wybraniu kontrolki — w tym przypadku przycisk **Pokaż obraz** .

1. Wybierz ponownie kartę **Projektant formularzy systemu Windows** (**Form1. cs [Design]**), a następnie otwórz plik kodu dla przycisku **Wyczyść obraz** , aby utworzyć dla niego metodę w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.

1. Aby dodać jeszcze jedną metodę, Otwórz plik kodu dla kontrolki **CheckBox** w **Projektant formularzy systemu Windows** , aby umożliwić IDE dodanie `checkBox1_CheckedChanged()` metody. Ta metoda jest wywoływana za każdym razem, gdy użytkownik zaznaczy lub wyczyści to pole wyboru.

   > [!TIP]
   > Podczas pracy nad aplikacją często przechodzą między edytorem kodu a **Projektant formularzy systemu Windows**. Środowisko IDE ułatwia nawigowanie w projekcie. Użyj **Eksplorator rozwiązań** , aby otworzyć **Projektant formularzy systemu Windows** przez dwukrotne kliknięcie *formularza Form1. cs* w języku C# lub *Form1. vb* w Visual Basic lub na pasku menu wybierz polecenie   >  **Projektant** widoków.

    Poniżej przedstawiono nowy kod widoczny w edytorze kodu.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs" id="Snippet2":::

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb" id="Snippet2":::

    > [!NOTE]
    > Kod może nie wyświetlać programów obsługi zdarzeń w przypadku liter "camelCase".

    Pięć metod, które zostały dodane, nazywają *programy obsługi zdarzeń*, ponieważ aplikacja wywołuje je za każdym razem, gdy występuje zdarzenie (takie jak użytkownik wybierający przycisk lub zaznaczając pole).

    Gdy przeglądasz kod kontrolki w środowisku IDE w czasie projektowania, Visual Studio dodaje metodę programu obsługi zdarzeń dla kontrolki, jeśli taka nie istnieje. Na przykład po dwukrotnym kliknięciu przycisku IDE dodaje procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia (która jest wywoływana za każdym razem, gdy użytkownik wybierze przycisk). Po dwukrotnym kliknięciu pola wyboru, IDE dodaje procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia (która jest wywoływana za każdym razem, gdy użytkownik wybierze lub usunie pole).

    Po dodaniu programu obsługi zdarzeń dla formantu można wrócić do niego w dowolnym momencie z **Projektant formularzy systemu Windows** przez dwukrotne kliknięcie kontrolki lub na pasku menu, wybierając polecenie **Wyświetl**  >  **kod**.

    Nazwy są ważne podczas tworzenia programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę. Po dodaniu programu obsługi zdarzeń przy użyciu IDE tworzy on nazwę na podstawie nazwy kontrolki i obsługiwanego zdarzenia.

    Na przykład zdarzenie kliknięcia dla przycisku o nazwie **showButton** jest nazywane `showButton_Click()` (Alternatywnie `ShowButton_Click()` ) metodą obsługi zdarzeń. Ponadto nawiasy otwierające i zamykające `()` są zwykle dodawane po nazwie metody, aby wskazać, że metody są omawiane.

    Jeśli zdecydujesz się zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy zmienną w kodzie, a następnie wybierz pozycję **Refaktoryzacja**  >  **Zmień nazwę**. Nazwy wszystkich wystąpień tej zmiennej w kodzie. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja zmiany nazwy](../ide/reference/rename.md).

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
