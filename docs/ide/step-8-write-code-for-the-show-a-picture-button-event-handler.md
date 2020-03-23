---
title: 'Krok 8: Napisz kod dla programu obsługi zdarzeń przycisku obrazu'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579808"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8: Napisz kod dla programu obsługi zdarzeń przycisku obrazu

W tym kroku przycisk **Pokaż obraz działa** w następujący sposób:

- Gdy użytkownik wybierze ten przycisk, <xref:System.Windows.Forms.OpenFileDialog> aplikacja otworzy pole.

- Jeśli użytkownik otworzy plik obrazu, aplikacja pokazuje <xref:System.Windows.Forms.PictureBox>ten obraz w pliku .

IDE ma zaawansowane narzędzie o nazwie IntelliSense, który pomaga pisać kod. Podczas wpisywać kod IDE otwiera pole z sugerowane uzupełnienia dla częściowych wyrazów, które można wprowadzić.

IntelliSense próbuje określić, co chcesz zrobić dalej i automatycznie przeskakuje do ostatniego elementu, który wybierzesz z listy. Możesz użyć strzałek w górę lub w dół, aby przejść na liście, lub zachować wpisywanie liter, aby zawęzić opcje. Gdy zobaczysz odpowiedni wybór, wybierz klawisz Tab, aby go **zaznaczyć.** Możesz też zignorować sugestie, jeśli nie są potrzebne.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku obrazu

1. Przejdź do **programu Windows Forms Designer** i kliknij dwukrotnie przycisk Pokaż **obraz.** IDE natychmiast przechodzi do projektanta kodu i przenosi kursor, `showButton_Click()` więc jest `ShowButton_Click()`wewnątrz (alternatywnie), metoda, która została dodana wcześniej.

