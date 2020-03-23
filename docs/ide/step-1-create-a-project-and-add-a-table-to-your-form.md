---
title: 'Krok 1: Tworzenie projektu i dodawanie tabeli do formularza'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1134fb5bb02bd8c78f347ef582f12da35074c36
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579921"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1: Tworzenie projektu i dodawanie tabeli do formularza

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. Wybierz pozycję **Visual C#** lub **Visual Basic** po lewej stronie okna dialogowego Nowy **projekt,** a następnie wybierz pozycję **Pulpit systemu Windows**.

1. Na liście szablonów wybierz szablon **aplikacji Windows Forms App (.NET Framework),** nazwij go *MatchingGame*, a następnie wybierz przycisk **OK.**

    Zostanie wyświetlony formularz o nazwie *Form1.cs* lub *Form1.vb,* w zależności od wybranego języka programowania.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji Windows Forms App (.NET Framework),** użyj Instalatora programu Visual Studio, aby zainstalować obciążenie **programowe .NET dla deweloperów pulpitu.**<br/><br/>![Obciążenie programistyczne pulpitu .NET w Instalatorze programu Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Aby uzyskać więcej informacji, zobacz stronę [Instalowanie programu Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *formularze systemu Windows* w polu wyszukiwania. Następnie wybierz pozycję **Pulpit** z listy **Typu projektu.**

   Po zastosowaniu filtru **typu projektu** wybierz szablon aplikacji Windows Forms **App (.NET Framework)** dla języka C# lub Visual Basic, a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# lub Visual Basic dla aplikacji Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Jeśli nie jest wyświetlany szablon **aplikacji Windows Forms App (.NET Framework),** można go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Następnie w Instalatorze programu Visual Studio wybierz zadanie **tworzenia pulpitu .NET.**
   >
   > ![Obciążenie rdzenia .NET w Instalatorze programu Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie.

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MatchingGame* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Aby ustawić właściwości formularza

1. W oknie **Właściwości** ustaw następujące właściwości formularza.

   1. Zmień właściwość **Tekst** formularza z **Form1** na **Pasująca gra**. Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Można to zrobić, ustawiając **Size** właściwości **na 550, 550**, lub przeciągając rogu formularza, aż zobaczysz poprawny rozmiar w prawym dolnym rogu zintegrowanego środowiska programistycznego (IDE).

2. Wyświetl przybornik, wybierając kartę **Przybornik** po lewej stronie IDE.

3. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> formant z **kategorii Kontenery** w przyborniku, a następnie ustaw dla niego następujące właściwości.

   1. Ustaw **właściwość BackColor** na **ChaflowerBlue**. Aby to zrobić, otwórz okno dialogowe **BackColor,** wybierając strzałkę rozwijaną obok właściwości **BackColor** w oknie **Właściwości.**  Następnie wybierz kartę **Sieć Web** w oknie dialogowym **BackColor,** aby wyświetlić listę dostępnych nazw kolorów.

      > [!NOTE]
      > Kolory nie są w porządku alfabetycznym, a **ChabererBlue** znajduje się w dolnej części listy.

   2. Ustaw **Dock** właściwość **wypełnić,** wybierając przycisk rozwijany obok właściwości i wybierając duży środkowy przycisk. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw **właściwość CellBorderStyle** na **Wstawka**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadań wybierz polecenie **Dodaj** wiersz dwa razy, aby dodać dwa kolejne wiersze, a następnie wybierz pozycję **Dodaj kolumnę** dwa razy, aby dodać dwie kolejne kolumny.

   6. W menu zadań wybierz polecenie **Edytuj wiersze i kolumny,** aby otworzyć okno **Style kolumn i wierszy.** Wybierz każdą z kolumn, wybierz przycisk opcji **Procent,** a następnie ustaw szerokość każdej kolumny na 25 procent całkowitej szerokości. Następnie wybierz **pozycję Wiersze** z pola rozwijanego w górnej części okna i ustaw wysokość każdego wiersza na 25 procent. Po zakończeniu wybierz przycisk **OK.**

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

4. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, powinieneś zobaczyć **tabelęLayoutPanel1** w górnej części okna **Właściwości.** Jeśli nie jest zaznaczona, wybierz TableLayoutPanel w formularzu lub wybierz go w formancie rozwijanym w górnej części okna **Właściwości.**

    Gdy pole TableLayoutPanel jest zaznaczone, otwórz <xref:System.Windows.Forms.Label> przybornik i dodaj formant (znajdujący się w kategorii **Typowe formanty)** do lewej górnej komórki tablelayoutPanel. Formant etykiety powinny być teraz wybrane w IDE. Ustaw dla niego następujące właściwości.

   1. Upewnij się, że właściwość **BackColor** etykiety jest ustawiona na **ChaflowerBlue**.

   2. Ustaw właściwość **AutoSize** na **False**.

   3. Ustaw właściwość **Dock** na **Wypełnienie**.

   4. Ustaw **TextAlign** właściwość **MiddleCenter,** wybierając przycisk rozwijany obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz **Font** właściwości. Powinien pojawić się przycisk wielokropek (**...**).

   6. Wybierz przycisk wielokropka i ustaw wartość **Czcionka** na **Webdings**, **Styl czcionki** na **Pogrubienie**i **Rozmiar** na **48**.

   7. Ustaw **właściwość Text** etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** w **Text** właściwości, spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

5. Wybierz formant Label i skopiuj go do następnej komórki w tablelayoutPanel. (Wybierz **klawisze Ctrl**+**C** lub na pasku menu wybierz pozycję **Edytuj** > **kopię).** Następnie wklej go. (Wybierz klawisze **Ctrl**+**V** lub na pasku menu wybierz pozycję **Edytuj** > **wklej).** Kopia pierwszej etykiety pojawi się w drugiej komórce tablelayoutPanel. Wklej go ponownie, a w trzeciej komórce pojawi się inna etykieta. Kontynuuj wklejanie kontrolek Etykiet, dopóki wszystkie komórki nie zostaną wypełnione.

   > [!NOTE]
   > Jeśli wklejasz zbyt wiele razy, IDE dodaje nowy wiersz do TableLayoutPanel, dzięki czemu ma miejsce, aby dodać nowy formant label. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz klawisze **Ctrl**+**Z** lub na pasku menu wybierz polecenie **Edytuj** > **cofnij**.

    Teraz formularz jest ułożony. Powinien wyglądać podobnie do poniższego zdjęcia.

    ![Początkowy formularz gry w dopasowywanie](../ide/media/express_tut4step1.png)<br/>*Początkowy formularz gry w dopasowywanie*

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Krok 2: Dodawanie obiektu Random i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Aby powrócić do tematu przeglądu, zobacz [Samouczek 3: Tworzenie pasującej gry](../ide/tutorial-3-create-a-matching-game.md).
