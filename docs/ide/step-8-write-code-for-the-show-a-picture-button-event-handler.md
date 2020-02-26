---
title: Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
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
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579808"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku Pokaż obraz

W tym kroku zostanie wykonane działanie przycisku **Pokaż obraz** w następujący sposób:

- Gdy użytkownik wybierze ten przycisk, aplikacja otworzy pole <xref:System.Windows.Forms.OpenFileDialog>.

- Jeśli użytkownik otworzy plik obrazu, aplikacja wyświetli ten obraz w <xref:System.Windows.Forms.PictureBox>.

Środowisko IDE ma zaawansowane narzędzie o nazwie IntelliSense, które ułatwia pisanie kodu. Podczas wpisywania kodu IDE otwiera okno z sugerowanymi uzupełnianiem dla wprowadzanych słów częściowych.

Funkcja IntelliSense próbuje określić, co chcesz zrobić dalej, i automatycznie przechodzi do ostatniego wybranego elementu z listy. Możesz użyć strzałek w górę lub w dół, aby przenieść się na listę, lub wpisać litery, aby zawęzić wybór. Gdy zobaczysz wybór, wybierz klawisz **Tab** , aby go zaznaczyć. Lub możesz zignorować sugestie, jeśli nie jest to konieczne.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku Pokaż obraz

1. Przejdź do **Projektant formularzy systemu Windows** i kliknij dwukrotnie przycisk **Pokaż obraz** . IDE natychmiast przechodzi do projektanta kodu i przenosi kursor tak, aby znajdował się w `showButton_Click()` (Alternatywnie `ShowButton_Click()`) metody, która została dodana wcześniej.