1. Wpisz `i` na pustej linii między `{ }`dwoma nawiasami klamrowymi . (W języku Visual Basic wpisz `Private Sub...` pustą linię między i .) `End Sub` Zostanie otwarte okno **IntelliSense,** jak pokazano na poniższej ilustracji.

    ![IntelliSense z kodem&#35; języka Visual C](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Kod może nie wyświetlać programów obsługi zdarzeń w literach "camelCase".

1. Okno **IntelliSense** powinno podświetlić słowo `if`. (Jeśli nie, wprowadź małe `f`litery , a będzie.) Zwróć uwagę, jak pole *etykietki narzędzia* obok okna **IntelliSense** pojawia się z opisem, **Fragment kodu dla if instrukcji**. (W języku Visual Basic etykietka narzędzia stwierdza również, że jest to fragment kodu, ale z nieco innym sformułowaniem). Chcesz użyć tego fragmentu kodu, więc wybierz klawisz `if` **Tab,** aby wstawić do kodu. Następnie ponownie wybierz klawisz **Tab,** aby użyć fragmentu `if` kodu. (Jeśli wybierzesz inną opcję i twoje okno **IntelliSense** zniknęło, backspace nad `i` i ponownie wpisz go, a okno **IntelliSense** zostanie ponownie otwarte).

    ![Kod&#35; języka Visual C](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Wprowadź więcej kodu za pomocą funkcji IntelliSense

Następnie użyj IntelliSense, aby wprowadzić więcej kodu, aby otworzyć okno dialogowe **Otwórz plik.** Jeśli użytkownik wybierze przycisk **OK,** picturebox ładuje wybrany plik. Poniższe kroki pokazują, jak wprowadzić kod i chociaż istnieje wiele kroków, to tylko kilka nacięć klawiszy:

 1. Zacznij od zaznaczonego tekstu **true** we we weselu. Wpisz, `op` aby go zastąpić. (W języku Visual Basic zaczynasz od `Op`początkowego limitu, więc wpisz .)

 1. Zostanie otwarte okno **IntelliSense** i zostanie **wyświetlone openFileDialog1**. Wybierz klawisz Tab, aby go **zaznaczyć.** (W języku Visual Basic zaczyna się od początkowego limitu, więc zobaczysz **OpenFileDialog1**. Upewnij się, że wybrano **openfiledialog1.)**

     Aby dowiedzieć `OpenFileDialog`się więcej o , zobacz [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Wpisz kropkę`.`( ) (Wielu programistów nazywa to kropką). Ponieważ wpisano kropkę zaraz po **openFileDialog1,** otwiera się okno **IntelliSense** wypełnione wszystkimi właściwościami i metodami składnika **OpenFileDialog.** Są to te same właściwości, które pojawiają się w oknie **Właściwości** po wybraniu go w **programie Windows Forms Designer**. Można również wybrać metody, które informują składnik o działań (np. otwieranie okna dialogowego).

    > [!NOTE]
    > Okno **IntelliSense** może wyświetlać zarówno właściwości, jak i metody. Aby ustalić, co jest wyświetlane, spójrz na ikonę po lewej stronie każdego elementu w oknie **IntelliSense.** Obok każdej metody zostanie wyświetlony obraz bloku oraz obraz klucza (klucza) obok każdej właściwości. Obok każdego wydarzenia znajduje się również ikona błyskawicy. <br><br>Oto wyświetlane ikony:<br><br>![Ikona Metody](../ide/media/express_iconmethod.png)<br>![Ikona właściwości](../ide/media/express_iconproperty.png)<br>![Ikona zdarzenia](../ide/media/express_iconevent.png)

 1. Zacznij pisać `ShowDialog` (wielkość liter nie ma znaczenia dla IntelliSense). Metoda `ShowDialog()` wyświetli okno dialogowe **Otwórz plik.** Po podświetleniu okna **ShowDialog**wybierz klawisz **Tab.** Możesz również wyróżnić "ShowDialog" i wybrać klawisz **F1,** aby uzyskać pomoc.

    Aby dowiedzieć `ShowDialog()` się więcej o tej metodzie, zobacz [Metoda ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. W przypadku użycia metody w formancie lub składniku (określanym jako *wywołanie metody),* należy dodać nawiasy. Więc wprowadź otwierania i zamykania nawiasów natychmiast `ShowDialog` `()` po "g" w : Powinien teraz wyglądać jak "openFileDialog1.ShowDialog()".

    > [!NOTE]
    > Metody są ważną częścią dowolnej aplikacji, a ten samouczek pokazał kilka sposobów korzystania z metod. Można wywołać metodę składnika, aby powiedzieć mu, aby coś zrobić, na przykład `ShowDialog()` jak nazwano **OpenFileDialog** składnika metody. Możesz utworzyć własne metody, aby aplikacja wykonywać rzeczy, takie jak ten, `showButton_Click()` który tworzysz teraz, o nazwie metoda, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

 1. W przypadku języka C#dodaj spację, a`==`następnie dodaj dwa znaki równości ( ). W programie Visual Basic dodaj spację, a`=`następnie użyj pojedynczego znaku równości ( ). (C# i Visual Basic używają różnych operatorów równości.

 1. Dodaj jeszcze jedną przestrzeń. Tak szybko, jak to zrobić, inne okno **IntelliSense** otwiera. Zacznij pisać `DialogResult` i wybierz klawisz **Tab,** aby go dodać.

    > [!NOTE]
    > Podczas pisania kodu do wywołania metody, czasami zwraca wartość. W takim przypadku metoda składnika <xref:System.Windows.Forms.CommonDialog.ShowDialog> **OpenFileDialog** zwraca <xref:System.Windows.Forms.DialogResult> wartość. DialogResult jest specjalną wartością, która informuje, co się stało w oknie dialogowym. Składnik **OpenFileDialog** może spowodować, że użytkownik **wybierze przycisk OK** lub **Anuluj,** więc jego `ShowDialog()` metoda zwraca albo `DialogResult.OK` . `DialogResult.Cancel`

 1. Wpisz kropkę, aby otworzyć okno **IntelliSense** wartość DialogResult. Wprowadź literę `O` i wybierz klawisz **Tab,** aby wstawić **przycisk OK**.

    Aby dowiedzieć się więcej o oknie DialogResult, zobacz [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > Pierwszy wiersz kodu powinien być kompletny. Dla języka C#, powinno być podobne do następujących.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  W przypadku języka Visual Basic powinno być następujące.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Teraz dodaj jeszcze jeden wiersz kodu. Możesz go wpisać (lub skopiować i wkleić), ale rozważ użycie funkcji IntelliSense, aby ją dodać. Im bardziej znasz IntelliSense, tym szybciej możesz napisać własny kod. Ostateczna `showButton_Click()` metoda powinna wyglądać podobnie do następującego kodu.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[Krok 9: Przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie quizu matematycznego z czasem](tutorial-2-create-a-timed-math-quiz.md)
* [samouczek 3: Tworzenie pasującej gry](tutorial-3-create-a-matching-game.md)
