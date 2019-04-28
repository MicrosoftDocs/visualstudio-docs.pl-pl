---
title: Krok 6. Nazw kontrolkom przycisków | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 802ff20facead891f05ac4727d1c091d095c50a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442493"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6. Nadawanie nazw kontrolkom przycisków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W formularzu istnieje tylko jeden element PictureBox. Po dodaniu, IDE automatycznie nadał mu **pictureBox1**. Istnieje tylko jedno pole wyboru, która nosi nazwę **checkBox1**. Wkrótce będzie pisanie kodu i ten kod będzie odnosić się do CheckBox i PictureBox. Ponieważ istnieje tylko jeden z tych kontrolek, będzie wiadomo, co oznacza wyświetlenie **pictureBox1** lub **checkBox1** w kodzie.  
  
> [!NOTE]
> W języku Visual Basic domyślną literą dowolnej nazwę formantu jest zakończenie początkowej, więc nazwy to **PictureBox1**, **CheckBox1**i tak dalej.  
  
 Dostępne są cztery przyciski w formularzu i IDE nadaje im **button1**, **button2**, **button3**, i **button4**. Patrząc tylko na ich aktualne nazwy, nie wiesz, który przycisk to **Zamknij** przycisk i który z nich jest **Pokaż obraz** przycisku. Dlatego właśnie nadawanie formantom przycisków bardziej czytelnych nazw jest pomocne.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 3](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 3](http://go.microsoft.com/fwlink/?LinkId=205202). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-name-your-button-controls"></a>Aby nazwać formanty przycisków  
  
1. W formularzu Wybierz **Zamknij** przycisku. (Jeśli nadal masz zaznaczone wszystkie przyciski, wybierz klawisz ESC, aby anulować zaznaczenie). Przewijanie w **właściwości** okna, aż zobaczysz **(nazwa)** właściwości. ( **(Nazwa)** właściwość jest u góry, gdy właściwości są w kolejności alfabetycznej.) Zmień nazwę na **closeButton**, jak pokazano na poniższej ilustracji.  
  
     ![Okno właściwości z nazwą closeButton](../ide/media/express-setnameproperty.png "Express_SetNameProperty")  
Okno właściwości z nazwą closeButton  
  
    > [!NOTE]
    > Jeśli spróbujesz zmienić nazwę przycisku na **closeButton**, ze spacją między wyrazami przycisk i zamykania, środowisko IDE wyświetla komunikat o błędzie: "Wartość właściwości jest nieprawidłowa." Miejsca do magazynowania (i kilka innych znaków) są niedozwolone w nazwach formantów.  
  
2. Zmień nazwę inne trzy przyciski na **backgroundButton**, **clearButton**, i **showButton**. Możesz sprawdzić nazwy, wybierając przycisk listy rozwijanej selektora kontroli w **właściwości** okna. Pojawiają się nowe nazwy przycisków.  
  
3. Kliknij dwukrotnie **Pokaż obraz** przycisku w formularzu. Jako alternatywę, wybierz **Pokaż obraz** znajdujący się na formularzu, a następnie naciśnij klawisz ENTER. Po wykonaniu, IDE otwiera dodatkową kartę w oknie głównym o nazwie **Form1.cs** (**Form1.vb** Jeśli używasz języka Visual Basic). Ta karta przedstawia plik kodu za formularzem, jak pokazano na poniższej ilustracji.  
  
     ![Karta Form1.CS z Visual C&#35; kodu](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode")  
Karta Form1.CS z kodem języka Visual C#  
  
4. Skup się na niniejszej części kodu. (Wybierz **VB** karcie poniżej, jeśli używasz języka Visual Basic, aby wyświetlić wersję kodu w Visual Basic.)  
  
     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]  
  
     Szukasz w kodzie o nazwie `showButton_Click()`. IDE dodane to do kodu formularza podczas otwierania pliku kodu dla **showButton** przycisku. W czasie projektowania podczas otwierania pliku kodu dla formantu w formularzu, kod jest generowany dla formantu, jeśli jeszcze nie istnieje. Ten kod, znany jako *metoda*, jest uruchamiany, gdy uruchamianie programu i wybraniu formantu - w takim przypadku **Pokaż obraz** przycisku.  
  
    > [!NOTE]
    > W tym samouczku został uproszczony kod języka Visual Basic, która jest generowana automatycznie przez usunięcie wszystkiego w nawiasach (). Zawsze, gdy ten problem wystąpi, możesz usunąć ten sam kod. Program będzie działać w obu kierunkach. Dla pozostałej części samouczków wszelki automatycznie wygenerowany kod jest uproszczony w miarę możliwości.  
  
5. Ponownie wybierz kartę Windows Forms Designer (**Form1.cs [projekt]** w elemencie wizualnym C#, **Form1.vb [projekt]** w języku Visual Basic), a następnie otwórz plik kodu dla **Wyczyść obraz** przycisk, aby utworzyć metodę dla niego w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Za każdym razem IDE dodaje nową metodę do pliku kodu formularza.  
  
6. Aby dodać jedną metodę, otwórz plik kodu dla formantu CheckBox w Windows Forms Designer, aby sprawić, że IDE, Dodaj `checkBox1_CheckedChanged()` metody. Metoda ta jest wywoływana zawsze wtedy, gdy użytkownik zaznacza lub czyści pole wyboru.  
  
    > [!NOTE]
    > Podczas pracy z programem, często przechodzisz między Edytorem kodu a Windows Forms Designer. IDE ułatwia nawigowanie w projekcie. Użyj **Eksploratora rozwiązań** otworzyć Windows Forms Designer klikając dwukrotnie **Form1.cs** w języku Visual C# lub **Form1.vb** w języku Visual Basic lub na pasku menu wybierz **Widoku**, **projektanta**.  
  
     Poniżej przedstawiono nowy kod wyświetlany w edytorze kodu.  
  
     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]  
  
     Pięć metod, które zostały dodane są nazywane *procedury obsługi zdarzeń*, ponieważ program wywołuje je zawsze, gdy występuje zdarzenie (na przykład użytkownika, wybranie przycisku lub zaznaczenie pola).  
  
     Podczas przeglądania kodu dla formantu w IDE w czasie projektowania, Visual Studio dodaje metodę programu obsługi zdarzeń dla formantu, jeśli go tam jeszcze nie. Na przykład po dwukrotnym kliknięciu przycisku, IDE dodaje program obsługi zdarzeń dla jego zdarzenia kliknięcia, (które jest wywoływane, gdy użytkownik naciśnie przycisk). Po dwukrotnym kliknięciu pola wyboru IDE dodaje program obsługi zdarzeń dla zdarzenia CheckedChanged (które jest wywoływane zawsze wtedy, gdy użytkownik zaznacza lub czyści pole).  
  
     Po dodaniu programu obsługi zdarzeń dla formantu, można powrócisz do niego w dowolnym momencie z projektanta programu Windows Forms przez dwukrotne kliknięcie formantu lub na pasku menu, wybierając **widoku**, **kodu**.  
  
     Nazwy są ważne podczas kompilowania programów, a metody (w tym programy obsługi zdarzeń) mogą mieć dowolną nazwę, która ma. Po dodaniu programu obsługi zdarzeń z IDE, tworzy on nazwę na podstawie nazwy formantu i przetwarzanego zdarzenia. Na przykład zdarzenie kliknięcia dla przycisku o nazwie **showButton** nosi nazwę `showButton_Click()` metody obsługi zdarzeń. Ponadto otwierający i zamykający nawias () są zwykle dodawane po nazwie metody aby wskazać, że metody są przedmiotem. Jeśli zdecydujesz, aby zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy na zmiennej w kodzie, a następnie wybierz **Refaktoryzuj**, **Zmień nazwę**. Wszystkie wystąpienia tej zmiennej w kodzie są zmieniane. Zobacz [Refaktoryzacja zmiany nazwy (C#)](../csharp-ide/rename-refactoring-csharp.md) lub [Refactoring i Zmień nazwę — okno dialogowe](http://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) Aby uzyskać więcej informacji.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md).
