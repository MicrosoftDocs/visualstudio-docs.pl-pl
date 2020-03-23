---
title: 'Krok 9: Przejrzyj, komentuj i przetestuj swój kod'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b31532bf6c26512e471ee787dc7219620e6db62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579748"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9: Przejrzyj, komentuj i przetestuj swój kod

Następnie dodaj komentarz do kodu. Komentarz to notatka, która nie zmienia zachowania aplikacji. Ułatwia to osobie, która czyta twój kod, zrozumienie, co robi. Dodawanie komentarzy do kodu jest dobrym nawykiem, aby dostać się do.

W języku C# dwa ukośniki do przodu (//) oznaczają wiersz jako komentarz. W języku Visual Basic pojedynczy cudzysłów (') jest używany do oznaczania wiersza jako komentarza. Po dodaniu komentarza należy przetestować aplikację. Jest dobrą praktyką, aby często uruchamiać i testować kod podczas pracy nad projektami, dzięki czemu można złapać i rozwiązać wszelkie problemy wcześnie, zanim kod staje się bardziej skomplikowane. Nazywa się to *testowaniem iteracyjnym*.

Po prostu zbudowałeś coś, co działa, i chociaż nie jest jeszcze zrobione, może już załadować obraz. Przed dodaniem komentarza do kodu i przetestowaniem go, poświęć trochę czasu, aby przejrzeć pojęcia kodu, ponieważ często użyjesz tych pojęć:

- Po **dwukrotnym** kliknięciu przycisku Pokaż obraz w programie Windows **Forms Designer**ide automatycznie dodał *metodę* do kodu programu.

- Metody są jak zorganizować kod: Jest to, jak kod jest zgrupowany.

- W większości przypadków metoda wykonuje niewielką liczbę czynności w określonej `showButton_Click()` kolejności, na przykład sposób, w jaki metoda (lub) `ShowButton_Click()`pokazuje okno dialogowe, a następnie ładuje obraz.

- Metoda składa się z *instrukcji*kodu lub wierszy kodu. Pomyśl o metodzie jako sposób łączenia instrukcji kodu razem.

- Gdy metoda jest wykonywana lub *wywoływana*, instrukcje w metodzie są wykonywane w kolejności, jeden po drugim, począwszy od pierwszego.

   Poniżej przedstawiono przykład instrukcji.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Oświadczenia są tym, co sprawia, że twoje programy robią rzeczy. W języku C# instrukcja zawsze kończy się średnikiem. W języku Visual Basic koniec wiersza jest końcem instrukcji. (W języku Visual Basic nie jest potrzebny średnik). Poprzednia instrukcja <xref:System.Windows.Forms.PictureBox> informuje formant, aby załadować plik wybrany przez użytkownika ze składnikiem **OpenFileDialog.**

## <a name="to-add-comments"></a>Aby dodać komentarze

1. Dodaj następujący komentarz do kodu.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Program obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń przycisku **showButton** został ukończony i działa. Rozpoczęto pisanie kodu, począwszy od instrukcji. `if` Instrukcja `if` jest jak powiedzieć aplikacji, "Sprawdź to jedno, a jeśli to prawda, wykonaj te czynności." W takim przypadku należy poinformować aplikację o otwarciu okna dialogowego **Otwórz plik,** a jeśli użytkownik wybierze plik i wybierze przycisk **OK,** wczytaj ten plik w **polu PictureBox**.

    > [!TIP]
    > IDE jest zbudowany, aby ułatwić pisanie kodu, a *fragmenty kodu* są jednym ze sposobów, w jaki to robi. Fragment kodu to skrót, który zostanie rozszerzony na mały blok kodu.
    >
    >  Możesz zobaczyć wszystkie dostępne fragmenty kodu. Na pasku menu wybierz pozycję**Menedżer urywków kodu** **narzędzi** > . W przypadku języka `if` C#fragment kodu znajduje się w języku **Visual C#** . W przypadku języka `if` Visual Basic urywki znajdują się w warunkach > **warunkowych i pętli** **wzorców kodu.** Za pomocą tego menedżera można przeglądać istniejące fragmenty kodu lub dodawać własne fragmenty kodu.
    >
    >  Aby uaktywnić fragment kodu podczas wpisywania kodu, wpisz go i wybierz klawisz **Tab.** Wiele urywków pojawia się w oknie **IntelliSense,** dlatego dwukrotnie wybierasz klawisz **Tab:** najpierw wybierz fragment kodu z okna **IntelliSense,** a następnie poinformuj IDE o użyciu fragmentu kodu. (IntelliSense obsługuje `if` fragment kodu, ale `ifelse` nie fragment kodu).

1. Przed uruchomieniem aplikacji zapisz aplikację, wybierając przycisk **Zapisz wszystkie,** który powinien wyglądać podobnie do poniższego zrzutu ekranu.

     ![Przycisk Zapisz wszystkie paski narzędzi](../ide/media/express_iconsaveall.png)<br>
***Save All*** *Przycisk* Zapisz wszystko

     Aby zapisać aplikację, wybierz pozycję **Zapisz** > **wszystko** z paska menu (lub naciśnij **klawisze Ctrl**+**Shift**+**S).** Jest to najlepsza praktyka, aby zapisać wcześnie i często.

     Po uruchomieniu program powinien wyglądać jak na poniższej ilustracji.

     ![Przeglądarka obrazów](../ide/media/express_pictureviewerdonerun.png)<br>***Przeglądarka obrazów***

## <a name="to-test-your-app"></a>Aby przetestować aplikację

1. Wybierz klawisz **F5** lub przycisk **Rozpocznij debugowanie.**

1. Wybierz przycisk **Pokaż obraz,** aby uruchomić właśnie napisytowany kod. Najpierw aplikacja otworzy okno dialogowe **Otwórz plik.** Sprawdź, czy filtry są wyświetlane na liście rozwijanej **Pliki typu** u dołu okna dialogowego. Następnie przejdź do obrazu i otwórz go. Przykładowe obrazy dostarczane z systemem operacyjnym Windows można zwykle znaleźć w folderze *Moje dokumenty* w folderze *Moje obrazy\Przykładowe obrazy.*

    > [!TIP]
    > Jeśli w oknie dialogowym **Wybieranie pliku obrazu** nie widać żadnych obrazów, upewnij się, że filtr **Wszystkie pliki\*(*. )** jest zaznaczony na liście rozwijanej w prawym dolnym momencie okna dialogowego.

1. Załaduj obraz, który pojawi się w pictureboxie. Następnie spróbuj zwymiarować formularz, przeciągając jego obramowania. Ponieważ urządzenie PictureBox jest zadokowane wewnątrz panelu TableLayoutPanel, który sam jest zadokowany wewnątrz formularza, obszar obrazu zmieni rozmiar, tak aby był tak szeroki, jak formularz, i wypełnił 90 procent górnej części formularza. Dlatego użyto <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.FlowLayoutPanel> kontenery: zachowują one rozmiar formularza poprawnie, gdy użytkownik zmienić jego rozmiar.

     W tej chwili większe zdjęcia wykraczają poza granice przeglądarki obrazów. W następnym kroku dodasz kod, aby obrazy zmieściło się w oknie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 10: Pisanie kodu dodatkowych przycisków i pole wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 8: Napisz kod dla programu obsługi zdarzeń przycisku pokaż obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
