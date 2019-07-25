---
title: Krok 8. Napisz kod dla programu obsługi zdarzeń przycisku Pokaż obraz
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01193111cd1c9e89dbdf32847499b6f79008b27d
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416942"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8. Napisz kod dla programu obsługi zdarzeń przycisku Pokaż obraz

W tym kroku zostanie wykonane działanie przycisku **Pokaż obraz** w następujący sposób:

- Gdy użytkownik wybierze ten przycisk, program otwiera <xref:System.Windows.Forms.OpenFileDialog> okno.

- Jeśli użytkownik otworzy plik obrazu, program wyświetli ten obraz w <xref:System.Windows.Forms.PictureBox>.

Środowisko IDE ma zaawansowane narzędzie o nazwie IntelliSense, które ułatwia pisanie kodu. Podczas wprowadzania kodu środowisko IDE otwiera okno z sugerowanymi uzupełnianiem dla wprowadzanych słów częściowych. Próbuje określić, co chcesz zrobić dalej, i automatycznie przechodzi do ostatniego wybranego elementu z listy. Możesz użyć strzałek w górę lub w dół, aby przenieść się na listę, lub wpisać litery, aby zawęzić wybór. Gdy zobaczysz wybór, wybierz klawisz **Tab** , aby go zaznaczyć. Lub możesz zignorować sugestie, jeśli nie jest to konieczne.

