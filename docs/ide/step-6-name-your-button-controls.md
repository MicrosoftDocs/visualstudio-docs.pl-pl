---
title: Krok 6. Nadawanie nazw kontrolkom przycisków
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46ad996f7c3b1eeff4a3eb928442879f0b7275aa
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925882"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6. Nadawanie nazw kontrolkom przycisków
W formularzu występuje tylko <xref:System.Windows.Forms.PictureBox> jeden. Po dodaniu, IDE automatycznie nazywa go **PictureBox1**. Istnieje tylko jeden <xref:System.Windows.Forms.CheckBox>o nazwie **checkBox1**. Wkrótce napiszesz kod i ten kod będzie się odnosił do pola CheckBox i PictureBox. Ponieważ istnieje tylko jedna z tych kontrolek, wiadomo, co oznacza, gdy zobaczysz **PictureBox1** lub **checkBox1** w kodzie.

> [!NOTE]
> W Visual Basic domyślną pierwszą literą każdej nazwy kontrolki jest Inicjał, więc nazwy to **PictureBox1**, **checkBox1**i tak dalej.

W formularzu znajdują się cztery przyciski i IDE o nazwie im **Button1**, **Button2**, **button3**i **button4**. Po prostu patrząc na swoje bieżące nazwy nie wiesz, który przycisk jest przyciskiem **Close** i który jest przyciskiem **Pokaż obraz** . Z tego względu, jeśli przycisk steruje bardziej informacyjnymi nazwami, pomocne są.

