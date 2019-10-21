---
title: Krok 6. nazwa kontrolek przycisków | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be633da5e8af6b987178d7c7360096db57fff1a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647011"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6. Nadawanie nazw kontrolkom przycisków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W formularzu istnieje tylko jeden element PictureBox. Po dodaniu, IDE automatycznie nazywa go **PictureBox1**. Istnieje tylko jedno pole wyboru o nazwie **checkBox1**. Wkrótce napiszesz kod i ten kod będzie się odnosił do pola CheckBox i PictureBox. Ponieważ istnieje tylko jedna z tych kontrolek, wiadomo, co oznacza, gdy zobaczysz **PictureBox1** lub **checkBox1** w kodzie.

> [!NOTE]
> W Visual Basic domyślną pierwszą literą każdej nazwy kontrolki jest Inicjał, więc nazwy to **PictureBox1**, **checkBox1**i tak dalej.

 W formularzu znajdują się cztery przyciski i IDE o nazwie im **Button1**, **Button2**, **button3**i **button4**. Po prostu patrząc na swoje bieżące nazwy nie wiesz, który przycisk jest przyciskiem **Close** i który jest przyciskiem **Pokaż obraz** . Z tego względu, jeśli przycisk steruje bardziej informacyjnymi nazwami, pomocne są.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# wideo 3](http://go.microsoft.com/fwlink/?LinkId=205202). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-name-your-button-controls"></a>Aby nazwać kontrolki przycisku

1. W formularzu wybierz przycisk **Zamknij** . (Jeśli nadal masz zaznaczone wszystkie przyciski, wybierz klawisz ESC, aby anulować wybór). Przewiń w oknie **Właściwości** do momentu wyświetlenia właściwości **(Name)** . (Właściwość **(Name)** znajduje się najbliżej góry, gdy właściwości są alfabetyczne.) Zmień nazwę na **CloseButton**, jak pokazano na poniższej ilustracji.

     ![Okno właściwości z nazwą CloseButton](../ide/media/express-setnameproperty.png "Express_SetNameProperty") okno Właściwości z nazwą closeButton

    > [!NOTE]
    > Jeśli spróbujesz zmienić nazwę przycisku na **CloseButton**, z odstępem między wyrazami Zamknij i przycisk, IDE wyświetla komunikat o błędzie: "wartość właściwości jest nieprawidłowa." Spacje (i kilka innych znaków) nie są dozwolone w nazwach kontrolek.

2. Zmień nazwy pozostałych trzech przycisków na **backgroundButton**, **clearButton**i **showButton**. Nazwy można sprawdzić, wybierając listę rozwijaną selektor formantów w oknie **Właściwości** . Pojawią się nowe nazwy przycisków.

3. Kliknij dwukrotnie przycisk **Pokaż obraz** w formularzu. Alternatywnie wybierz przycisk **Pokaż obraz** na formularzu, a następnie wybierz klawisz ENTER. Gdy to zrobisz, IDE otworzy dodatkową kartę w oknie głównym o nazwie **Form1.cs** (**Form1. vb** , jeśli używasz Visual Basic). Na tej karcie jest wyświetlany plik kodu znajdujący się za formularzem, jak pokazano na poniższej ilustracji.

     ![Karta Form1.cs z kartą Visual&#35; C Code](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode") Form1.cs z kodem C# wizualizacji

4. Skup się na tej części kodu. (Wybierz kartę **VB** poniżej, jeśli używasz Visual Basic do wyświetlania Visual Basic wersji kodu).

     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]

     Przeglądasz kod o nazwie `showButton_Click()`. Środowisko IDE zostało dodane do kodu formularza podczas otwierania pliku kodu dla przycisku **showButton** . W czasie projektowania, gdy otworzysz plik kodu dla formantu w formularzu, kod jest generowany dla kontrolki, jeśli jeszcze nie istnieje. Ten kod, znany jako *Metoda*, jest uruchamiany po uruchomieniu programu i wybraniu kontrolki — w tym przypadku przycisk **Pokaż obraz** .

    > [!NOTE]
    > W tym samouczku wygenerowany automatycznie kod Visual Basic został uproszczony przez usunięcie wszystkich elementów między nawiasami (). W każdym przypadku można usunąć ten sam kod. Program będzie działał w dowolny sposób. W pozostałej części samouczków każdy automatycznie wygenerowany kod jest uproszczony zawsze, gdy jest to możliwe.