![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Utwórz przeglądarkę obrazów w Visual Basic — wideo 4](https://msdn.microsoft.com/vstudio/gg315355.aspx). Ten film wideo korzysta ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku Pokaż obraz

1. Przejdź do **Projektant formularzy systemu Windows** i kliknij dwukrotnie przycisk **Pokaż obraz** . IDE natychmiast przechodzi do projektanta kodu i przenosi kursor tak, aby znajdował się wewnątrz `showButton_Click()` metody, która została dodana wcześniej.

2. Wpisz w pustym wierszu między dwoma `{ }`nawiasami klamrowymi. `i` (W Visual Basic wpisz pusty wiersz między `Private Sub...` i `End Sub`.) Zostanie otwarte okno **IntelliSense** , jak pokazano na poniższej ilustracji.

     ![Technologia IntelliSense z kodem&#35; Visual C](../ide/media/express_ifintellisense.png)

3. W oknie **IntelliSense** należy wyróżnić słowo `if`. (Jeśli nie, wprowadź małą literę `f`i.) Zwróć uwagę, jak zostanie wyświetlone małe pole *etykietki narzędzia* obok okna **IntelliSense** z opisem, **fragment kodu dla instrukcji if**. (W Visual Basic, etykietka narzędzia wskazuje również, że jest to fragment, ale nieco inny wyraz). Chcesz użyć tego fragmentu kodu, więc wybierz klawisz **Tab** , aby wstawić `if` do kodu. Następnie ponownie wybierz klawisz **Tab** , aby użyć `if` fragmentu kodu. (W przypadku wybrania w innym miejscu okna funkcji **IntelliSense** zniknęła spacja nad `i` i ponownie wpisz ją, a okno **IntelliSense** zostanie otwarte).

     ![Kod języka&#35; Visual C](../ide/media/express_highlighttrue.png)

4. Następnie użyj funkcji IntelliSense, aby wprowadzić więcej kodu, aby otworzyć okno dialogowe **Otwórz plik** . Jeśli użytkownik wybrał przycisk **OK** , PictureBox załaduje plik wybrany przez użytkownika. Poniższe kroki pokazują, jak wprowadzić kod, a chociaż jest to wiele kroków, wystarczy kilka naciśnięć klawiszy:

    1. Zacznij od zaznaczonego tekstu **true** w fragmencie kodu. Wpisz `op` , aby go zastąpić. (W Visual Basic zaczynasz od początkowej litery, więc wpisz `Op`).

    2. Zostanie otwarte okno **IntelliSense** z **openFileDialog1**. Wybierz klawisz **Tab** , aby go zaznaczyć. (W Visual Basic zaczyna się od początkowej Cap, więc zobaczysz **openFileDialog1**. Upewnij się, że wybrano **openFileDialog1** .)

         Aby dowiedzieć się `OpenFileDialog`więcej na temat, zobacz [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

    3. Wpisz kropkę (`.`) (wielu programistów wywołuje to kropkę). Ponieważ wpisano kropkę bezpośrednio po **openFileDialog1**, zostanie otwarte okno **IntelliSense** z właściwościami i metodami składnika **OpenFileDialog** . Są to te same właściwości, które pojawiają się w oknie **Właściwości** w przypadku wybrania go w **Projektant formularzy systemu Windows**. Możesz również wybrać metody, które poinformują składnik, aby wykonali czynności (na przykład otwierając okno dialogowe).

        > [!NOTE]
        > W oknie **IntelliSense** można wyświetlić właściwości i metody. Aby określić, co jest wyświetlane, przyjrzyj się ikonie po lewej stronie każdego elementu w oknie **IntelliSense** . Zobaczysz obraz bloku obok każdej metody, a obraz klucza (lub kolei) obok każdej właściwości. Obok każdego zdarzenia znajduje się również ikona błyskawicy. Te obrazy są wyświetlane w następujący sposób.

         ![Ikona metody](../ide/media/express_iconmethod.png)

         ![Ikona Właściwość](../ide/media/express_iconproperty.png)

         ![Ikona zdarzenia](../ide/media/express_iconevent.png)

    4. Zacznij pisać `ShowDialog` (wielkie litery jest nieważne dla IntelliSense). Metoda wyświetli okno dialogowe **Otwórz plik.** `ShowDialog()` Gdy okno zostanie wyróżnione **ShowDialog**, wybierz klawisz **Tab** . Możesz również wyróżnić "ShowDialog" i wybrać klawisz **F1** , aby uzyskać pomoc dotyczącą tego.

         Aby dowiedzieć się więcej `ShowDialog()` na temat metody, zobacz [Metoda ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

    5. W przypadku korzystania z metody dla formantu lub składnika (nazywanego *wywołaniem metody*) należy dodać nawiasy. Wprowadź nawiasy otwierające i zamykające bezpośrednio po "g" w `ShowDialog`: `()`Powinien teraz wyglądać podobnie jak "openFileDialog1. ShowDialog ()".

        > [!NOTE]
        > Metody są ważną częścią każdego programu, a w tym samouczku przedstawiono kilka sposobów korzystania z metod. Można wywołać metodę składnika, aby poinformować go o tym, jak nazywamy `ShowDialog()` metodę składnika **OpenFileDialog** . Możesz utworzyć własne metody, aby umożliwić programowi wykonywanie zadań, takich jak ten, który tworzysz teraz, zwanej `showButton_Click()` metodą, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

    6. Dla wizualizacji C#Dodaj spację, a następnie Dodaj dwa znaki równości (`==`). Na Visual Basic Dodaj spację, a następnie użyj pojedynczego znaku równości (`=`). (Wizualizacje C# i Visual Basic używają różnych operatorów równości).

    7. Dodaj kolejną spację. Gdy tylko to zrobisz, zostanie otwarte inne okno **IntelliSense** . Rozpocznij wpisywanie `DialogResult` i wybierz klawisz **Tab** , aby go dodać.

        > [!NOTE]
        > Podczas pisania kodu w celu wywołania metody, czasami zwraca wartość. W takim przypadku <xref:System.Windows.Forms.CommonDialog.ShowDialog> Metoda składnika **OpenFileDialog** zwraca <xref:System.Windows.Forms.DialogResult> wartość. DialogResult to specjalna wartość informująca o tym, co się stało w oknie dialogowym. Składnik **OpenFileDialog** może spowodować, że użytkownik wybierze **przycisk OK** lub `ShowDialog()` **Anuluj**, dlatego metoda zwraca albo `DialogResult.OK` lub `DialogResult.Cancel`.

    8. Wpisz kropkę, aby otworzyć okno **IntelliSense** wartości DialogResult. Wprowadź literę `O` i wybierz klawisz **Tab** , aby wstawić **przycisk OK**.

         Aby dowiedzieć się więcej na temat DialogResult, zobacz [DialogResult](<xref:System.Windows.Forms.DialogResult>).

        > [!NOTE]
        > Należy ukończyć pierwszy wiersz kodu. Dla wizualizacji C#należy wykonać następujące czynności.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  W przypadku Visual Basic należy wykonać następujące czynności.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Teraz Dodaj jeszcze jeden wiersz kodu. Możesz ją wpisać (lub skopiować i wkleić), ale rozważ użycie funkcji IntelliSense, aby ją dodać. Im bardziej znająsz technologię IntelliSense, tym szybciej możesz napisać własny kod. Ostatnia `showButton_Click()` Metoda wygląda następująco.

         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 9: Przejrzyj, Skomentuj i Przetestuj swój kod](../ide/step-9-review-comment-and-test-your-code.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodaj składniki okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).
