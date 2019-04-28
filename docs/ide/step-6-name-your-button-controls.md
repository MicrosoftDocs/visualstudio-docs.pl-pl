---
title: Krok 6. Nazw kontrolkom przycisków
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dbee780f2153003e870dbe0dbbb15b721a009df
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442018"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6. Nazw kontrolkom przycisków
Jest tylko jedna <xref:System.Windows.Forms.PictureBox> w formularzu. Po dodaniu, IDE automatycznie nadał mu **pictureBox1**. Jest tylko jedna <xref:System.Windows.Forms.CheckBox>, który nosi **checkBox1**. Wkrótce będzie pisanie kodu i ten kod będzie odnosić się do CheckBox i PictureBox. Ponieważ istnieje tylko jeden z tych kontrolek, będzie wiadomo, co oznacza wyświetlenie **pictureBox1** lub **checkBox1** w kodzie.

> [!NOTE]
> W języku Visual Basic domyślną literą dowolnej nazwę formantu jest zakończenie początkowej, więc nazwy to **PictureBox1**, **CheckBox1**i tak dalej.

 Dostępne są cztery przyciski w formularzu i IDE nadaje im **button1**, **button2**, **button3**, i **button4**. Patrząc tylko na ich aktualne nazwy, nie wiesz, który przycisk to **Zamknij** przycisk i który z nich jest **Pokaż obraz** przycisku. Dlatego właśnie nadawanie formantom przycisków bardziej czytelnych nazw jest pomocne.

 ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -3 wideo](http://go.microsoft.com/fwlink/?LinkId=205202). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-name-your-button-controls"></a>Aby nazwać formanty przycisków

1. W formularzu Wybierz **Zamknij** przycisku. (Jeśli nadal masz zaznaczone wszystkie przyciski, wybierz opcję **Esc** klawisz, aby anulować zaznaczenie.) Przewijanie w **właściwości** okna, aż zobaczysz **(nazwa)** właściwości. ( **(Nazwa)** właściwość jest u góry, gdy właściwości są w kolejności alfabetycznej.) Zmień nazwę na **closeButton**, jak pokazano na poniższej ilustracji.

     ![Okno właściwości z nazwą closeButton](../ide/media/express_setnameproperty.png)
**właściwości** okno z **closeButton** nazwy

    > [!NOTE]
    > Jeśli spróbujesz zmienić nazwę przycisku na **closeButton**, ze spacją między wyrazami przycisk i zamykania, środowisko IDE wyświetla komunikat o błędzie: "Wartość właściwości jest nieprawidłowa." Miejsca do magazynowania (i kilka innych znaków) są niedozwolone w nazwach formantów.

2. Zmień nazwę inne trzy przyciski na **backgroundButton**, **clearButton**, i **showButton**. Możesz sprawdzić nazwy, wybierając przycisk listy rozwijanej selektora kontroli w **właściwości** okna. Pojawiają się nowe nazwy przycisków.

3. Kliknij dwukrotnie **Pokaż obraz** przycisku w formularzu. Jako alternatywę, wybierz **Pokaż obraz** znajdujący się na formularzu, a następnie wybierz **Enter** klucza. Po wykonaniu, IDE otwiera dodatkową kartę w oknie głównym o nazwie **Form1.cs** (**Form1.vb** Jeśli używasz języka Visual Basic). Ta karta przedstawia plik kodu za formularzem, jak pokazano na poniższej ilustracji.

     ![Karta Form1.CS z Visual C&#35; kodu](../ide/media/express_showbuttoncode.png)
**Form1.cs** kartę z wizualizacją C# kodu

4. Skup się na niniejszej części kodu. (Wybierz **VB** karcie poniżej, jeśli używasz języka Visual Basic, aby wyświetlić wersję kodu w Visual Basic.)

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]

     Szukasz w kodzie o nazwie `showButton_Click()`. IDE dodane to do kodu formularza podczas otwierania pliku kodu dla **showButton** przycisku. W czasie projektowania podczas otwierania pliku kodu dla formantu w formularzu, kod jest generowany dla formantu, jeśli jeszcze nie istnieje. Ten kod, znany jako *metoda*, jest uruchamiany, gdy uruchamianie programu i wybraniu formantu - w takim przypadku **Pokaż obraz** przycisku.

    > [!NOTE]
    > W tym samouczku został uproszczony kod języka Visual Basic, która jest generowana automatycznie przez usunięcie wszystkiego w nawiasach `()`. Zawsze, gdy ten problem wystąpi, możesz usunąć ten sam kod. Program będzie działać w obu kierunkach. Dla pozostałej części samouczków wszelki automatycznie wygenerowany kod jest uproszczony w miarę możliwości.

5. Wybierz **Windows Forms Designer** karcie ponownie (**Form1.cs [projekt]** w elemencie wizualnym C#, **Form1.vb [projekt]** w języku Visual Basic), a następnie otwórz plik kodu dla  **Wyczyść obraz** przycisk, aby utworzyć metodę dla niego w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.

6. Aby dodać jedną metodę, otwórz plik kodu dla **wyboru** w kontrolce **Windows Forms Designer** się IDE doda `checkBox1_CheckedChanged()` metody. Metoda ta jest wywoływana zawsze wtedy, gdy użytkownik zaznacza lub czyści pole wyboru.

    > [!NOTE]
    > Podczas pracy z programem, często przechodzisz między Edytorem kodu a **Windows Forms Designer**. IDE ułatwia nawigowanie w projekcie. Użyj **Eksploratora rozwiązań** otworzyć **Windows Forms Designer** przez dwukrotne kliknięcie *Form1.cs* w elemencie wizualnym C# lub *Form1.vb* w Visual Basic lub na pasku menu wybierz **widoku** > **projektanta**.

     Poniżej przedstawiono nowy kod wyświetlany w edytorze kodu.

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

     Pięć metod, które zostały dodane są nazywane *procedury obsługi zdarzeń*, ponieważ program wywołuje je zawsze, gdy występuje zdarzenie (na przykład użytkownika, wybranie przycisku lub zaznaczenie pola).

     Podczas przeglądania kodu dla formantu w IDE w czasie projektowania, Visual Studio dodaje metodę programu obsługi zdarzeń dla formantu, jeśli go tam jeszcze nie. Na przykład po dwukrotnym kliknięciu przycisku środowisko IDE dodaje program obsługi zdarzeń dla jego <xref:System.Windows.Forms.Control.Click> zdarzeń, (które jest wywoływane, gdy użytkownik naciśnie przycisk). Po dwukrotnym kliknięciu pola wyboru IDE dodaje program obsługi zdarzeń dla jego <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzeń, (które jest wywoływane zawsze wtedy, gdy użytkownik zaznacza lub czyści pole).

     Po dodaniu programu obsługi zdarzeń dla formantu, można powrócisz do niego w dowolnym momencie z **Windows Forms Designer** przez dwukrotne kliknięcie formantu lub na pasku menu, wybierając **widoku**  >  **Kodu**.

     Nazwy są ważne podczas kompilowania programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę, która ma. Po dodaniu programu obsługi zdarzeń z IDE, tworzy on nazwę na podstawie nazwy formantu i przetwarzanego zdarzenia. Na przykład zdarzenie kliknięcia dla przycisku o nazwie **showButton** nosi nazwę `showButton_Click()` metody obsługi zdarzeń. Ponadto, nawiasy otwierające i zamykające `()` są zwykle dodawane po nazwie metody aby wskazać, że metody są przedmiotem. Jeśli zdecydujesz, aby zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy na zmiennej w kodzie, a następnie wybierz **Refaktoryzuj** > **Zmień nazwę**. Wszystkie wystąpienia tej zmiennej w kodzie są zmieniane. Zobacz [Refaktoryzacja zmiany nazwy](../ide/reference/rename.md) Aby uzyskać więcej informacji.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md).