5. Wybierz ponownie kartę Projektant formularzy systemu Windows (**Form1.cs [projekt]** w wizualizacji C#, **formularz Form1. vb [projekt]** w Visual Basic), a następnie otwórz plik kodu dla przycisku **Wyczyść obraz** , aby utworzyć dla niego metodę w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.

6. Aby dodać jeszcze jedną metodę, Otwórz plik kodu dla kontrolki CheckBox w Projektant formularzy systemu Windows, aby środowisko IDE dodać metodę `checkBox1_CheckedChanged()`. Ta metoda jest wywoływana za każdym razem, gdy użytkownik zaznaczy lub wyczyści to pole wyboru.

    > [!NOTE]
    > Podczas pracy z programem często przechodzą między edytorem kodu a Projektant formularzy systemu Windows. Środowisko IDE ułatwia nawigowanie w projekcie. Użyj **Eksplorator rozwiązań** , aby otworzyć Projektant formularzy systemu Windows przez dwukrotne kliknięcie **Form1.cs** C# w wizualizacji lub **Form1. vb** w Visual Basic lub na pasku menu wybierz **Widok**, **Projektant**.

     Poniżej przedstawiono nowy kod widoczny w edytorze kodu.

     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]

     Pięć metod, które zostały dodane, nazywają *programy obsługi zdarzeń*, ponieważ program wywołuje je za każdym razem, gdy występuje zdarzenie (takie jak użytkownik wybierający przycisk lub zaznaczenie pola).

     Gdy przeglądasz kod kontrolki w środowisku IDE w czasie projektowania, Visual Studio dodaje metodę programu obsługi zdarzeń dla kontrolki, jeśli taka nie istnieje. Na przykład po dwukrotnym kliknięciu przycisku IDE dodaje procedurę obsługi zdarzeń dla zdarzenia kliknięcia (który jest wywoływany za każdym razem, gdy użytkownik wybierze przycisk). Po dwukrotnym kliknięciu pola wyboru, IDE dodaje procedurę obsługi zdarzeń dla zdarzenia CheckedChanged (który jest wywoływany za każdym razem, gdy użytkownik zaznaczy lub wyczyści pole).

     Po dodaniu programu obsługi zdarzeń dla formantu można wrócić do niego w dowolnym momencie z Projektant formularzy systemu Windows przez dwukrotne kliknięcie kontrolki lub na pasku menu, wybierając **Widok**, **kod**.

     Nazwy są ważne podczas tworzenia programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę. Po dodaniu programu obsługi zdarzeń przy użyciu IDE tworzy on nazwę na podstawie nazwy kontrolki i obsługiwanego zdarzenia. Na przykład zdarzenie kliknięcia dla przycisku o nazwie **showButton** jest nazywane metodą obsługi zdarzeń `showButton_Click()`. Ponadto otwierające i zamykające nawiasy () są zwykle dodawane po nazwie metody, aby wskazać, że metody są omawiane. Jeśli zdecydujesz się zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy zmienną w kodzie, a następnie wybierz pozycję **Refaktoryzacja**, **Zmień nazwę**. Nazwy wszystkich wystąpień tej zmiennej w kodzie. Aby uzyskać więcej informacji, zobacz [Zmienianie refaktoryzacji (C#)](../csharp-ide/rename-refactoring-csharp.md) lub [Refaktoryzacja i zmiana nazwy okna dialogowego](https://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) .

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie kontrolek do formularza](../ide/step-5-add-controls-to-your-form.md).
