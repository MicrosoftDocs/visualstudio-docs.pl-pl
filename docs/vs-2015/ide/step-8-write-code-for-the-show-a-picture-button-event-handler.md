---
title: Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2c1b09d88de938ee4bc93b69b50d53c0d39006f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300001"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8. Wpisywanie kodu dla obsługi zdarzeń pokazywania przycisków obrazowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym kroku zostanie wykonane działanie przycisku **Pokaż obraz** w następujący sposób:

- Gdy użytkownik wybierze ten przycisk, program otworzy okno dialogowe **Otwórz plik** .

- Jeśli użytkownik otworzy plik obrazu, program wyświetli ten obraz w elemencie PictureBox.

  Środowisko IDE ma zaawansowane narzędzie o nazwie IntelliSense, które ułatwia pisanie kodu. Podczas wprowadzania kodu środowisko IDE otwiera okno z sugerowanymi uzupełnianiem dla wprowadzanych słów częściowych. Próbuje określić, co chcesz zrobić dalej, i automatycznie przechodzi do ostatniego wybranego elementu z listy. Możesz użyć strzałek w górę lub w dół, aby przenieść się na listę, lub wpisać litery, aby zawęzić wybór. Gdy zobaczysz wybór, wybierz klawisz TAB, aby go zaznaczyć. Lub możesz zignorować sugestie, jeśli nie jest to konieczne.

  ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 4](https://go.microsoft.com/fwlink/?LinkId=205215) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# wideo 4](https://go.microsoft.com/fwlink/?LinkId=205203). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku Pokaż obraz

1. Przejdź do Projektant formularzy systemu Windows i kliknij dwukrotnie przycisk **Pokaż obraz** . IDE natychmiast przechodzi do projektanta kodu i przenosi kursor tak, aby znajdował się w podanej wcześniej metodzie `showButton_Click()`.

2. Wpisz `i` w pustym wierszu między dwoma nawiasami klamrowymi {}. (W Visual Basic wpisz pusty wiersz między prywatnym sub... i End Sub). Zostanie otwarte okno **IntelliSense** , jak pokazano na poniższej ilustracji.

     ![Technologia IntelliSense z Visual&#35; C Code](../ide/media/express-ifintellisense.png "Express_IfIntellisense") IntelliSense z C# Visual Code

3. W oknie **IntelliSense** należy podświetlić słowo **if**. (Jeśli nie, wprowadź małe litery `f`i będzie to możliwe). Zwróć uwagę, jak zostanie wyświetlone małe pole *etykietki narzędzia* obok okna **IntelliSense** z opisem, **fragment kodu dla instrukcji if**. (W Visual Basic, etykietka narzędzia wskazuje również, że jest to fragment, ale nieco inny wyraz). Chcesz użyć tego fragmentu kodu, więc wybierz klawisz TAB, **Aby wstawić go** w kodzie. Następnie ponownie wybierz klawisz **Tab, aby użyć fragmentu** kodu. (W przypadku wybrania opcji w innym miejscu, gdy okno funkcji **IntelliSense** zniknie, nadpisać **i ponownie** wpisz je), a okno **IntelliSense** zostanie otwarte.)

     ![Kod wizualny&#35; ](../ide/media/express-highlighttrue.png "Express_HighlightTrue") C# kodu języka Visual C

4. Następnie użyj funkcji IntelliSense, aby wprowadzić więcej kodu, aby otworzyć okno dialogowe **Otwórz plik** . Jeśli użytkownik wybrał przycisk **OK** , PictureBox załaduje plik wybrany przez użytkownika. Poniższe kroki pokazują, jak wprowadzić kod, a chociaż jest to wiele kroków, wystarczy kilka naciśnięć klawiszy:

    1. Zacznij od zaznaczonego tekstu **true** w fragmencie kodu. Wpisz `op`, aby go zastąpić. (W Visual Basic zaczynasz od początkowej Cap, więc wpisz `Op`.)

    2. Zostanie otwarte okno **IntelliSense** z **openFileDialog1**. Wybierz klawisz TAB, aby go zaznaczyć. (W Visual Basic zaczyna się od początkowej Cap, więc zobaczysz **openFileDialog1**. Upewnij się, że wybrano **openFileDialog1** .)

         Aby dowiedzieć się więcej na temat `OpenFileDialog`, zobacz [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Wpisz kropkę (`.`) (wiele programistów wywołuje to kropkę). Ponieważ wpisano kropkę bezpośrednio po **openFileDialog1**, zostanie otwarte okno **IntelliSense** z właściwościami i metodami składnika **OpenFileDialog** . Są to te same właściwości, które pojawiają się w oknie **Właściwości** w przypadku wybrania go w Projektant formularzy systemu Windows. Możesz również wybrać metody, które poinformują składnik, aby wykonali czynności (na przykład otwierając okno dialogowe).

        > [!NOTE]
        > W oknie **IntelliSense** można wyświetlić właściwości i metody. Aby określić, co jest wyświetlane, przyjrzyj się ikonie po lewej stronie każdego elementu w oknie **IntelliSense** . Zobaczysz obraz bloku obok każdej metody, a obraz klucza (lub kolei) obok każdej właściwości. Obok każdego zdarzenia znajduje się również ikona błyskawicy. Te obrazy są wyświetlane w następujący sposób.

         ![Ikona metody](../ide/media/express-iconmethod.png "Express_IconMethod") Ikona metody

         ![Ikona właściwości](../ide/media/express-iconproperty.png "Express_IconProperty") Ikona właściwości

         ![Ikona zdarzenia](../ide/media/express-iconevent.png "Express_IconEvent") Ikona zdarzenia

    4. Zacznij wpisywać `ShowDialog` (kapitalizacja jest nieważna dla IntelliSense). Metoda `ShowDialog()` wyświetli okno dialogowe **Otwórz plik** . Gdy okno zostanie wyróżnione **ShowDialog**, wybierz klawisz Tab. Możesz również wyróżnić "ShowDialog" i wybrać klawisz F1, aby uzyskać pomoc dotyczącą tego.

         Aby dowiedzieć się więcej na temat metody `ShowDialog()`, zobacz [Metoda ShowDialog](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. W przypadku korzystania z metody dla formantu lub składnika (nazywanego *wywołaniem metody*) należy dodać nawiasy. Wprowadź nawias otwierający i zamykający bezpośrednio po "g" w `ShowDialog`: `()` powinien teraz wyglądać podobnie jak "openFileDialog1. ShowDialog ()".

        > [!NOTE]
        > Metody są ważną częścią każdego programu, a w tym samouczku przedstawiono kilka sposobów korzystania z metod. Można wywołać metodę składnika, aby powiedzieć, jak to zrobić, jak w przypadku wywołania metody `ShowDialog()` składnika **OpenFileDialog** . Możesz utworzyć własne metody, aby umożliwić programowi wykonywanie zadań, takich jak ten, który tworzysz teraz, nazywamy metodą `showButton_Click()`, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

    6. Dla wizualizacji C#Dodaj spację, a następnie Dodaj dwa znaki równości (`==`). Na Visual Basic Dodaj spację, a następnie użyj pojedynczego znaku równości (`=`). (Wizualizacje C# i Visual Basic używają różnych operatorów równości).

    7. Dodaj kolejną spację. Gdy tylko to zrobisz, zostanie otwarte inne okno **IntelliSense** . Zacznij wpisywać `DialogResult` a następnie wybierz klawisz TAB, aby go dodać.

        > [!NOTE]
        > Podczas pisania kodu w celu wywołania metody, czasami zwraca wartość. W takim przypadku Metoda `ShowDialog()` składnika **OpenFileDialog** zwraca wartość DialogResult. DialogResult to specjalna wartość informująca o tym, co się stało w oknie dialogowym. Składnik **OpenFileDialog** może spowodować, że użytkownik wybierze **przycisk OK** lub **Anuluj**, więc metoda `ShowDialog()` zwraca wartość DialogResult. OK lub DialogResult. Cancel.

    8. Wpisz kropkę, aby otworzyć okno **IntelliSense** wartości DialogResult. Wprowadź literę `O` i wybierz klawisz TAB, aby wstawić **przycisk OK**.

         Aby dowiedzieć się więcej na temat `DialogResult`, zobacz [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > Należy ukończyć pierwszy wiersz kodu. Dla wizualizacji C#należy wykonać następujące czynności.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  W przypadku Visual Basic należy wykonać następujące czynności.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Teraz Dodaj jeszcze jeden wiersz kodu. Możesz ją wpisać (lub skopiować i wkleić), ale rozważ użycie funkcji IntelliSense, aby ją dodać. Im bardziej znająsz technologię IntelliSense, tym szybciej możesz napisać własny kod. Ostateczna Metoda `showButton_Click()` wygląda następująco. (Wybierz kartę **VB** , aby wyświetlić Visual Basic wersję kodu).

         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).
