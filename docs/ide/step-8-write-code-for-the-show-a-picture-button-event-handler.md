---
title: Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku obrazu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5c84f113722cda29624a3d37dfc971a67fb72e1
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853654"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Krok 8. Pisanie kodu dla programu obsługi zdarzeń przycisku obrazu

W tym kroku wprowadzisz **Pokaż obraz** przycisk pracował jak to:

- Gdy użytkownik wybierze ten przycisk, program otworzy <xref:System.Windows.Forms.OpenFileDialog> pole.

- Jeśli użytkownik otworzy plik obrazu, spowoduje wyświetlenie tego obrazu w <xref:System.Windows.Forms.PictureBox>.

IDE ma potężne narzędzie o nazwie IntelliSense, które ułatwia pisanie kodu. Gdy wprowadzasz kod, IDE otwiera pole z sugerowanymi uzupełnieniami częściowych wyrazów, które należy wprowadzić. Próbuje określić, co chcesz zrobić dalej i automatycznie przechodzi do ostatniego elementu wybranego z listy. Można użyć w górę lub strzałkę w dół, aby przenieść na liście, lub możesz wpisywać litery, aby ograniczyć zakres wyboru. Po wyświetleniu wyboru, należy wybrać **kartę** klawisz, aby go zaznaczyć. Lub możesz zignorować sugestie, jeśli nie są potrzebne.

