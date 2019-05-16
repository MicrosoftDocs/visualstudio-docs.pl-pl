---
title: Krok 3. Przypisanie losowej ikony do każdej etykiety | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d65d1a758523aaf7652f2d47bec50aa9fdb91884
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694008"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3. Przypisywanie losowej ikony do każdej etykiety
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, przypisz ikony losowo do formantów etykiet w formularzu za pomocą `AssignIconsToSquares()` metody.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety  
  
1. Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Istnieje nowe słowo kluczowe: `foreach` w języku Visual C# i `For Each` w języku Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]  
  
2. Dodaj `AssignIconsToSquares()` metody, jak pokazano w poprzednim kroku. Możesz ją umieścić tuż pod kodem dodanym w [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Jak wspomniano wcześniej, jest coś, co nowego w swojej `AssignIconsToSquares()` metoda: `foreach` pętli w języku Visual C# i `For Each` w języku Visual Basic. Możesz użyć `For Each` pętli w dowolnym momencie, co chcesz zrobić to ta sama akcja wiele razy. W tym przypadku chcesz wykonać te same instrukcje dla każdej etykiety w TableLayoutPanel, jak zostało wyjaśnione przez następujący kod. Pierwszy wiersz tworzy zmienną o nazwie `control` która przechowuje każdy jeden formant naraz podczas czy formant ma instrukcje w pętli wykonywanej na nim.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]  
  
    > [!NOTE]
    > Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.  
  
     `AssignIconsToSquares()` Metoda iteruje przez każdy formant etykiety w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje pobierają losową ikonę z listy, dodanej w [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Dlatego dołączono dwie z każdej ikony na liście, aby istniała para ikon przypisanych do losowych formantów etykiet.)  
  
     Przyjrzyj się dokładniej kodowi który działa wewnątrz `foreach` lub `For Each` pętli. Ten kod jest przedstawiony tutaj.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]  
  
     Pierwszy wiersz konwertuje `control` zmienną etykietę o nazwie `iconLabel`. Wiersz po tym to `if` instrukcję, która sprawdza, aby upewnić się, że konwersja zadziałała. Jeśli konwersja działa, instrukcje `if` Uruchom instrukcję. (Może pamiętasz z poprzednich samouczków `if` instrukcja jest używane do oceny dowolnego określonego warunku.) W pierwszym wierszu `if` instrukcja tworzy zmienną o nazwie `randomNumber` zawierającą liczbę losową, która odnosi się do jednego z elementów na liście ikon. Aby to zrobić, używa `Next` metody `Random` obiektu, który został utworzony wcześniej. `Next` Metoda zwraca liczbę losową. Ten wiersz używa także `Count` właściwość `icons` listy, aby określić zakres, z którego można wybrać liczbę losową. Następny wiersz przypisuje jeden ikony elementów listy, aby `Text` właściwości etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Na koniec, ostatni wiersz w `if` instrukcja powoduje usunięcie z listy ikonę, która została dodana do formularza.  
  
     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [jak: Krok za pomocą debugera programu Visual Studio? ](https://msdn.microsoft.com/vstudio/ee672313.aspx) lub [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md) Aby uzyskać więcej informacji.  
  
3. Aby wypełnić planszę gry ikonami, musisz wywołać `AssignIconsToSquares()` metoda zaraz po uruchomieniu programu. Jeśli używasz Visual C#, Dodaj instrukcję tuż poniżej wywołania `InitializeComponent()` method in Class metoda `Form1` *Konstruktor*, aby formularz wywoływał nową metodę w celu skonfigurowania się przed wyświetleniem. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktorów (C# Programming Guide)](https://msdn.microsoft.com/library/ace5hbzh.aspx) lub [korzystanie z konstruktorów i destruktorów](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) w języku Visual Basic, aby uzyskać więcej informacji.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]  
  
     Dla języka Visual Basic należy dodać `AssignIconsToSquares()` wywołanie metody do `Form1_Load` metody, aby kod wyglądał następująco.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4. Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.  
  
5. Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.  
  
     ![Gra w dopasowywanie z losowymi ikonami](../ide/media/express-tut4step3.png "Express_Tut4Step3")  
Gra w dopasowywanie z losowymi ikonami  
  
     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby ukryć je przed graczem, możesz ustawić każdej etykiety `Forecolor` właściwość sam kolor jak kolor jego `BackColor` właściwości.  
  
    > [!TIP]
    > Innym sposobem na ukrycie formantów, takich jak etykiety, jest ustalenie ich **Visible** właściwość `False`.  
  
6. Aby ukryć ikony, należy zatrzymać program i usunąć znaki komentarza dla zakomentowanego wiersza kodu wewnątrz `For Each` pętli.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]  
  
7. Na pasku menu wybierz **Zapisz wszystko** przycisk, aby zapisać swój program, a następnie uruchom go. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
- Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
