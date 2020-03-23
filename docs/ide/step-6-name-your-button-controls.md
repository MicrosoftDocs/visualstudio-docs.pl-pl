---
title: 'Krok 6: Nadaj nazwy przyciskom'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579793"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Nadaj nazwy przyciskom

Jest tylko jeden <xref:System.Windows.Forms.PictureBox> w formularzu. Po dodaniu, IDE automatycznie nazwał go **pictureBox1**. Jest tylko jeden <xref:System.Windows.Forms.CheckBox>, który nosi nazwę **checkBox1**. Wkrótce napiszesz kod, a ten kod będzie odnosił się do CheckBox i PictureBox. Ponieważ istnieje tylko jeden z tych formantów, będziesz wiedzieć, co to znaczy, gdy widzisz **pictureBox1** lub **checkBox1** w kodzie.

> [!TIP]
> W języku Visual Basic domyślną pierwszą literą dowolnej nazwy formantu jest początkowa etykieta, więc nazwy to **PictureBox1**, **CheckBox1**i tak dalej.

W formularzu znajdują się cztery przyciski, a IDE nazwał je **button1**, **button2**, **button3**i **button4**. Patrząc tylko na ich aktualne nazwy, nie wiesz, który przycisk jest przycisk **Zamknij,** a który jest przycisk **Pokaż zdjęcie.** Dlatego nadanie przyciskom bardziej informacyjnych nazw jest pomocne.

## <a name="to-name-your-button-controls"></a>Aby nadać nazwy kontrolkami przycisków

1. W formularzu wybierz przycisk **Zamknij.** (Jeśli nadal zaznaczono wszystkie przyciski, wybierz klawisz **Esc,** aby anulować zaznaczenie). Przewiń w oknie **Właściwości,** aż zobaczysz właściwość **(Nazwa).** (Właściwość **(Nazwa)** znajduje się u góry, gdy właściwości są alfabetyczne.) Zmień nazwę, aby **closeButton**, jak pokazano na poniższym zrzucie ekranu.

    ![Okno Właściwości z nazwą closeButton](../ide/media/express_setnameproperty.png)<br>***Properties*** *Okno* Właściwości z *nazwą* ***closeButton***

    > [!NOTE]
    > Spróbuj zmienić nazwę przycisku, aby **zamknąć Button**, z spacją między słowami "zamknij" i "Przycisk". Po wykonaniu tej pracy ide wyświetla komunikat o błędzie: "Wartość właściwości jest nieprawidłowa." Spacje (i kilka innych znaków) nie są dozwolone w nazwach formantów.

1. Zmień nazwę pozostałych trzech przycisków na **backgroundButton**, **clearButton**i **showButton**.
Nazwy można sprawdzić, wybierając listę rozwijaną selektora formantu w oknie **Właściwości.** Pojawią się nowe nazwy przycisków.

1. Kliknij dwukrotnie przycisk **Pokaż zdjęcie** w formularzu. Alternatywnie wybierz przycisk **Pokaż obraz** w formularzu, a następnie naciśnij klawisz **Enter.** Po wykonaniu tej usługi IDE otworzy dodatkową kartę w oknie głównym o nazwie **Form1.cs**. (Jeśli używasz języka Visual Basic, karta nosi nazwę **Form1.vb**).

   Ta karta wyświetla plik kodu za formularzem, jak pokazano na poniższym zrzucie ekranu.

    ![Karta Form1.cs z kodem&#35; programu Visual C](../ide/media/express_showbuttoncode.png)<br>
***Karta Form1.cs*** *z kodem języka C#*

    > [!NOTE]
    > Karta Form1.cs lub Form1.vb może wyświetlać **showButton** jako **ShowButton.**

1. Skoncentruj się na tej części kodu.

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

   Szukasz kodu o nazwie `showButton_Click()` (alternatywnie). `ShowButton_Click()` IDE dodał to do kodu formularza po otwarciu pliku kodu dla przycisku **showButton.** W czasie projektowania po otwarciu pliku kodu formantu w formularzu, kod jest generowany dla formantu, jeśli jeszcze nie istnieje. Ten kod, znany jako *metoda,* jest uruchamiany po uruchomieniu aplikacji i wybraniu formantu — w tym przypadku **przycisku Pokaż obraz.**

1. Ponownie wybierz kartę **Projektant formularzy systemu Windows** ( Form1.cs **[Projekt]**), a następnie otwórz plik kodu dla przycisku **Wyczyść obraz,** aby utworzyć dla niego metodę w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.

1. Aby dodać jeszcze jedną metodę, otwórz plik kodu formantu **CheckBox** w `checkBox1_CheckedChanged()` **projektancie formularzy systemu Windows,** aby ide dodać metodę. Ta metoda jest wywoływana za każdym razem, gdy użytkownik zaznacza lub czyści pole wyboru.

   > [!TIP]
   > Podczas pracy nad aplikacją często można przechodzić między edytorem kodu a programem **Windows Forms Designer.** IDE ułatwia nawigację w projekcie. Użyj **Eksploratora rozwiązań,** aby otworzyć **Projektanta formularzy systemu Windows,** klikając dwukrotnie *Form1.cs* w języku C# lub *Formularz1.vb* w języku Visual Basic lub na pasku menu wybierz polecenie **Wyświetl** > **projektanta**.

    Poniżej przedstawiono nowy kod, który jest wyświetlany w edytorze kodu.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Kod może nie wyświetlać programów obsługi zdarzeń w literach "camelCase".

    Pięć dodanych metod są nazywane *programami obsługi zdarzeń,* ponieważ aplikacja wywołuje je za każdym razem, gdy zdarzenie (np. użytkownik wybierający przycisk lub zaznaczając pole) dzieje.

    Podczas wyświetlania kodu formantu w IDE w czasie projektowania visual studio dodaje metodę obsługi zdarzeń dla formantu, jeśli nie ma. Na przykład po dwukrotnym kliknięciu przycisku IDE dodaje <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla swojego zdarzenia (który jest wywoływany za każdym razem, gdy użytkownik wybierze przycisk). Po dwukrotnym kliknięciu pola wyboru IDE dodaje <xref:System.Windows.Forms.CheckBox.CheckedChanged> program obsługi zdarzeń dla swojego zdarzenia (który jest wywoływany za każdym razem, gdy użytkownik zaznaczy lub wyczyści to pole).

    Po dodaniu programu obsługi zdarzeń dla formantu można do niego powrócić w dowolnym momencie z **programu Windows Forms Designer,** klikając dwukrotnie formant lub na pasku menu, wybierając pozycję **Wyświetl** > **kod**.

    Nazwy są ważne podczas tworzenia programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę. Po dodaniu programu obsługi zdarzeń z IDE, tworzy nazwę na podstawie nazwy formantu i zdarzenia obsługiwane.

    Na przykład Click zdarzenie dla przycisku o nazwie **showButton** jest nazywany `showButton_Click()` (alternatywnie) `ShowButton_Click()`metoda obsługi zdarzeń. Ponadto otwieranie i zamykanie `()` nawiasów są zwykle dodawane po nazwie metody, aby wskazać, że metody są omawiane.

    Jeśli zdecydujesz, że chcesz zmienić nazwę zmiennej kodu, kliknij tę zmienną w kodzie, a następnie wybierz polecenie **Refactor** > **Rename**. Wszystkie wystąpienia tej zmiennej w kodzie są zmieniane. Aby uzyskać więcej informacji, zobacz [Zmiana nazwy refaktoryzacji](../ide/reference/rename.md).

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 5: Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
