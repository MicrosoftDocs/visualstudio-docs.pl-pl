---
title: Krok 9. przeglądanie, komentowanie i testowanie kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7fc6f29246f90c47a4c59a5ae6bb1999ceac72bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646907"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9. Przejrzenie, komentowanie i testowanie kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następnie Dodaj komentarz do kodu. Komentarz to Uwaga, która nie zmienia sposobu zachowania programu. Ułatwia to osobie odczytującej Twój kod, aby zrozumieć, co robi. Dodawanie komentarzy do kodu jest dobrym wykonywaćem do uzyskania. W wizualizacji C#dwa ukośniki (//) oznaczają wiersz jako komentarz. W Visual Basic znak pojedynczego cudzysłowu (') służy do oznaczania linii jako komentarz. Po dodaniu komentarza Przetestuj swój program. Dobrym rozwiązaniem jest częste uruchamianie i testowanie kodu podczas pracy nad projektami, dzięki czemu możesz wychwycić i rozwiązać wszelkie problemy wcześniej, zanim kod będzie bardziej skomplikowany. Jest to nazywane *testami iteracyjnymi*.

 Właśnie skompilowano coś, co działa, a chociaż nie zostało to jeszcze zrobione, może już załadować obraz. Przed dodaniem komentarza do kodu i przetestowania go, należy zapoznać się z pojęciami dotyczącymi kodu, ponieważ często będziesz używać tych koncepcji:

- Po dwukrotnym kliknięciu przycisku **Pokaż obraz** w Projektant formularzy systemu Windows, IDE automatycznie dodaliśmy *metodę* do kodu programu.

- Metody służą do organizowania kodu: jest to sposób, w jaki kod jest zgrupowany.

- W większości przypadków Metoda wykonuje niewielką liczbę rzeczy w określonej kolejności, podobnie jak Metoda `showButton_Click()` wyświetla okno dialogowe, a następnie ładuje obraz.

- Metoda składa się z *instrukcji*kodu lub wierszy kodu. Należy traktować metodę jako sposób łączenia instrukcji kodu.

- Gdy metoda jest wykonywana lub *wywoływana*, instrukcje w metodzie są wykonywane w kolejności, jeden po drugim, zaczynając od pierwszego.

   Poniżej znajduje się przykład instrukcji.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Instrukcje sprawiają, że programy działają w programie. W wizualizacji C#, instrukcja zawsze jest zakończona średnikiem. Na Visual Basic końcem wiersza jest koniec instrukcji. (Nie jest wymagany średnik w Visual Basic). Poprzednia instrukcja nakazuje formantowi `PictureBox` załadować plik, który użytkownik wybrał ze składnika **OpenFileDialog** .

  ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# pliku wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-add-comments"></a>Aby dodać komentarze

1. Dodaj do kodu następujący komentarz.

     [!code-csharp[VbExpressTutorial1Step9_10#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step9_10#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#1)]

    > [!NOTE]
    > Procedura obsługi zdarzeń kliknięcia przycisku **showButton** jest teraz zakończona i działa. Rozpoczęto pisanie kodu, rozpoczynając od instrukcji `if`. Instrukcją `if` jest sposób informowania programu, "Sprawdź to i jeśli jest prawdziwe, wykonaj te akcje". W takim przypadku Użytkownik poinformuje program, aby otworzył okno dialogowe **Otwórz plik** , a jeśli użytkownik wybierze plik, a następnie kliknie przycisk **OK** , Załaduj ten plik w elemencie PictureBox.

    > [!TIP]
    > Środowisko IDE zostało skompilowane, aby ułatwić pisanie kodu, a *fragmenty kodu* są jednym ze sposobów. Fragment kodu jest skrótem, który jest rozwinięty w niewielkim bloku.
    >
    >  Zobaczysz wszystkie dostępne fragmenty kodu. Na pasku menu wybierz kolejno opcje **Narzędzia**i **Code wstaweks Manager**. Dla wizualizacji C#`if` fragment kodu znajduje się **w C# wizualizacji** . W przypadku Visual Basic, fragmenty kodu `if` są w wyrażeniach **warunkowych i pętli, a** **wzorce kodowe**. Za pomocą tego menedżera można przeglądać istniejące fragmenty kodu lub dodawać własne fragmenty kodu.
    >
    >  Aby uaktywnić fragment kodu przy wpisywaniu tekstu, wpisz go i wybierz klawisz TAB. Wiele fragmentów kodu pojawia się w oknie **IntelliSense** , co oznacza, że wybierasz klawisz Tab dwa razy: najpierw, aby wybrać wstawkę z okna **IntelliSense** , a następnie wskazać, że IDE używa tego fragmentu kodu. (Technologia IntelliSense obsługuje fragment kodu `if`, ale nie fragment `ifelse`).

2. Przed uruchomieniem programu Zapisz swój program, wybierając przycisk **Zapisz wszystkie** paski narzędzi, który pojawia się w następujący sposób.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Przycisk Zapisz wszystko

     Alternatywnie, aby zapisać program, na pasku menu wybierz **plik**, **Zapisz wszystko**. Najlepszym rozwiązaniem jest wczesne i częste zapisywanie.

     Po uruchomieniu program powinien wyglądać jak na poniższej ilustracji.

     ![Przeglądarka obrazów](../ide/media/express-pictureviewerdonerun.png "Express_PictureViewerDoneRun") Przeglądarka obrazów

### <a name="to-test-your-program"></a>Aby przetestować program

1. Wybierz klawisz F5 lub wybierz przycisk paska narzędzi **Rozpocznij debugowanie** .

2. Wybierz przycisk **Pokaż obraz** , aby uruchomić właśnie napisany kod. Po pierwsze program otwiera okno dialogowe **Otwórz plik** . Sprawdź, czy Twoje filtry są wyświetlane na liście rozwijanej **Pliki typu** u dołu okna dialogowego. Następnie przejdź do obrazu i otwórz go. Zwykle można znaleźć przykładowe obrazy dostarczane z systemem operacyjnym Windows w folderze **Moje dokumenty** w folderze **Moje obrazy Pictures\Sample** .

    > [!NOTE]
    > Jeśli nie widzisz żadnych obrazów w oknie dialogowym **Wybierz plik obrazu** , upewnij się, że "wszystkie pliki (*. \*) "filtr jest zaznaczony na liście rozwijanej po prawej stronie okna dialogowego.

3. Załaduj obraz i pojawia się w elemencie PictureBox. Następnie spróbuj zmienić rozmiar formularza, przeciągając jego obramowania. Ponieważ element PictureBox jest zadokowany wewnątrz elementu TableLayoutPanel, który sam jest zadokowany w formularzu, obszar obrazu zmieni się w taki sposób, aby był tak szeroki jak formularz, i wypełni górne 90 procent formularza. To dlatego, że użyto kontenerów TableLayoutPanel i FlowLayoutPanel: zachowują rozmiar formularza poprawnie, gdy użytkownik zmienia jego rozmiary.

     Teraz większe obrazy wykraczają poza obramowania przeglądarki obrazów. W następnym kroku dodasz kod umożliwiający dopasowanie obrazów do okna.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).
