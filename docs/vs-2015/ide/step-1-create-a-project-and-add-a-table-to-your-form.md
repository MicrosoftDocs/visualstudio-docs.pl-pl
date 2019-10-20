---
title: Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a7f9930dc1619d6f35a6024bd0f754f7caeeb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643503"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Utworzenie projektu i dodawanie tabeli do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. Jeśli nie używasz programu Visual Studio Express, musisz najpierw wybrać język programowania. Z listy **zainstalowane szablony** wybierz pozycję **Visual C#**  lub **Visual Basic**.

3. Na liście szablonów projektu wybierz pozycję **Windows Forms aplikacja**, nazwij projekt **MatchingGame**, a następnie wybierz przycisk **OK** .

4. W oknie **Właściwości** ustaw następujące właściwości formularza.

   1. Zmień właściwość **Text** formularza z **Form1** na **pasującą grę**. Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Można to zrobić, ustawiając właściwość **size** na **550, 550**lub przeciągając róg formularza do momentu, gdy zobaczysz właściwy rozmiar w prawym dolnym rogu zintegrowanego środowiska programistycznego (IDE).

5. Wyświetl Przybornik, wybierając kartę **Przybornik** po lewej stronie IDE.

6. Przeciągnij formant `TableLayoutPanel` z kategorii **kontenery** w przyborniku, a następnie ustaw dla niego następujące właściwości.

   1. Ustaw właściwość **BackColor** na **CornflowerBlue**. Aby to zrobić, Otwórz okno dialogowe **BackColor** , wybierając strzałkę listy rozwijanej obok właściwości **BackColor** w oknie **Właściwości** .  Następnie wybierz kartę **Sieć Web** w oknie dialogowym **BackColor** , aby wyświetlić listę dostępnych nazw kolorów.

      > [!NOTE]
      > Kolory nie są w kolejności alfabetycznej, a CornflowerBlue jest w dolnej części listy.

   2. Ustaw właściwość **Dock** na wartość **Fill** , wybierając przycisk listy rozwijanej obok właściwości i wybierając przycisk z dużymi środkami. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw właściwość **CellBorderStyle** na wartość **Wstaw**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadania wybierz dwa razy **Dodaj wiersz** , aby dodać dwa wiersze, a następnie wybierz dwa razy **Dodaj kolumnę** , aby dodać dwie kolumny.

   6. W menu zadania wybierz polecenie **Edytuj wiersze i kolumny** , aby otworzyć okno **Style kolumn i wierszy** . Wybierz każdą z kolumn, wybierz przycisk opcji **procent** , a następnie ustaw szerokość każdej kolumny na 25 procent całkowitej szerokości. Następnie wybierz pozycję **wiersze** w polu listy rozwijanej w górnej części okna, a następnie ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz przycisk **OK** .

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

7. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, należy zobaczyć **tableLayoutPanel1** w górnej części okna **Właściwości** . Jeśli nie jest zaznaczone, wybierz TableLayoutPanel w formularzu lub wybierz go w kontrolce menu rozwijanego u góry okna **Właściwości** .

    Gdy TableLayoutPanel jest zaznaczone, Otwórz przybornik i Dodaj kontrolkę **etykieta** (znajdującą się w kategorii **Formanty standardowe** ) do lewej górnej komórki TableLayoutPanel. Kontrolka `Label` powinna być teraz zaznaczona w IDE. Ustaw dla niego następujące właściwości.

   1. Upewnij się, że właściwość " **BackColor** " etykiety jest ustawiona na **CornflowerBlue**.

   2. Ustaw właściwość **AutoSize** na **false**.

   3. Ustaw właściwość **Dock** na **Fill**.

   4. Ustaw właściwość **TextAlign** na **MiddleCenter** , wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz właściwość **Font** . Powinien pojawić się przycisk wielokropka (...).

   6. Wybierz przycisk wielokropka, a następnie ustaw wartość **czcionki** na **Webdings**, **styl czcionki** na **pogrubiony**, a **rozmiar** na **72**.

   7. Ustaw właściwość **Text** etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** we właściwości **Text** , spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

8. Wybierz formant etykiety i skopiuj go do następnej komórki w TableLayoutPanel. (Wybierz klawisze CTRL + C lub na pasku menu wybierz **Edytuj**, **Kopiuj**). Następnie wklej go. (Wybierz klawisze CTRL + V lub na pasku menu wybierz polecenie **Edytuj**, **Wklej**). Kopia pierwszej etykiety pojawia się w drugiej komórce TableLayoutPanel. Wklej ją ponownie, w trzeciej komórce pojawi się kolejna etykieta. Kontynuuj wklejanie `Label` kontrolek do momentu wypełnienia wszystkich komórek.

   > [!NOTE]
   > Jeśli wkleisz zbyt wiele razy, IDE doda nowy wiersz do TableLayoutPanel, aby zrobić miejsce na dodanie nowego formantu etykiety. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz klawisze Ctrl + Z lub na pasku menu wybierz polecenie **Edytuj**, **Cofnij**.

    Teraz formularz został rozłożony. Powinien wyglądać tak, jak na poniższej ilustracji.

    ![Początkowy pasujący formularz gry](../ide/media/express-tut4step1.png "Express_Tut4Step1") Początkowy pasujący formularz gry

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2. Dodawanie losowego obiektu i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Aby powrócić do tematu przeglądu, zobacz [samouczek 3: Tworzenie gry w dopasowywanie](../ide/tutorial-3-create-a-matching-game.md).
