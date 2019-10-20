---
title: Krok 3. przypisanie losowej ikony do każdej etykiety | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4382a450051b7626a5eb5e29bf2ce4e78f6eceda
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671826"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3. Przypisanie losowej ikony do każdej etykiety
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, należy przypisać ikony losowo do kontrolek etykiet w formularzu za pomocą metody `AssignIconsToSquares()`.

### <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety

1. Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Istnieje nowe słowo kluczowe: `foreach` w wizualizacji C# i `For Each` w Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Dodaj metodę `AssignIconsToSquares()`, jak pokazano w poprzednim kroku. Można go umieścić tuż poniżej kodu dodanego w [kroku 2: dodać losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak wspomniano wcześniej, w metodzie `AssignIconsToSquares()` występuje coś nowego: Pętla `foreach` w wizualizacji C# i `For Each` w Visual Basic. Pętli `For Each` można użyć w dowolnym momencie, gdy chcesz wykonać tę samą czynność wiele razy. W tym przypadku chcesz wykonać te same instrukcje dla każdej etykiety w TableLayoutPanel, jak zostało wyjaśnione przez następujący kod. Pierwszy wiersz tworzy zmienną o nazwie `control`, która przechowuje każdy formant pojedynczo, podczas gdy kontrolka zawiera instrukcje w pętli wykonywanej.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.

     Metoda `AssignIconsToSquares()` iteruje przez poszczególne kontrolki etykiet w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje ściągają losowo ikonę z listy dodanej w [kroku 2: Dodaj losowy obiekt i listę ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Dlatego dołączono dwie z każdej ikony na liście, aby istniała para ikon przypisanych do losowych formantów etykiet.)

     Dokładniej sprawdzaj kod, który działa wewnątrz pętli `foreach` lub `For Each`. Ten kod jest przedstawiony tutaj.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     Pierwszy wiersz konwertuje zmienną `control` na etykietę o nazwie `iconLabel`. Wiersz po tym jest instrukcją `if`, która sprawdza, czy konwersja zadziałała. Jeśli konwersja działa, instrukcje w instrukcji `if` są uruchamiane. (Jak można przywołać z poprzednich samouczków, instrukcja `if` zostanie użyta do obliczenia dowolnego określonego warunku). Pierwszy wiersz w instrukcji `if` tworzy zmienną o nazwie `randomNumber`, która zawiera liczbę losową odpowiadającą jednemu z elementów na liście ikon. W tym celu używa metody `Next` obiektu `Random` utworzonego wcześniej. Metoda `Next` zwraca liczbę losową. Ten wiersz używa również właściwości `Count` listy `icons`, aby określić zakres, z którego ma zostać wybrana liczba losowa. Następny wiersz przypisuje jeden z elementów listy ikon do właściwości `Text` etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Na koniec ostatni wiersz instrukcji `if` usuwa z listy ikonę, która została dodana do formularza.

     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: krok po debugerze w programie Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) lub [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md) .

3. Aby wypełnić tablicę gier ikonami, należy wywołać metodę `AssignIconsToSquares()` zaraz po uruchomieniu programu. Jeśli używasz wizualizacji C#, Dodaj instrukcję tuż poniżej wywołania metody `InitializeComponent()` w*konstruktorze*`Form1`, dzięki czemu formularz wywoła nową metodę, aby skonfigurować ją przed wyświetleniem. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Aby uzyskać więcej informacji, zobacz [konstruktory (C# Przewodnik programowania)](https://msdn.microsoft.com/library/ace5hbzh.aspx) lub [Używanie konstruktorów i destruktorów](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) w Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Aby uzyskać Visual Basic, Dodaj wywołanie metody `AssignIconsToSquares()` do metody `Form1_Load`, aby kod wyglądał następująco.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.

5. Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.

     ![Dopasowywanie gry z losowymi ikonami](../ide/media/express-tut4step3.png "Express_Tut4Step3") Dopasowywanie gry z losowymi ikonami

     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby ukryć je z odtwarzacza, można ustawić właściwość `Forecolor` każdej etykiety na ten sam kolor, co Właściwość `BackColor`.

    > [!TIP]
    > Innym sposobem ukrycia formantów, takich jak etykiety, jest ustawienie właściwości **Visible** na `False`.

6. Aby ukryć ikony, Zatrzymaj program i usuń znaczniki komentarza dla wiersza z komentarzem do kodu wewnątrz pętli `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Na pasku menu wybierz przycisk **Zapisz wszystko** , aby zapisać program, a następnie uruchom go. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2. Dodawanie losowego obiektu i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
