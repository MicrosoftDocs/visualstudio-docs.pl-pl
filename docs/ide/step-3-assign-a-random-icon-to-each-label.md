---
title: Krok 3. Przypisywanie losowej ikony do każdej etykiety
ms.date: 03/21/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 627b798827cd0b966d1f34336c7e1119841f9d4a
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472631"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3. Przypisywanie losowej ikony do każdej etykiety

Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, przypisz ikony losowo do formantów Label w formularzu `AssignIconsToSquares()` za pomocą metody.

## <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety

1. Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Jest nowe słowo kluczowe: `foreach` w `For Each` języku C# i visual basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Dodaj `AssignIconsToSquares()` metodę, jak pokazano w poprzednim kroku. Możesz umieścić go tuż pod kodem dodanym w [kroku 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak wspomniano wcześniej, istnieje coś nowego `AssignIconsToSquares()` w `foreach` metodzie: pętla w języku C# i `For Each` visual basic. Pętlę `For Each` można użyć w dowolnym momencie, gdy chcesz wykonać tę samą czynność wiele razy. W takim przypadku chcesz wykonać te same instrukcje <xref:System.Windows.Forms.TableLayoutPanel>dla każdej etykiety na swojej , jak wyjaśniono w poniższym kodzie. Pierwszy wiersz tworzy zmienną o nazwie, `control` która przechowuje każdy formant po jednym naraz, podczas gdy ten formant ma instrukcje w pętli wykonywane na nim.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.

     Metoda `AssignIconsToSquares()` iteruje za pośrednictwem każdego formantu etykiety w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje wyciągają losową ikonę z listy dodanej w [kroku 2: Dodaj obiekt Random i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Przypominamy, że każda z tych ikon jest literą w czcionce Webdings, dlatego są one wyrażone jako tekst w tej metodzie. Na liście znalazły się dwie ikony, dzięki czemu do losowych kontrolek etykiet przypisano parę ikon.

     Przyjrzyj się bliżej kodowi, który działa wewnątrz `foreach` lub `For Each` pętli. Ten kod jest przedstawiony tutaj.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     Pierwszy wiersz konwertuje zmienną **formantu** na etykietę o nazwie **iconLabel**. Wiersz po tym `if` jest instrukcja, która sprawdza, aby upewnić się, że konwersja zadziałała. Jeśli konwersja działa, instrukcje `if` w instrukcji są uruchamiane. (Jak można przypomnieć z poprzednich samouczków, instrukcja `if` jest używana do oceny niezależnie od warunku określisz.) Pierwszy wiersz w `if` instrukcji tworzy zmienną o nazwie **randomNumber,** która zawiera losową liczbę odpowiadającą jednemu z elementów na liście ikon. Aby to zrobić, używa <xref:System.Random.Next> metody <xref:System.Random> obiektu, który został utworzony wcześniej. Metoda `Next` zwraca liczbę losową. Ten wiersz używa <xref:System.Collections.Generic.List%601.Count> również właściwości listy **ikon,** aby określić zakres, z którego można wybrać liczbę losową. Następny wiersz przypisuje jeden z elementów <xref:System.Windows.Forms.Label.Text> listy ikon do właściwości etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Na koniec ostatni wiersz `if` w instrukcji usuwa z listy ikonę, która została dodana do formularza.

     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [Jak: Krok z debugerem w programie Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) lub [Nawiguj po kodzie z debugerem, aby](../debugger/navigating-through-code-with-the-debugger.md) uzyskać więcej informacji.

3. Aby wypełnić planszę z ikonami, musisz `AssignIconsToSquares()` wywołać metodę, gdy tylko program zostanie uruchomiony. Jeśli używasz języka C#, dodaj instrukcję tuż `InitializeComponent()` poniżej wywołania do metody w _konstruktorze_ **Form1,** więc formularz wywołuje nową metodę, aby skonfigurować się przed jej pokazano. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktory (Przewodnik programowania Języka C# lub](/dotnet/csharp/programming-guide/classes-and-structs/constructors) [Użyj konstruktorów i destruktorów](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) w języku Visual Basic, aby uzyskać więcej informacji.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     W języku Visual `AssignIconsToSquares()` Basic dodaj `Form1_Load` wywołanie metody do metody, tak aby kod wyglądał następująco.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety. 

5. Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji. 

     ![Gra w dopasowywanie z losowymi ikonami](../ide/media/express_tut4step3.png)<br/>
*Gra w dopasowywanie z losowymi ikonami*

     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby ukryć je przed odtwarzaczem, można ustawić właściwości **ForeColor** każdej etykiety na ten sam kolor, co jego właściwość **BackColor.**

6. Aby ukryć ikony, zatrzymaj program i usuń znaczniki komentarzy `For Each` dla komentowanego wiersza kodu wewnątrz pętli.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na pasku menu wybierz przycisk **Zapisz wszystko,** aby zapisać program, a następnie uruchom go. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 4: Dodawanie programu obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 2: Dodawanie obiektu Random i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
