---
title: Krok 1. Tworzenie projektu i Dodawanie tabeli do formularza | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bec6c539963d54bfa1d866ccc4811425bba9e3a4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068577"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Tworzenie projektu i dodawanie tabeli do formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Jeśli nie używasz programu Visual Studio Express, musisz najpierw wybrać język programowania. Z **zainstalowane szablony** , wybierz opcję **Visual C#** lub **języka Visual Basic**.  
  
3. Na liście szablonów projektu wybierz **aplikacja interfejsu Windows Forms**, nadaj projektowi nazwę **nazwę MatchingGame**, a następnie wybierz **OK** przycisku.  
  
4. W **właściwości** okna, ustaw następujące właściwości formularza.  
  
   1. Formularz zmiany **tekstu** właściwość **Form1** do **gra w dopasowywanie**. Ten tekst jest wyświetlany w górnej części okna gry.  
  
   2. Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Możesz to zrobić, ustawiając **rozmiar** właściwości **550, 550**, lub poprzez przeciąganie rogu formularza, aż zobaczysz właściwy rozmiar w prawym dolnym rogu zintegrowanego rozwoju (środowiska ŚRODOWISKO IDE).  
  
5. Wyświetl przybornik, wybierając **przybornika** karty po lewej stronie IDE.  
  
6. Przeciągnij `TableLayoutPanel` z kontrolować **kontenery** kategorii w przyborniku, a następnie ustaw następujące właściwości dla niego.  
  
   1. Ustaw **BackColor** właściwości **CornflowerBlue**. Aby to zrobić, otwórz **BackColor** okno dialogowe, wybierając strzałkę listy rozwijanej obok **BackColor** właściwość **właściwości** okna.  Następnie wybierz **Web** karcie **BackColor** okno dialogowe, aby wyświetlić listę nazw dostępnych kolorów.  
  
      > [!NOTE]
      >  Kolory nie są w kolejności alfabetycznej, a CornflowerBlue jest w dolnej części listy.  
  
   2. Ustaw **Dock** właściwości **wypełnienia** wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając duży środkowy przycisk. Tabela się rozszerza i obejmuje cały formularz.  
  
   3. Ustaw **CellBorderStyle** właściwości **Inset**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.  
  
   4. Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.  
  
   5. W menu zadań wybierz **Dodaj wiersz** dwa razy, aby dodać dwa wiersze, a następnie wybierz **Dodaj kolumnę** dwa razy, aby dodać dwie kolumny.  
  
   6. W menu zadań wybierz **Edytuj wiersze i kolumny** otworzyć **Style kolumn i wierszy** okna. Wybierz każdą z kolumn, wybierz pozycję **procent** przycisk opcji, a następnie ustaw szerokość każdej kolumny na 25 procent ogólnej szerokości. Następnie wybierz pozycję **wierszy** z listy rozwijanej w górnej części okna i Ustaw wysokość każdego wiersza na 25 procent. Gdy wszystko będzie gotowe, wybierz pozycję **OK** przycisku.  
  
      TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.  
  
7. Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, powinien zostać wyświetlony **tableLayoutPanel1** w górnej części **właściwości** okna. Jeśli nie jest zaznaczone, wybierz TableLayoutPanel na formularzu lub wybierz go z rozwijanej listy formantów u góry **właściwości** okna.  
  
    Gdy TableLayoutPanel jest zaznaczony, Otwórz przybornik i Dodaj **etykiety** kontroli (znajdujący się w **wspólnych formantów** kategoria) do lewej górnej komórki TableLayoutPanel. `Label` Kontroli powinny teraz być zaznaczone w środowisku IDE. Ustaw dla niego następujące właściwości.  
  
   1. Upewnij się, że etykiety **BackColor** właściwość jest ustawiona na **CornflowerBlue**.  
  
   2. Ustaw **AutoSize** właściwości **False**.  
  
   3. Ustaw **Dock** właściwości **wypełnienia**.  
  
   4. Ustaw **TextAlign** właściwości **MiddleCenter** , wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowy przycisk. Gwarantuje to, że ikona pojawia się w środku komórki.  
  
   5. Wybierz **czcionki** właściwości. Powinien pojawić się przycisk wielokropka (...).  
  
   6. Wybierz przycisk wielokropka i ustaw **czcionki** wartość **Webdings**, **styl czcionki** do **Bold**i **rozmiar** do **72**.  
  
   7. Ustaw **tekstu** właściwość etykiety na literę **c**.  
  
        Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.  
  
       > [!NOTE]
       >  Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast umieszczać **c** w **tekstu** właściwość, spróbuj wprowadzić różne litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.  
  
8. Wybierz formant etykiety i skopiuj go do następnej komórki w TableLayoutPanel. (Wybierz klawisze Ctrl + C lub na pasku menu wybierz **Edytuj**, **kopiowania**.) Następnie wklej go. (Wybierz klawisze Ctrl + V lub na pasku menu wybierz **Edytuj**, **Wklej**.) W drugiej komórce TableLayoutPanel pojawi się kopia pierwszej etykiety. Wklej ją ponownie, w trzeciej komórce pojawi się kolejna etykieta. Wklejaj `Label` kontroluje, aż wszystkie komórki zostaną wypełnione.  
  
   > [!NOTE]
   >  Jeśli wkleisz zbyt wiele razy, IDE doda nowy wiersz do TableLayoutPanel, aby zrobić miejsce na dodanie nowego formantu etykiety. Można cofnąć tę operację. Aby usunąć nową komórkę, wybierz klawisze Ctrl + Z lub na pasku menu wybierz **Edytuj**, **Cofnij**.  
  
    Teraz formularz jest rozmieszczony. Powinien wyglądać tak, jak na poniższej ilustracji:  
  
    ![Początkowy formularz gry w dopasowywanie](../ide/media/express-tut4step1.png "Express_Tut4Step1")  
   Początkowy formularz gry w dopasowywanie  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
- Aby powrócić do tematu przeglądu, zobacz [Tutorial 3: Stwórz grę pasujący obiekt typu](../ide/tutorial-3-create-a-matching-game.md).
