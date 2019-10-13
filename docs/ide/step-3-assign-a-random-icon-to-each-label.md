---
title: 'Krok 3: Przypisywanie losowej ikony do każdej etykiety'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a670ec4b5b6689c68820b37b20a4e1a942dc3bd
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289609"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Przypisywanie losowej ikony do każdej etykiety
Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, należy przypisać ikony losowo do kontrolek etykiet w formularzu przy użyciu metody `AssignIconsToSquares()`.

## <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety

1. Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Istnieje nowe słowo kluczowe: `foreach` w wizualizacji C# i `For Each` w Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment C# kodu lub Visual Basic fragment kodu.<br><br>0Programming — kontrola języka dla dokumentacji docs. Microsoft. com @ no__t-1 @no__t

2. Dodaj metodę `AssignIconsToSquares()`, jak pokazano w poprzednim kroku. Możesz go umieścić tuż poniżej kodu dodanego w [Step 2: Dodaj losowy obiekt i listę ikon @ no__t-0.

     Jak wspomniano wcześniej, istnieje coś nowego w metodzie `AssignIconsToSquares()`: Pętla `foreach` w wizualizacji C# i `For Each` w Visual Basic. Można użyć pętli `For Each` w dowolnym momencie, gdy chcesz wykonać tę samą akcję wiele razy. W takim przypadku należy wykonać te same instrukcje dla każdej etykiety na <xref:System.Windows.Forms.TableLayoutPanel>, jak wyjaśniono w poniższym kodzie. Pierwszy wiersz tworzy zmienną o nazwie `control`, która przechowuje każdy formant pojedynczo, podczas gdy kontrolka zawiera instrukcje w pętli wykonanej.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.

     Metoda `AssignIconsToSquares()` iteruje przez poszczególne kontrolki etykiet w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje pobierają losową ikonę z listy dodanej w [Step 2: Dodaj losowy obiekt i listę ikon @ no__t-0. (Dlatego zostały uwzględnione dwie z każdej ikony na liście, więc będzie istnieć para ikon przypisanych do losowych kontrolek etykiet.)

     Dokładniej sprawdzaj kod, który działa w pętli `foreach` lub `For Each`. Ten kod jest przedstawiony tutaj.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     Pierwszy wiersz konwertuje zmienną **sterującą** na etykietę o nazwie **iconLabel**. Wiersz po tym jest instrukcją `if`, która sprawdza, czy konwersja zadziałała. Jeśli konwersja działa, instrukcje w instrukcji `if` są uruchamiane. (Jak można przywołać z poprzednich samouczków, instrukcja `if` służy do obliczenia dowolnego określonego warunku). Pierwszy wiersz w instrukcji `if` tworzy zmienną o nazwie **randomNumber** , która zawiera liczbę losową odpowiadającą jednemu z elementów na liście ikon. W tym celu używa metody <xref:System.Random.Next> obiektu <xref:System.Random> utworzonego wcześniej. Metoda `Next` zwraca liczbę losową. Ten wiersz używa również właściwości <xref:System.Collections.Generic.List%601.Count> listy **ikon** , aby określić zakres, z którego ma zostać wybrana liczba losowa. Następny wiersz przypisuje jeden z elementów listy ikon do właściwości <xref:System.Windows.Forms.Label.Text> etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Na koniec ostatni wiersz w instrukcji `if` usuwa z listy ikonę, która została dodana do formularza.

     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [How: Wejdź do debugera w programie Visual Studio? ](https://msdn.microsoft.com/vstudio/ee672313.aspx) lub [Przejdź przez kod za pomocą debugera,](../debugger/navigating-through-code-with-the-debugger.md) Aby uzyskać więcej informacji.

3. Aby wypełnić tablicę gier ikonami, należy wywołać metodę `AssignIconsToSquares()` zaraz po uruchomieniu programu. Jeśli używasz wizualizacji C#, Dodaj instrukcję tuż poniżej wywołania metody `InitializeComponent()` w_konstruktorze_ **Form1**, więc formularz wywoła nową metodę, aby skonfigurować ją przed wyświetleniem. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktoryC# (Przewodnik programowania)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) lub [Użyj konstruktorów i destruktorów](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) w Visual Basic, aby uzyskać więcej informacji.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Dla Visual Basic Dodaj wywołanie metody `AssignIconsToSquares()` do metody `Form1_Load`, aby kod wyglądał następująco.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.

5. Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.

     gra @no__t 0Matching z losowymi ikonami @ no__t-1 Dopasowywanie gier z losowymi ikonami

     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby ukryć je z odtwarzacza, można ustawić właściwość **ForeColor** każdej etykiety na ten sam kolor, co Właściwość **BackColor** .

    > [!TIP]
    > Innym sposobem ukrycia formantów, takich jak etykiety, jest ustawienie właściwości **Visible** na **wartość false**.

6. Aby ukryć ikony, Zatrzymaj program i usuń znaczniki komentarza dla wiersza z komentarzem (kod wewnątrz pętli `For Each`).

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na pasku menu wybierz przycisk **Zapisz wszystko** , aby zapisać program, a następnie uruchom go. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Step 4: Dodaj program obsługi zdarzeń kliknięcia do każdej etykiety @ no__t-0.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Step 2: Dodaj losowy obiekt i listę ikon @ no__t-0.
