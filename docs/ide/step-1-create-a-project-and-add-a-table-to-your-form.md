---
title: Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bac96a61a5c071a01f1584911ba41cd84e87da7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979562"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza

::: moniker range="vs-2017"

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

::: moniker-end

::: moniker range="vs-2019"

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

1. Wybierz pozycję w polu wyszukiwania wpisz "WPF" **aplikacja WPF (.NET Framework)**, a następnie wybierz **dalej**.

   (Jeśli nie widzisz **aplikacja WPF (.NET Framework)** szablon, użyj Instalatora programu Visual Studio, aby zainstalować **programowanie aplikacji klasycznych dla platformy .NET** obciążenia.)

1. Nazwij projekt, **nazwę MatchingGame**i wybierz polecenie **Create**

::: moniker-end

2. Jeśli nie używasz programu Visual Studio Express, musisz najpierw wybrać język programowania. Z **zainstalowane szablony** , wybierz opcję **Visual C#** lub **języka Visual Basic**.

3. Na liście szablonów projektu wybierz **aplikacja interfejsu Windows Forms**, nadaj projektowi nazwę **nazwę MatchingGame**, a następnie wybierz **OK** przycisku.

4. W **właściwości** okna, ustaw następujące właściwości formularza.

   1. Formularz zmiany **tekstu** właściwość **Form1** do **gra w dopasowywanie**. Ten tekst jest wyświetlany w górnej części okna gry.

   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Możesz to zrobić, ustawiając **rozmiar** właściwości **550, 550**, lub poprzez przeciąganie rogu formularza, aż zobaczysz właściwy rozmiar w prawym dolnym rogu zintegrowanego rozwoju (środowiska ŚRODOWISKO IDE).

5. Wyświetl przybornik, wybierając **przybornika** karty po lewej stronie IDE.

6. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **kontenery** kategorii w przyborniku, a następnie ustaw następujące właściwości dla niego.

   1. Ustaw **BackColor** właściwości **CornflowerBlue**. Aby to zrobić, otwórz **BackColor** okno dialogowe, wybierając strzałkę listy rozwijanej obok **BackColor** właściwość **właściwości** okna.  Następnie wybierz **Web** karcie **BackColor** okno dialogowe, aby wyświetlić listę nazw dostępnych kolorów.

      > [!NOTE]
      > Kolory nie są w kolejności alfabetycznej, a **CornflowerBlue** znajduje się w pobliżu dolnej części listy.

   2. Ustaw **Dock** właściwości **wypełnienia** wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając duży środkowy przycisk. Tabela się rozszerza i obejmuje cały formularz.

   3. Ustaw **CellBorderStyle** właściwości **Inset**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.

   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.

   5. W menu zadań wybierz **Dodaj wiersz** dwa razy, aby dodać dwa wiersze, a następnie wybierz **Dodaj kolumnę** dwa razy, aby dodać dwie kolumny.

   6. W menu zadań wybierz **Edytuj wiersze i kolumny** otworzyć **Style kolumn i wierszy** okna. Wybierz każdą z kolumn, wybierz pozycję **procent** przycisk opcji, a następnie ustaw szerokość każdej kolumny na 25 procent ogólnej szerokości. Następnie wybierz pozycję **wierszy** z listy rozwijanej w górnej części okna i Ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz pozycję **OK** przycisku.

      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.

7. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, powinien zostać wyświetlony **tableLayoutPanel1** w górnej części **właściwości** okna. Jeśli nie jest zaznaczone, wybierz TableLayoutPanel na formularzu lub wybierz go z rozwijanej listy formantów u góry **właściwości** okna.

    Gdy TableLayoutPanel jest zaznaczony, Otwórz przybornik i Dodaj <xref:System.Windows.Forms.Label> kontroli (znajdujący się w **wspólnych formantów** kategoria) do lewej górnej komórki TableLayoutPanel. Formant etykiety powinny teraz być zaznaczone w środowisku IDE. Ustaw dla niego następujące właściwości.

   1. Upewnij się, że etykiety **BackColor** właściwość jest ustawiona na **CornflowerBlue**.

   2. Ustaw **AutoSize** właściwości **False**.

   3. Ustaw **Dock** właściwości **wypełnienia**.

   4. Ustaw **TextAlign** właściwości **MiddleCenter** , wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.

   5. Wybierz **czcionki** właściwości. Wielokropek (**...** ) powinien pojawić się przycisk.

   6. Wybierz przycisk wielokropka i ustaw **czcionki** wartość **Webdings**, **styl czcionki** do **Bold**i **rozmiar** do **48**.

   7. Ustaw **tekstu** właściwość etykiety na literę **c**.

        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.

       > [!NOTE]
       > Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** w **tekstu** właściwość, spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.

8. Wybierz formant etykiety i skopiuj go do następnej komórki w TableLayoutPanel. (Wybierz **Ctrl**+**C** kluczy lub na pasku menu wybierz **Edytuj** > **kopiowania**.) Następnie wklej go. (Wybierz **Ctrl**+**V** kluczy lub na pasku menu wybierz **Edytuj** > **Wklej**.) W drugiej komórce TableLayoutPanel pojawi się kopia pierwszej etykiety. Wklej ją ponownie, a inny etykieta jest wyświetlana w trzeciej komórce. Wklejaj formanty etykiet, aż wszystkie komórki zostaną wypełnione.

   > [!NOTE]
   > Jeśli wkleisz zbyt wiele razy, IDE doda nowy wiersz do TableLayoutPanel, tak, aby miało miejsce na dodanie nowego formantu etykiety. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz **Ctrl**+**Z** kluczy lub na pasku menu wybierz **Edytuj** > **Cofnij**.

    Teraz formularz jest rozmieszczony. Powinien wyglądać tak, jak na poniższej ilustracji:

    ![Początkowy formularz gry w dopasowywanie](../ide/media/express_tut4step1.png) początkowy formularz gry w dopasowywanie

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Dodawanie obiektu Random i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Aby powrócić do tematu przeglądu, zobacz [Tutorial 3: Utwórz pasujący obiekt typu gier](../ide/tutorial-3-create-a-matching-game.md).