![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 4](https://msdn.microsoft.com/vstudio/gg315355.aspx). W tym wideo używa starszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Aby napisać kod dla programu obsługi zdarzeń przycisku obrazu

1.  Przejdź do **Windows Forms Designer** i kliknij dwukrotnie **Pokaż obraz** przycisku. IDE natychmiast trafia do projektanta kodu i przenosi kursor znajduje się wewnątrz `showButton_Click()` metoda dodanej wcześniej.

2.  Typ `i` w pustym wierszu między dwoma nawiasami klamrowymi `{ }`. (W języku Visual Basic wpisz w pustym wierszu między `Private Sub...` i `End Sub`.) **IntelliSense** zostanie otwarte okno, jak pokazano na poniższej ilustracji.

     ![Funkcja IntelliSense, przy użyciu języka Visual C&#35; kodu](../ide/media/express_ifintellisense.png)

3.  **IntelliSense** okno powinno podkreślać wyraz `if`. (Jeśli nie, należy wprowadzić małymi literami `f`, i będzie ono.) Zwróć uwagę, jak małe *etykietki narzędzia* obok pola **IntelliSense** zostanie wyświetlone okno z opisem **fragment kodu dotyczący if — instrukcja**. (W języku Visual Basic etykietka narzędzia również wskazuje to fragment, lecz nieco inaczej sformułowane.) Aby użyć tej wstawki, więc wybierz **kartę** klawisz, aby wstawić `if` w kodzie. Następnie wybierz **kartę** klucz ponownie `if` fragmentu kodu. (Jeśli użytkownik zaznaczy gdzie indziej i **IntelliSense** okna zniknął, trzeba cofnąć się za `i` i wpisać to ponownie, a **IntelliSense** ponownie zostanie otwarte okno.)

     ![Visual C&#35; code](../ide/media/express_highlighttrue.png)

4.  Następnie użyj funkcji IntelliSense, aby wprowadzić więcej kodu, aby otworzyć **Otwórz plik** okno dialogowe. Jeśli użytkownik wybrał **OK** button, element PictureBox ładuje plik wybrany przez użytkownika. Poniższe kroki pokazują jak wprowadzać kod, a wiele czynności, ale jest kilka naciśnięć klawiszy:

    1.  Start z zaznaczonym tekstem **true** we fragmencie kodu. Typ `op` go zastąpić. (W języku Visual Basic start literą, więc wpisz `Op`.)

    2.  **IntelliSense** okna otwiera i wyświetla **openFileDialog1**. Wybierz **kartę** klawisz, aby go zaznaczyć. (W języku Visual Basic zaczyna się od zakończenia początkowej, tak aby było widać **OpenFileDialog1**. Upewnij się, że **OpenFileDialog1** jest zaznaczona.)

         Aby dowiedzieć się więcej na temat `OpenFileDialog`, zobacz [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

    3.  Wpisz kropkę (`.`) (wielu programistów nazywa to kropką.) Ponieważ wpisano kropkę na prawo po **openFileDialog1**, **IntelliSense** zostanie wyświetlone okno dialogowe, wypełnionymi wszystkimi **OpenFileDialog** metodami i właściwościami składnika. Są to te same właściwości, które pojawiają się w **właściwości** okna, jeśli został wybrany **Windows Forms Designer**. Możesz również wybrać metody, które informują składnik, aby wykonywały (np. otwarcie okna dialogowego).

        > [!NOTE]
        > **IntelliSense** okna można wyświetlić właściwości i metody. Aby ustalić, co jest pokazywane, spójrz na ikonę po lewej stronie każdej pozycji w **IntelliSense** okna. Obok każdej właściwości widzisz obraz bloku przy każdej metodzie i obraz klucza (lub klucz). Istnieje również ikonę pioruna obok każdego zdarzenia. Te obrazy wyświetlane są w następujący sposób.

         ![Ikona metody](../ide/media/express_iconmethod.png)

         ![Ikona Właściwość](../ide/media/express_iconproperty.png)

         ![Ikona zdarzenie](../ide/media/express_iconevent.png)

    4.  Rozpocznij wpisywanie `ShowDialog` (wielkość liter nie ma znaczenia w przypadku IntelliSense). `ShowDialog()` Wyświetli metodę **Otwórz plik** okno dialogowe. Po podświetleniu w oknie **ShowDialog**, wybierz **kartę** klucza. Możesz również wyróżnić "ShowDialog" i wybierz **F1** klawisz, aby uzyskać pomoc dotyczącą go.

         Aby dowiedzieć się więcej na temat `ShowDialog()` metody, zobacz [metoda ShowDialog](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

    5.  Kiedy używasz metody na kontrolce lub składnik (nazywane *wywołanie metody*), musisz dodać nawiasy. Wprowadź nawiasy otwierające i zamykające natychmiast po "g" w `ShowDialog`: `()` Teraz powinien on wyglądać "openFileDialog1.ShowDialog()".

        > [!NOTE]
        > Metody są ważną częścią dowolnego programu, a ten samouczek pokazał kilka sposobów wykorzystania metod. Można wywołać metodę składnika, aby nakazać mu coś, tak jak Wywołałeś **OpenFileDialog** składnika `ShowDialog()` metody. Można tworzyć swoje własne metody, które umożliwiają programowi wykonywanie czynności, jak ta, którą tworzymy teraz, o nazwie `showButton_Click()` metody, która otwiera okno dialogowe i obraz, gdy użytkownik wybierze przycisk.

    6.  Dla języka Visual C# Dodaj spację, a następnie dodaj dwa znaki równości (`==`). Dla języka Visual Basic Dodaj spację, a następnie użyj pojedynczego znaku równości (`=`). (Visual C# i Visual Basic używają różnych operatorów porównania).

    7.  Dodaj kolejną spację. Jak najszybciej zrobisz, inny **IntelliSense** zostanie otwarte okno. Rozpocznij wpisywanie `DialogResult` i wybierz polecenie **kartę** klawisz, aby ją dodać.

        > [!NOTE]
        > Podczas pisania kodu w celu wywołania metody czasami zwraca wartość. W tym przypadku **OpenFileDialog** składnika <xref:System.Windows.Forms.CommonDialog.ShowDialog> metoda zwraca <xref:System.Windows.Forms.DialogResult> wartość. DialogResult jest wartością specjalną, która informuje, co wydarzyło się w oknie dialogowym. **OpenFileDialog** składnika może spowodować wybór użytkownika **OK** lub **anulować**, więc jego `ShowDialog()` metoda zwraca albo `DialogResult.OK` lub `DialogResult.Cancel`.

    8.  Wpisz kropkę, aby otworzyć wartość DialogResult **IntelliSense** okna. Wprowadź literę `O` i wybierz polecenie **kartę** klawisz, aby wstawić **OK**.

         Aby dowiedzieć się więcej na temat DialogResult, zobacz [DialogResult](<xref:System.Windows.Forms.DialogResult>).

        > [!NOTE]
        >  Pierwszy wiersz kodu powinien być kompletny. Dla języka Visual C#, należy go poniżej.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  Dla języka Visual Basic powinien być następujący:.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Teraz Dodaj jeszcze jeden wiersz kodu. Możesz to wpisać (lub skopiuj i wklej ją), ale należy wziąć pod uwagę, dodaj go za pomocą technologii IntelliSense. Im więcej znasz technologię IntelliSense, tym szybciej można napisać własny kod. Ostateczna `showButton_Click()` metoda wygląda podobnie do następującej. (Wybierz **VB** kartę, aby wyświetlić wersję kodu w Visual Basic.)

         [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]
         [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 9: Przejrzyj, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).