![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Utwórz przeglądarkę obrazów w C# pliku wideo 3.](http://go.microsoft.com/fwlink/?LinkId=205202) Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-name-your-button-controls"></a>Aby nazwać kontrolki przycisku

1. W formularzu wybierz przycisk **Zamknij** . (Jeśli nadal masz zaznaczone wszystkie przyciski, wybierz klawisz **ESC** , aby anulować wybór). Przewiń w oknie **Właściwości** do momentu wyświetlenia właściwości **(Name)** . (Właściwość **(Name)** znajduje się najbliżej góry, gdy właściwości są alfabetyczne.) Zmień nazwę na **CloseButton**, jak pokazano na poniższej ilustracji.

     ![Okno właściwości przy użyciu okna](../ide/media/express_setnameproperty.png)
**Właściwości** nazwy CloseButton z nazwą **CloseButton**

    > [!NOTE]
    > Jeśli spróbujesz zmienić nazwę przycisku na **CloseButton**, z odstępem między wyrazami Zamknij i przycisk, IDE wyświetli komunikat o błędzie: "Wartość właściwości jest nieprawidłowa." Spacje (i kilka innych znaków) nie są dozwolone w nazwach kontrolek.

2. Zmień nazwy pozostałych trzech przycisków na **backgroundButton**, **clearButton**i **showButton**. Nazwy można sprawdzić, wybierając listę rozwijaną selektor formantów w oknie **Właściwości** . Pojawią się nowe nazwy przycisków.

3. Kliknij dwukrotnie przycisk **Pokaż obraz** w formularzu. Alternatywnie wybierz przycisk **Pokaż obraz** na formularzu, a następnie wybierz klawisz **Enter** . Gdy to zrobisz, IDE otworzy dodatkową kartę w oknie głównym o nazwie **Form1.cs** (**Form1. vb** , jeśli używasz Visual Basic). Na tej karcie jest wyświetlany plik kodu znajdujący się za formularzem, jak pokazano na poniższej ilustracji.

     ![Karta Form1.cs z kartą Visual&#35; C](../ide/media/express_showbuttoncode.png)
Code**Form1.cs** z kodem C# wizualizacji

4. Skup się na tej części kodu. (Wybierz kartę **VB** poniżej, jeśli używasz Visual Basic do wyświetlania Visual Basic wersji kodu).

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]

     Przeglądasz kod o nazwie `showButton_Click()`. Środowisko IDE zostało dodane do kodu formularza podczas otwierania pliku kodu dla przycisku **showButton** . W czasie projektowania, gdy otworzysz plik kodu dla formantu w formularzu, kod jest generowany dla kontrolki, jeśli jeszcze nie istnieje. Ten kod, znany jako *Metoda*, jest uruchamiany po uruchomieniu programu i wybraniu kontrolki — w tym przypadku przycisk **Pokaż obraz** .

    > [!NOTE]
    > W tym samouczku wygenerowany automatycznie kod Visual Basic został uproszczony przez usunięcie wszystkich elementów między nawiasami `()`. W każdym przypadku można usunąć ten sam kod. Program będzie działał w dowolny sposób. W pozostałej części samouczków każdy automatycznie wygenerowany kod jest uproszczony zawsze, gdy jest to możliwe.

5. Wybierz ponownie kartę **Projektant formularzy systemu Windows** (**Form1.cs [projekt]** w wizualizacji C#, **formularz Form1. vb [projekt]** w Visual Basic), a następnie otwórz plik kodu dla przycisku **Wyczyść obraz** , aby utworzyć dla niego metodę w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.

6. Aby dodać jeszcze jedną metodę, Otwórz plik kodu dla kontrolki **CheckBox** w **Projektant formularzy systemu Windows** , aby umożliwić `checkBox1_CheckedChanged()` IDE dodanie metody. Ta metoda jest wywoływana za każdym razem, gdy użytkownik zaznaczy lub wyczyści to pole wyboru.

    > [!NOTE]
    > Podczas pracy z programem często przechodzą między edytorem kodu a **Projektant formularzy systemu Windows**. Środowisko IDE ułatwia nawigowanie w projekcie. Użyj **Eksplorator rozwiązań** , aby **otworzyć Projektant formularzy systemu Windows** przez dwukrotne kliknięcie *Form1.cs* w C# wizualizacji lub *Form1. vb* w Visual Basic lub na pasku menu wybierz**Projektant** **widoków** > .

     Poniżej przedstawiono nowy kod widoczny w edytorze kodu.

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

     Pięć metod, które zostały dodane, nazywają *programy obsługi zdarzeń*, ponieważ program wywołuje je za każdym razem, gdy występuje zdarzenie (takie jak użytkownik wybierający przycisk lub zaznaczenie pola).

     Gdy przeglądasz kod kontrolki w środowisku IDE w czasie projektowania, Visual Studio dodaje metodę programu obsługi zdarzeń dla kontrolki, jeśli taka nie istnieje. Na przykład po dwukrotnym kliknięciu przycisku IDE dodaje procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia (która jest wywoływana za każdym razem, gdy użytkownik wybierze przycisk). Po dwukrotnym kliknięciu pola wyboru, IDE dodaje procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia (która jest wywoływana za każdym razem, gdy użytkownik wybierze lub usunie pole).

     Po dodaniu programu obsługi zdarzeń dla formantu można wrócić do niego w dowolnym momencie z **Projektant formularzy systemu Windows** przez dwukrotne kliknięcie kontrolki lub na pasku menu, wybierając polecenie **Wyświetl** > **kod**.

     Nazwy są ważne podczas tworzenia programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę. Po dodaniu programu obsługi zdarzeń przy użyciu IDE tworzy on nazwę na podstawie nazwy kontrolki i obsługiwanego zdarzenia. Na przykład zdarzenie kliknięcia dla przycisku o nazwie **showButton** jest nazywane `showButton_Click()` metodą obsługi zdarzeń. Ponadto nawiasy `()` otwierające i zamykające są zwykle dodawane po nazwie metody, aby wskazać, że metody są omawiane. Jeśli zdecydujesz się zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy zmienną w kodzie, a następnie wybierz pozycję Refaktoryzacja > **Zmień nazwę**. Nazwy wszystkich wystąpień tej zmiennej w kodzie. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja zmiany nazwy](../ide/reference/rename.md) .

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 7: Dodaj składniki okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodaj formanty do formularza](../ide/step-5-add-controls-to-your-form.md).