1. Wpisz `i` w pustym wierszu między `{ }`dwa nawiasy klamrowe. (W Visual Basic wpisz pusty wiersz między `Private Sub...` i `End Sub`.) Zostanie otwarte okno **IntelliSense** , jak pokazano na poniższej ilustracji.

    ![Technologia IntelliSense z kodem&#35; Visual C](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Kod może nie wyświetlać programów obsługi zdarzeń w przypadku liter "camelCase".

1. W oknie **IntelliSense** należy podświetlić słowo `if`. (Jeśli nie, wprowadź małe litery `f`i będzie to możliwe). Zwróć uwagę, jak pole *etykietki narzędzia* obok okna **IntelliSense** pojawia się z opisem, **fragment kodu dla instrukcji if**. (W Visual Basic, etykietka narzędzia wskazuje również, że jest to fragment, ale nieco inny wyraz). Chcesz użyć tego fragmentu kodu, więc wybierz klawisz **Tab** , aby wstawić `if` do kodu. Następnie ponownie wybierz klawisz **Tab** , aby użyć fragmentu kodu `if`. (W przypadku wybrania w innym miejscu okna funkcji **IntelliSense** znikają spacje nad `i` i ponownie je wpiszą, a okno **IntelliSense** zostanie otwarte).

    ![Kod języka&#35; Visual C](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Użyj IntelliSense, aby wprowadzić więcej kodu

Następnie użyj funkcji IntelliSense, aby wprowadzić więcej kodu, aby otworzyć okno dialogowe **Otwórz plik** . Jeśli użytkownik wybrał przycisk **OK** , PictureBox załaduje plik wybrany przez użytkownika. Poniższe kroki pokazują, jak wprowadzić kod, a chociaż istnieje wiele kroków, wystarczy kilka naciśnięć klawiszy:

 1. Zacznij od zaznaczonego tekstu **true** w fragmencie kodu. Wpisz `op`, aby go zastąpić. (W Visual Basic zaczynasz od początkowej Cap, więc wpisz `Op`.)

 1. Zostanie otwarte okno **IntelliSense** z **openFileDialog1**. Wybierz klawisz **Tab** , aby go zaznaczyć. (W Visual Basic zaczyna się od początkowej Cap, więc zobaczysz **openFileDialog1**. Upewnij się, że wybrano **openFileDialog1** .)

     Aby dowiedzieć się więcej na temat `OpenFileDialog`, zobacz [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Wpisz kropkę (`.`) (wiele programistów wywołuje to kropkę). Ponieważ wpisano kropkę bezpośrednio po **openFileDialog1**, zostanie otwarte okno **IntelliSense** z właściwościami i metodami składnika **OpenFileDialog** . Są to te same właściwości, które pojawiają się w oknie **Właściwości** w przypadku wybrania go w **Projektant formularzy systemu Windows**. Możesz również wybrać metody, które poinformują składnik, aby wykonali czynności (na przykład otwierając okno dialogowe).

    > [!NOTE]
    > W oknie **IntelliSense** można wyświetlić właściwości i metody. Aby określić, co jest wyświetlane, przyjrzyj się ikonie po lewej stronie każdego elementu w oknie **IntelliSense** . Zobaczysz obraz bloku obok każdej metody, a obraz klucza (lub kolei) obok każdej właściwości. Obok każdego zdarzenia znajduje się również ikona błyskawicy. <br><br>Oto ikony, które są wyświetlane:<br><br>![ikona metody](../ide/media/express_iconmethod.png)<br>ikona właściwości ![](../ide/media/express_iconproperty.png)<br>ikona zdarzenia ![](../ide/media/express_iconevent.png)

 1. Zacznij wpisywać `ShowDialog` (kapitalizacja jest nieważna dla IntelliSense). Metoda `ShowDialog()` wyświetli okno dialogowe **Otwórz plik** . Gdy okno zostanie wyróżnione **ShowDialog**, wybierz klawisz **Tab** . Możesz również wyróżnić "ShowDialog" i wybrać klawisz **F1** , aby uzyskać pomoc dotyczącą tego.

    Aby dowiedzieć się więcej na temat metody `ShowDialog()`, zobacz [Metoda ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. W przypadku korzystania z metody dla formantu lub składnika (nazywanego *wywołaniem metody*) należy dodać nawiasy. Wprowadź nawias otwierający i zamykający bezpośrednio po "g" w `ShowDialog`: `()` powinien teraz wyglądać podobnie jak "openFileDialog1. ShowDialog ()".

    > [!NOTE]
    > Metody są ważną częścią dowolnej aplikacji, a w tym samouczku przedstawiono kilka sposobów korzystania z metod. Można wywołać metodę składnika, aby powiedzieć, jak to zrobić, jak w przypadku wywołania metody `ShowDialog()` składnika **OpenFileDialog** . Możesz utworzyć własne metody, aby aplikacja mogła wykonać swoją aplikację, jak ta, którą tworzysz teraz, nazywana metodą `showButton_Click()`, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

 1. W C#polu Dodaj spację, a następnie Dodaj dwa znaki równości (`==`). Na Visual Basic Dodaj spację, a następnie użyj pojedynczego znaku równości (`=`). (C# i Visual Basic używać różnych operatorów równości).

 1. Dodaj kolejną spację. Gdy tylko to zrobisz, zostanie otwarte inne okno **IntelliSense** . Zacznij wpisywać `DialogResult` a następnie wybierz klawisz **Tab** , aby go dodać.

    > [!NOTE]
    > Podczas pisania kodu w celu wywołania metody, czasami zwraca wartość. W takim przypadku Metoda <xref:System.Windows.Forms.CommonDialog.ShowDialog> składnika **OpenFileDialog** zwraca wartość <xref:System.Windows.Forms.DialogResult>. DialogResult to specjalna wartość informująca o tym, co się stało w oknie dialogowym. Składnik **OpenFileDialog** może spowodować, że użytkownik wybierze **przycisk OK** lub **Anuluj**, aby metoda `ShowDialog()` zwracała `DialogResult.OK` lub `DialogResult.Cancel`.

 1. Wpisz kropkę, aby otworzyć okno **IntelliSense** wartości DialogResult. Wprowadź literę `O` i wybierz klawisz **Tab** , aby wstawić **przycisk OK**.

    Aby dowiedzieć się więcej na temat DialogResult, zobacz [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > Należy ukończyć pierwszy wiersz kodu. Dla C#programu powinien być podobny do poniższego.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  W przypadku Visual Basic należy wykonać następujące czynności.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Teraz Dodaj jeszcze jeden wiersz kodu. Możesz ją wpisać (lub skopiować i wkleić), ale rozważ użycie funkcji IntelliSense, aby ją dodać. Im bardziej znająsz technologię IntelliSense, tym szybciej możesz napisać własny kod. Ostateczna Metoda `showButton_Click()` powinna wyglądać podobnie do poniższego kodu.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)** .

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)
