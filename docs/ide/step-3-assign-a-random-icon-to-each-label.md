---
title: Krok 3. Przypisywanie losowej ikony do każdej etykiety
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4b635f86eb67f04db3ba6243e7b0ba4634bfb4
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416665"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3. Przypisywanie losowej ikony do każdej etykiety
Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, należy przypisać ikony losowo do kontrolek etykiet w formularzu przy użyciu `AssignIconsToSquares()` metody.

## <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety

1. Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Istnieje nowe słowo kluczowe: `foreach` w wizualizacji C# i `For Each` w Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

2. `AssignIconsToSquares()` Dodaj metodę, jak pokazano w poprzednim kroku. Możesz go umieścić tuż poniżej kodu dodanego w [kroku 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak `AssignIconsToSquares()` wspomniano wcześniej, istnieją nowe metody `foreach` : Pętla w wizualizacji C# i `For Each` w Visual Basic. `For Each` Pętli można użyć w dowolnym momencie, gdy chcesz wykonać tę samą czynność wiele razy. W takim przypadku należy wykonać te same instrukcje dla każdej etykiety w <xref:System.Windows.Forms.TableLayoutPanel>, jak wyjaśniono w poniższym kodzie. Pierwszy wiersz tworzy zmienną o nazwie `control` , która przechowuje każdy formant pojedynczo, podczas gdy kontrolka zawiera instrukcje w pętli wykonanej.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.

     `AssignIconsToSquares()` Metoda iteruje przez każdy formant etykiety w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje ściągają losowo ikonę z listy dodanej w [kroku 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Dlatego zostały uwzględnione dwie z każdej ikony na liście, więc będzie istnieć para ikon przypisanych do losowych kontrolek etykiet.)

     Dokładniej sprawdzaj kod, który jest uruchamiany wewnątrz `foreach` pętli lub. `For Each` Ten kod jest przedstawiony tutaj.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     Pierwszy wiersz konwertuje zmienną **sterującą** na etykietę o nazwie **iconLabel**. Wiersz po tym jest `if` instrukcją, która sprawdza, czy konwersja zadziałała. Jeśli konwersja działa, instrukcje w instrukcji są `if` uruchamiane. (Jak można przywołać z poprzednich samouczków, `if` instrukcja zostanie użyta do obliczenia dowolnego określonego warunku). Pierwszy wiersz w `if` instrukcji tworzy zmienną o nazwie **randomNumber** , która zawiera liczbę losową odpowiadającą jednemu z elementów na liście ikon. W tym celu używa <xref:System.Random.Next> metody <xref:System.Random> obiektu, który został utworzony wcześniej. `Next` Metoda zwraca liczbę losową. Ten wiersz używa <xref:System.Collections.Generic.List%601.Count> również właściwości listy **ikon** do określenia zakresu, z którego ma zostać wybrana liczba losowa. Następny wiersz przypisuje jeden z elementów listy ikon do <xref:System.Windows.Forms.Label.Text> właściwości etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Na koniec ostatni wiersz w `if` instrukcji usuwa z listy ikonę, która została dodana do formularza.

     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [jak mogę: Krok z debugerem w programie Visual Studio? lub [Przejdź przez kod za pomocą debugera,](../debugger/navigating-through-code-with-the-debugger.md) Aby uzyskać więcej informacji. ](https://msdn.microsoft.com/vstudio/ee672313.aspx)

3. Aby wypełnić tablicę gier ikonami, musisz wywołać `AssignIconsToSquares()` metodę zaraz po uruchomieniu programu. Jeśli używasz C#wizualizacji, Dodaj instrukcję tuż poniżej `InitializeComponent()` wywołania metody w_konstruktorze_ **Form1**, więc formularz wywoła nową metodę, aby skonfigurować ją przed wyświetleniem. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktoryC# (Przewodnik programowania)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) lub [Użyj konstruktorów i destruktorów](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) w Visual Basic, aby uzyskać więcej informacji.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     W przypadku Visual Basic Dodaj `AssignIconsToSquares()` wywołanie metody `Form1_Load` do metody, aby kod wyglądał następująco.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.

5. Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.

     ![Gra w dopasowywanie z](../ide/media/express_tut4step3.png) losowymi ikonami odpowiadającymi grze z losowymi ikonami

     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby ukryć je z odtwarzacza, można ustawić właściwość **ForeColor** każdej etykiety na ten sam kolor, co Właściwość **BackColor** .

    > [!TIP]
    > Innym sposobem ukrycia formantów, takich jak etykiety, jest ustawienie właściwości **Visible** na **wartość false**.

6. Aby ukryć ikony, Zatrzymaj program i usuń znaczniki komentarza dla wiersza z komentarzami kodu wewnątrz `For Each` pętli.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na pasku menu wybierz przycisk **Zapisz wszystko** , aby zapisać program, a następnie uruchom go. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodaj program obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
