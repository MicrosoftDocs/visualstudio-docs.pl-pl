---
title: Krok 9. Przejrzyj, komentowanie i testowanie kodu
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cddb92e57a501fb8ea5eeda9b2c6ec60b95c45c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934318"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9. Przejrzyj, komentowanie i testowanie kodu
Następnie dodaj komentarz do kodu. Należy zauważyć, że nie zmienia sposób, w jaki program zachowuje się jest komentarz. To ułatwia komuś, kto czyta swój kod, aby zrozumieć, jak działa. Dodawanie komentarzy do kodu to dobry sposób na. W języku Visual C# dwie kreski ułamkowe (/ /) oznaczają wiersz jako komentarz. W języku Visual Basic pojedynczy cudzysłów (') służy do oznaczania wiersza jako komentarz. Po dodaniu komentarza, przetestuj swój program. Jest dobrą praktyką, aby uruchomić i przetestować kod często podczas pracy nad swoimi projektami, aby można było wyłapać i rozwiązać wszelkie problemy wcześnie, zanim kod stanie się bardziej skomplikowane. Jest to nazywane *iteracyjne testowanie*.

 Stworzyłeś właśnie coś, co działa, a mimo że nie jest jeszcze zrobione, już można załadować obrazu. Przed Dodaj komentarz do kodu i przetestowaniem go Poświęć czas, aby zapoznać się z pojęciami kodu, ponieważ będą często używane następujące pojęcia:

- Po dwukrotnym kliknięciu **Pokaż obraz** znajdujący się w **Windows Forms Designer**, IDE automatycznie dodaje *metoda* do kodu programu.

- Metody to sposób organizowania kodu: To, jak kod jest zgrupowany razem.

- W większości przypadków, metoda wykonuje kilka rzeczy w określonej kolejności, jak Twoja `showButton_Click()` metoda Wyświetla okno dialogowe, a następnie ładująca obraz.

- Metoda składa się z kodu *instrukcji*, lub linii kodu. Myśl o metodzie, aby powiązać ze sobą instrukcji kodu.

- Po wykonaniu metody lub *o nazwie*, instrukcji w metodzie są wykonywane w kolejności, jedna po drugiej, począwszy od pierwszej.

   Oto przykład instrukcji.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Instrukcje są na tym, co sprawia, że Twoje programy robią pewne rzeczy. W języku Visual C# instrukcja zawsze kończy się średnikiem. W języku Visual Basic koniec wiersza jest końcem instrukcji. (Średnik nie jest potrzebny w języku Visual Basic). Poprzednia instrukcja nakazuje swoje <xref:System.Windows.Forms.PictureBox> kontroli można załadować pliku, który użytkownik wybrał ze **OpenFileDialog** składnika.

  ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -5 wideo](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-add-comments"></a>Aby dodać komentarze

1.  Dodaj poniższy komentarz do kodu.

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

    > [!NOTE]
    >  Twoje **showButton** przycisku <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń jest zakończony i działa. Rozpocząłeś pisanie kodu, rozpoczynając od `if` instrukcji. `if` Instrukcja jest, jak sprawdzić program, "Sprawdź to jedno i jeśli to PRAWDA, wykonaj te akcje". W tym przypadku powiesz programowi w taki sposób, aby otworzyć **Otwórz plik** okno dialogowe, a jeśli użytkownik wybierze plik i wybierze **OK** przycisk, załadował ten pliku w **PictureBox**.

    > [!TIP]
    >  IDE zostało zbudowane ułatwia pisanie kodu, i *fragmenty kodu* jest jednym ze sposobów, tak. Wstawka to skrót, który rozwija się w małych blokach kodu.
    >
    >  Możesz zobaczyć wszystkie dostępne wstawki. Na pasku menu wybierz **narzędzia** > **Menedżera wstawek kodu**. Dla języka Visual C# `if` fragmentu kodu znajduje się w **Visual C#** . Dla języka Visual Basic `if` fragmenty znajdują się w **instrukcje warunkowe i pętle** > **wzorców kodu**. Można użyć tego menedżera do przeglądania istniejących wstawek lub dodać własne wstawki.
    >
    >  Aby uaktywnić wstawkę podczas wpisywania kod, wpisz ją, a następnie wybierz **kartę** klucza. Wiele fragmentów są wyświetlane w **IntelliSense** okna, dlatego możesz wybrać **kartę** dwa razy: najpierw do wybrania wstawki z **IntelliSense** okna, a następnie poinformowania Środowisko IDE przeznaczone do użycia do fragmentu kodu. (Technologia IntelliSense obsługuje `if` fragment kodu, ale nie `ifelse` fragmentu kodu.)

2.  Przed uruchomieniem programu należy zapisać program, wybierając **Zapisz wszystko** przycisku paska narzędzi, który wygląda następująco.

     ![Zapisz wszystkie przyciski paska narzędzi](../ide/media/express_iconsaveall.png)
**Zapisz wszystko** przycisku

     Alternatywnie, aby zapisać swój program, na pasku menu, wybierz **pliku** > **Zapisz wszystko**. Jest najlepszym rozwiązaniem jest zapisywać wcześnie i często.

     Gdy jest uruchomiona, Twój program powinien wyglądać jak na poniższym obrazie.

     ![Obraz podglądu](../ide/media/express_pictureviewerdonerun.png)
**Picture Viewer**

## <a name="to-test-your-program"></a>Aby przetestować swój program

1.  Wybierz **F5** klucza, lub wybierz **Rozpocznij debugowanie** przycisku paska narzędzi.

2.  Wybierz **Pokaż obraz** przycisk, aby uruchomić napisany właśnie kod. Najpierw program otworzy **Otwórz plik** okno dialogowe. Sprawdź, czy filtry są widoczne w **pliki typu** listy rozwijanej w dolnej części okna dialogowego. Następnie przejdź do obrazu i otwórz go. Zwykle można znaleźć przykładowe obrazy, które są dostarczane z systemem operacyjnym Windows w Twojej *Moje dokumenty* folderu, wewnątrz *My Pictures\Sample Pictures* folderu.

    > [!NOTE]
    >  Jeśli nie widzisz żadnych obrazów w **wybierz plik obrazu** okno dialogowe, upewnij się, że **wszystkie pliki (*.\*)**  filtr jest zaznaczony na liście rozwijanej u dołu po prawej stronie okna dialogowego.

3.  Zdjęcia i pojawia się w obiekcie PictureBox. Spróbuj zmienić rozmiar formularza przeciągając jego obramowania. Ponieważ Twoje PictureBox zadokowano wewnątrz elementu TableLayoutPanel, który sam jest zadokowany wewnątrz formularza, Twój obszar obrazu będzie zmieniany tak jak szerokość całego formularza i wypełni najważniejsze 90 procent firm z formularza. Dlatego możesz używać <xref:System.Windows.Forms.TableLayoutPanel> i <xref:System.Windows.Forms.FlowLayoutPanel> kontenerów: Prowadzą użyłeś pojemników, gdy użytkownik zmienia jego rozmiar formularza.

     Teraz większe zdjęcia wykraczają poza granice przeglądarki obrazów. W następnym kroku dodasz kod, aby obrazy mieściły się w oknie.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 10: Pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Pisanie kodu dla programu obsługi zdarzeń przycisku Obraz](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).
