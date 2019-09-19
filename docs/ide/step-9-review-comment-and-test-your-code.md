---
title: Krok 9. Przeglądanie, komentowanie i testowanie kodu
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d0504f994c05ed9c924b3758a7f83838c67df44
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118723"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9. Przeglądanie, komentowanie i testowanie kodu

Następnie Dodaj komentarz do kodu. Komentarz to Uwaga, która nie zmienia sposobu zachowania aplikacji. Ułatwia to osobie odczytującej Twój kod, aby zrozumieć, co robi. Dodawanie komentarzy do kodu jest dobrym wykonywaćem do uzyskania.

W C#programie dwa ukośniki (//) oznaczają wiersz jako komentarz. W Visual Basic znak pojedynczego cudzysłowu (') służy do oznaczania linii jako komentarz. Po dodaniu komentarza Przetestuj swoją aplikację. Dobrym rozwiązaniem jest częste uruchamianie i testowanie kodu podczas pracy nad projektami, dzięki czemu możesz wychwycić i rozwiązać wszelkie problemy wcześniej, zanim kod będzie bardziej skomplikowany. Jest to nazywane *testami iteracyjnymi*.

Właśnie skompilowano coś, co działa, a chociaż nie zostało to jeszcze zrobione, może już załadować obraz. Przed dodaniem komentarza do kodu i przetestowania go, należy zapoznać się z pojęciami dotyczącymi kodu, ponieważ często będziesz używać tych koncepcji:

- Po dwukrotnym kliknięciu przycisku **Pokaż obraz** w **Projektant formularzy systemu Windows**, IDE automatycznie dodaliśmy *metodę* do kodu programu.

- Metody organizowania kodu: Jest to sposób grupowania kodu.

- W większości przypadków Metoda wykonuje niewielką liczbę rzeczy w określonej kolejności, jak `showButton_Click()` w przypadku, gdy Metoda (lub `ShowButton_Click()`) pokazuje okno dialogowe, a następnie ładuje obraz.

- Metoda składa się z *instrukcji*kodu lub wierszy kodu. Należy traktować metodę jako sposób łączenia instrukcji kodu.

- Gdy metoda jest wykonywana lub *wywoływana*, instrukcje w metodzie są wykonywane w kolejności, jeden po drugim, zaczynając od pierwszego.

   Poniżej znajduje się przykład instrukcji.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Instrukcje sprawiają, że programy działają w programie. W C#programie instrukcja zawsze jest zakończona średnikiem. Na Visual Basic końcem wiersza jest koniec instrukcji. (Nie jest wymagany średnik w Visual Basic). Poprzednia instrukcja instruuje <xref:System.Windows.Forms.PictureBox> formant do załadowania pliku wybranego przez użytkownika ze składnikiem **OpenFileDialog** .

## <a name="to-add-comments"></a>Aby dodać komentarze

1. Dodaj do kodu następujący komentarz.

    > [!IMPORTANT]
    > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Program obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń przycisku showButton jest teraz zakończony i działa. Rozpoczęto pisanie kodu, rozpoczynając `if` od instrukcji. `if` Instrukcja to sposób informowania o swojej aplikacji, "Sprawdź to i jeśli jest prawdziwe, wykonaj te akcje". W takim przypadku możesz poinstruować aplikację, aby otworzyła okno dialogowe **Otwórz plik** , a jeśli użytkownik wybierze plik i kliknie przycisk **OK** , Załaduj ten plik w elemencie **PictureBox**.

    > [!TIP]
    > Środowisko IDE zostało skompilowane, aby ułatwić pisanie kodu, a *fragmenty kodu* są jednym ze sposobów. Fragment kodu jest skrótem, który jest rozwinięty w niewielkim bloku.
    >
    >  Zobaczysz wszystkie dostępne fragmenty kodu. Na pasku menu wybierz kolejno pozycje **Narzędzia** > **fragmenty kodu Menedżer**. W C#przypadku, `if` fragment kodu znajduje się w **wizualizacji C#**  . W przypadku Visual Basic, `if` fragmenty kodu są w **warunkach i pętle** > **wzorców kodów**. Za pomocą tego menedżera można przeglądać istniejące fragmenty kodu lub dodawać własne fragmenty kodu.
    >
    >  Aby uaktywnić fragment kodu przy wpisywaniu tekstu, wpisz go i wybierz klawisz **Tab** . Wiele fragmentów kodu pojawia się w oknie **IntelliSense** , co oznacza, że wybierasz klawisz **Tab** dwa razy: najpierw, aby wybrać wstawkę z okna **IntelliSense** , a następnie wskazać, że IDE używa tego fragmentu kodu. (Technologia IntelliSense obsługuje `if` fragment kodu, ale `ifelse` nie fragment kodu).

1. Przed uruchomieniem aplikacji Zapisz aplikację, wybierając przycisk **Zapisz wszystkie** paski narzędzi, który powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express_iconsaveall.png)<br>
***Zapisz wszystko*** *przycisk*

     Alternatywnie, aby zapisać aplikację, wybierz pozycję **plik** > **Zapisz wszystko** na pasku menu (lub naciśnij **klawisze CTRL**+**SHIFT**+**S**). Najlepszym rozwiązaniem jest wczesne i częste zapisywanie.

     Po uruchomieniu program powinien wyglądać jak na poniższej ilustracji.

     ![Przeglądarka obrazów](../ide/media/express_pictureviewerdonerun.png)<br>***Przeglądarka obrazów***

## <a name="to-test-your-app"></a>Aby przetestować aplikację

1. Wybierz klawisz **F5** lub wybierz przycisk paska narzędzi **Rozpocznij debugowanie** .

1. Wybierz przycisk **Pokaż obraz** , aby uruchomić właśnie napisany kod. Najpierw aplikacja otwiera okno dialogowe **Otwórz plik** . Sprawdź, czy Twoje filtry są wyświetlane na liście rozwijanej **Pliki typu** u dołu okna dialogowego. Następnie przejdź do obrazu i otwórz go. Zwykle można znaleźć przykładowe obrazy dostarczane z systemem operacyjnym Windows w folderze *Moje dokumenty* w folderze *Moje obrazy Pictures\Sample* .

    > [!TIP]
    > Jeśli nie widzisz żadnych obrazów w oknie dialogowym **Wybierz plik obrazu** , upewnij się, że na liście rozwijanej w prawym dolnym rogu okna dialogowego jest zaznaczona opcja filtr **wszystkie pliki (\**.)** .

1. Załaduj obraz i pojawia się w elemencie PictureBox. Następnie spróbuj zmienić rozmiar formularza, przeciągając jego obramowania. Ponieważ element PictureBox jest zadokowany wewnątrz elementu TableLayoutPanel, który sam jest zadokowany w formularzu, obszar obrazu zmieni się w taki sposób, aby był tak szeroki jak formularz, i wypełni górne 90 procent formularza. Dlatego użyto <xref:System.Windows.Forms.TableLayoutPanel> kontenerów i <xref:System.Windows.Forms.FlowLayoutPanel> : Użytkownicy zachowują rozmiar formularza poprawnie, gdy zmienia jego rozmiary.

     Teraz większe obrazy wykraczają poza obramowania przeglądarki obrazów. W następnym kroku dodasz kod umożliwiający dopasowanie obrazów do okna.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz  **[krok 10: Napisz kod dla dodatkowych przycisków i pola](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** wyboru.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Napisz kod dla programu obsługi](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)zdarzeń przycisku Pokaż obraz.

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie quizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry zgodnej](tutorial-3-create-a-matching-game.md)
