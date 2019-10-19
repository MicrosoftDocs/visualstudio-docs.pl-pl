---
title: Krok 9. przeglądanie, komentowanie i testowanie kodu
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
ms.openlocfilehash: 39be6feffb70dd43823af2af0fce719daafc6f78
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572486"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9. przeglądanie, komentowanie i testowanie kodu

Następnie Dodaj komentarz do kodu. Komentarz to Uwaga, która nie zmienia sposobu zachowania aplikacji. Ułatwia to osobie odczytującej Twój kod, aby zrozumieć, co robi. Dodawanie komentarzy do kodu jest dobrym wykonywaćem do uzyskania.

W C#programie dwa ukośniki (//) oznaczają wiersz jako komentarz. W Visual Basic znak pojedynczego cudzysłowu (') służy do oznaczania linii jako komentarz. Po dodaniu komentarza Przetestuj swoją aplikację. Dobrym rozwiązaniem jest częste uruchamianie i testowanie kodu podczas pracy nad projektami, dzięki czemu możesz wychwycić i rozwiązać wszelkie problemy wcześniej, zanim kod będzie bardziej skomplikowany. Jest to nazywane *testami iteracyjnymi*.

Właśnie skompilowano coś, co działa, a chociaż nie zostało to jeszcze zrobione, może już załadować obraz. Przed dodaniem komentarza do kodu i przetestowania go, należy zapoznać się z pojęciami dotyczącymi kodu, ponieważ często będziesz używać tych koncepcji:

- Po dwukrotnym kliknięciu przycisku **Pokaż obraz** w **Projektant formularzy systemu Windows**, IDE automatycznie dodaliśmy *metodę* do kodu programu.

- Metody służą do organizowania kodu: jest to sposób, w jaki kod jest zgrupowany.

- W większości przypadków Metoda wykonuje niewielką liczbę elementów w określonej kolejności, jak Metoda `showButton_Click()` (lub `ShowButton_Click()`) wyświetla okno dialogowe, a następnie ładuje obraz.

- Metoda składa się z *instrukcji*kodu lub wierszy kodu. Należy traktować metodę jako sposób łączenia instrukcji kodu.

- Gdy metoda jest wykonywana lub *wywoływana*, instrukcje w metodzie są wykonywane w kolejności, jeden po drugim, zaczynając od pierwszego.

   Poniżej znajduje się przykład instrukcji.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Instrukcje sprawiają, że programy działają w programie. W C#programie instrukcja zawsze jest zakończona średnikiem. Na Visual Basic końcem wiersza jest koniec instrukcji. (Nie jest wymagany średnik w Visual Basic). Poprzednia instrukcja nakazuje formantowi <xref:System.Windows.Forms.PictureBox> załadować plik, który użytkownik wybrał ze składnika **OpenFileDialog** .

## <a name="to-add-comments"></a>Aby dodać komentarze

1. Dodaj do kodu następujący komentarz.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> przycisku **showButton** jest teraz zakończony i działa. Rozpoczęto pisanie kodu, rozpoczynając od instrukcji `if`. Instrukcją `if` jest sposób informowania swojej aplikacji, "Sprawdź to i jeśli prawda, wykonaj te akcje". W takim przypadku możesz poinstruować aplikację, aby otworzyła okno dialogowe **Otwórz plik** , a jeśli użytkownik wybierze plik i kliknie przycisk **OK** , Załaduj ten plik w elemencie **PictureBox**.

    > [!TIP]
    > Środowisko IDE zostało skompilowane, aby ułatwić pisanie kodu, a *fragmenty kodu* są jednym ze sposobów. Fragment kodu jest skrótem, który jest rozwinięty w niewielkim bloku.
    >
    >  Zobaczysz wszystkie dostępne fragmenty kodu. Na pasku menu wybierz kolejno opcje **narzędzia**  > **kod fragmenty kodu**. W C#przypadku, fragment `if` znajduje się **w C# wizualizacji** . W przypadku Visual Basic fragmenty kodu `if` znajdują się w **wzorcach** ,  > **warunkowe i pętle**. Za pomocą tego menedżera można przeglądać istniejące fragmenty kodu lub dodawać własne fragmenty kodu.
    >
    >  Aby uaktywnić fragment kodu przy wpisywaniu tekstu, wpisz go i wybierz klawisz **Tab** . Wiele fragmentów kodu pojawia się w oknie **IntelliSense** , co oznacza, że wybierasz klawisz **Tab** dwa razy: najpierw, aby wybrać wstawkę z okna **IntelliSense** , a następnie wskazać, że IDE używa tego fragmentu kodu. (Technologia IntelliSense obsługuje fragment kodu `if`, ale nie fragment `ifelse`).

1. Przed uruchomieniem aplikacji Zapisz aplikację, wybierając przycisk **Zapisz wszystkie** paski narzędzi, który powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Save wszystkie przyciski paska narzędzi ](../ide/media/express_iconsaveall.png)<br>
*Przycisk* ***Zapisz wszystko***

     Alternatywnie, aby zapisać aplikację, wybierz pozycję **plik**  > **Zapisz wszystko** na pasku menu (lub naciśnij klawisz **Ctrl** +**SHIFT** +**S**). Najlepszym rozwiązaniem jest wczesne i częste zapisywanie.

     Po uruchomieniu program powinien wyglądać jak na poniższej ilustracji.

     ](../ide/media/express_pictureviewerdonerun.png) przeglądarka ![Picture<br>***Przeglądarka obrazów***

## <a name="to-test-your-app"></a>Aby przetestować aplikację

1. Wybierz klawisz **F5** lub wybierz przycisk paska narzędzi **Rozpocznij debugowanie** .

1. Wybierz przycisk **Pokaż obraz** , aby uruchomić właśnie napisany kod. Najpierw aplikacja otwiera okno dialogowe **Otwórz plik** . Sprawdź, czy Twoje filtry są wyświetlane na liście rozwijanej **Pliki typu** u dołu okna dialogowego. Następnie przejdź do obrazu i otwórz go. Zwykle można znaleźć przykładowe obrazy dostarczane z systemem operacyjnym Windows w folderze *Moje dokumenty* w folderze *Moje obrazy Pictures\Sample* .

    > [!TIP]
    > Jeśli nie widzisz żadnych obrazów w oknie dialogowym **Wybierz plik obrazu** , upewnij się, że na liście rozwijanej w prawym dolnym rogu okna dialogowego jest zaznaczone pole wyboru **wszystkie pliki (*. \*)** .

1. Załaduj obraz i pojawia się w elemencie PictureBox. Następnie spróbuj zmienić rozmiar formularza, przeciągając jego obramowania. Ponieważ element PictureBox jest zadokowany wewnątrz elementu TableLayoutPanel, który sam jest zadokowany w formularzu, obszar obrazu zmieni się w taki sposób, aby był tak szeroki jak formularz, i wypełni górne 90 procent formularza. Dlatego zostały użyte <xref:System.Windows.Forms.TableLayoutPanel> i kontenery <xref:System.Windows.Forms.FlowLayoutPanel>: zachowują rozmiar formularza poprawnie, gdy użytkownik zmienia jego rozmiary.

     Teraz większe obrazy wykraczają poza obramowania przeglądarki obrazów. W następnym kroku dodasz kod umożliwiający dopasowanie obrazów do okna.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** .

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Zobacz także

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
