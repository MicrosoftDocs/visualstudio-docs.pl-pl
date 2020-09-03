---
title: 'Przewodnik: testowanie w pierwszej kolejności przy użyciu funkcji generowania z użycia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f40ed5f3070f177d1c914495f78a223364d64ae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662676"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>Wskazówki: wcześniejsze testowanie obsługi przy użyciu funkcji generowania na podstawie sposobu użycia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie pokazano, jak używać funkcji [Generuj z użycia](../misc/generate-from-usage.md) , która obsługuje programowanie po raz pierwszy.

 *Programowanie w pierwszej kolejności* jest podejściem do projektowania oprogramowania, w którym najpierw można napisać testy jednostkowe na podstawie specyfikacji produktu, a następnie napisać kod źródłowy, który jest wymagany do pomyślnego wykonania testów. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje programowanie po raz pierwszy przez wygenerowanie nowych typów i elementów członkowskich w kodzie źródłowym podczas pierwszego odwoływania się do nich w przypadku testów, zanim zostaną zdefiniowane.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje nowe typy i członków z minimalnym zakłóceniem w przepływie pracy. Można tworzyć wycinki dla typów, metod, właściwości, pól lub konstruktorów bez opuszczania bieżącej lokalizacji w kodzie. Po otwarciu okna dialogowego, aby określić opcje generowania typów, fokus wraca natychmiast do bieżącego otwartego pliku po zamknięciu okna dialogowego.

 Funkcja generowania z użycia może być używana z platformami testów, które integrują się z usługą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W tym temacie przedstawiono strukturę testowania jednostkowego firmy Microsoft.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Aby utworzyć projekt biblioteki klas systemu Windows i projekt testowy

1. W programie [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Utwórz nowy projekt biblioteki klas systemu Windows. Nadaj mu nazwę `GFUDemo_VB` lub `GFUDemo_CS` , w zależności od języka, którego używasz.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy ikonę rozwiązania u góry, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** po lewej stronie kliknij pozycję **Testuj**.

3. W okienku **Szablony** kliknij pozycję **projekt testu jednostkowego** i zaakceptuj domyślną nazwę UnitTestProject1. Na poniższej ilustracji przedstawiono okno dialogowe, gdy pojawia się ono w [!INCLUDE[csprcs](../includes/csprcs-md.md)] . W programie okno [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dialogowe wygląda podobnie.

     ![Okno dialogowe nowego projektu testowego](../ide/media/newproject-test.png "NewProject_Test") Nowy projekt — okno dialogowe

4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Nowy projekt** .

5. W projekcie klasy w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy wpis **odwołania** i kliknij polecenie **Dodaj odwołanie**.

6. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **projekty** , a następnie wybierz projekt testu jednostkowego.

7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Menedżer odwołań** .

8. W pliku **Class1** , bezpośrednio po ostatnim z istniejących instrukcji **using** , Dodaj instrukcję **using** dla projektu testowego:

    * W Visual Basic, Dodaj `Using UnitTestProject1`

    * W języku C#, Dodaj `using UnitTestProject1;`

9. Zapisz rozwiązanie. Teraz możesz zacząć pisać testy

### <a name="to-generate-a-new-class-from-a-unit-test"></a>Aby wygenerować nową klasę z testu jednostkowego

1. Projekt testowy zawiera plik o nazwie UnitTest1. Kliknij dwukrotnie ten plik w **Eksplorator rozwiązań** , aby otworzyć go w edytorze kodu. Wygenerowano klasę testową i metodę testową.

2. Znajdź deklarację klasy `UnitTest1` i zmień jej nazwę na `AutomobileTest` . W języku C#, jeśli `UnitTest1()` jest obecny Konstruktor, zmień jego nazwę na `AutomobileTest()` .

    > [!NOTE]
    > Technologia IntelliSense oferuje teraz dwa alternatywy dla uzupełniania instrukcji IntelliSense: *Tryb uzupełniania* i *tryb sugestii*. Tryb sugestii służy do sytuacji, w których klasy i składowe są używane przed zdefiniowaniem. Gdy okno IntelliSense jest otwarte, możesz nacisnąć klawisze CTRL + ALT + SPACJa, aby przełączyć się między trybem uzupełniania i trybem sugestii. Aby uzyskać więcej informacji, zobacz [Używanie technologii IntelliSense](../ide/using-intellisense.md) . Tryb sugestii ułatwia wprowadzanie tekstu `Automobile` w następnym kroku.

3. Znajdź `TestMethod1()` metodę i zmień jej nazwę na `DefaultAutomobileIsInitializedCorrectly()` . Wewnątrz tej metody Utwórz nowe wystąpienie klasy o nazwie `Automobile` , jak pokazano na poniższej ilustracji. Zostanie wyświetlone faliste podkreślenie, które wskazuje na błąd w czasie kompilacji, a tag inteligentny pojawia się pod nazwą typu. Dokładna lokalizacja tagu inteligentnego różni się w zależności od tego, czy używasz programu, czy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] też [!INCLUDE[csprcs](../includes/csprcs-md.md)] .

     ![Podkreślanie tagów inteligentnych w Visual Basic](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB") Visual Basic

     ![Tag inteligentny podkreśla w języku C&#35;](../ide/media/genclass-underline.png "GenClass_Underline") Visual C #

4. Umieść wskaźnik myszy nad tagiem inteligentnym, aby wyświetlić komunikat o błędzie informujący o tym, że żaden typ nie `Automobile` jest jeszcze zdefiniowany. Kliknij tag inteligentny lub naciśnij klawisze CTRL +. (CTRL + kropka), aby otworzyć menu skrótów generowanie z użycia, jak pokazano na poniższej ilustracji.

     ![Menu kontekstowe tagów inteligentnych w Visual Basic](../ide/media/genclass-smartvb.png "GenClass_SmartVB") Visual Basic

     ![Menu kontekstowe tagów inteligentnych w języku C&#35;](../ide/media/genclass-smartcs.png "GenClass_SmartCS") Visual C #

5. Teraz masz dwie możliwości. Możesz kliknąć pozycję **Generuj "klasy Automobile"** , aby utworzyć nowy plik w projekcie testowym i wypełnić go pustą klasą o nazwie `Automobile` . Jest to szybka metoda tworzenia nowej klasy w nowym pliku, który ma domyślne Modyfikatory dostępu w bieżącym projekcie. Możesz również kliknąć pozycję **Generuj nowy typ** , aby otworzyć okno dialogowe **generowanie nowego typu** . Zapewnia to opcje, które obejmują umieszczenie klasy w istniejącym pliku i dodanie pliku do innego projektu.

     Kliknij przycisk **Generuj nowy typ** , aby otworzyć okno dialogowe **generowanie nowego typu** , które jest wyświetlane na poniższej ilustracji. Na liście **projekt** kliknij **GFUDemo_VB** lub **GFUDemo_CS** , aby polecić [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodanie pliku do projektu kodu źródłowego zamiast projektu testowego.

     ![Okno dialogowe generowanie nowego typu](../ide/media/genotherdialog.png "GenOtherDialog") Okno dialogowe generowanie nowego typu

6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe i utworzyć nowy plik.

7. W **Eksplorator rozwiązań**, poszukaj w węźle projektu GFUDemo_VB lub GFUDemo_CS, aby upewnić się, że nowy plik automobile. VB lub automobile.cs znajduje się w tym miejscu. W edytorze kodu fokus jest nadal w `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` . Możesz kontynuować pisanie testu z co najmniej przerwą.

### <a name="to-generate-a-property-stub"></a>Aby wygenerować Właściwość zastępczą

1. Załóżmy, że Specyfikacja produktu wskazuje, że `Automobile` Klasa ma dwie właściwości publiczne o nazwie `Model` i `TopSpeed` . Te właściwości muszą zostać zainicjowane przy użyciu wartości domyślnych `"Not specified"` i `-1` przez konstruktora domyślnego. Poniższy test jednostkowy sprawdzi, czy domyślny Konstruktor ustawi odpowiednie wartości domyślne.

     Dodaj następujący wiersz kodu do `DefaultAutomobileIsInitializedCorrectly` .

     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]

     Ponieważ kod odwołuje się do dwóch niezdefiniowanych właściwości w `Automobile` , zostanie wyświetlony tag inteligentny. Kliknij tag inteligentny dla `Model` , a następnie kliknij pozycję **Generuj procedurę tworzenia właściwości**. Wygeneruj również właściwość zastępczą właściwości `TopSpeed` .

     W `Automobile` klasie typy nowych właściwości są prawidłowo wnioskowane w kontekście.

     Na poniższej ilustracji przedstawiono menu skrótów tagów inteligentnych.

     ![Generuj menu kontekstowe właściwości w Visual Basic](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB") Visual Basic

     ![Generuj menu kontekstowe właściwości w języku C&#35;](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS") Visual C #

### <a name="to-locate-the-source-code"></a>Aby zlokalizować kod źródłowy

1. Użyj funkcji **Przejdź do** , aby przejść do pliku kodu źródłowego automobile.cs lub automobile. vb, aby sprawdzić, czy nowe właściwości zostały wygenerowane.

     Funkcja **Przechodzenie do** umożliwia szybkie wprowadzanie ciągu tekstowego, takiego jak nazwa typu lub część nazwy, i przejdź do odpowiedniej lokalizacji, klikając element na liście wyników.

     Otwórz okno dialogowe **Przejdź do** , klikając w edytorze kodu i naciskając klawisze CTRL +, (Ctrl + przecinek). W polu tekstowym wpisz `automobile` . Kliknij na liście klasę **Automobile** , a następnie kliknij przycisk **OK**.

     **Przechodzenie do** okna jest pokazane na poniższej ilustracji.

     ![Przejdź do okna dialogowego](../ide/media/navigate-2.png "Navigate_2") Przejdź do okna

### <a name="to-generate-a-stub-for-a-new-constructor"></a>Aby wygenerować element zastępczy dla nowego Konstruktora

1. W tej metodzie testowej zostanie wygenerowana procedura tworzenia konstruktora, która będzie `Model` inicjować `TopSpeed` właściwości i w celu zdefiniowania określonych wartości. Później dodasz więcej kodu do ukończenia testu. Dodaj następującą dodatkową metodę testową do `AutomobileTest` klasy.

     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]

2. Kliknij tag inteligentny pod nowym konstruktorem klasy, a następnie kliknij pozycję **Generuj Konstruktor zastępczy**. W `Automobile` pliku klasy należy zauważyć, że nowy Konstruktor zbadał nazwy zmiennych lokalnych, które są używane w wywołaniu konstruktora, znaleziono właściwości, które mają takie same nazwy w `Automobile` klasie, i dostarczony kod w treści konstruktora do przechowywania wartości argumentów we `Model` `TopSpeed` właściwościach i. (W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , `_model` pola i `_topSpeed` w nowym konstruktorze to niejawnie zdefiniowane pola zapasowe dla `Model` właściwości i `TopSpeed` .)

3. Po wygenerowaniu nowego konstruktora faliste podkreślenie pojawia się pod wywołaniem konstruktora domyślnego w `DefaultAutomobileIsInitializedCorrectly` . Komunikat o błędzie stwierdza, że `Automobile` Klasa nie ma konstruktora, który przyjmuje zero argumentów. Aby wygenerować jawny Konstruktor domyślny, który nie ma parametrów, kliknij tag inteligentny, a następnie kliknij pozycję **Generuj Konstruktor zastępczy**.

### <a name="to-generate-a-stub-for-a-method"></a>Aby wygenerować element zastępczy dla metody

1. Przyjęto założenie, że Specyfikacja wskazuje, że nowa wartość `Automobile` może zostać wprowadzona do stanu uruchomienia, jeśli jej `Model` `TopSpeed` właściwości i są ustawione na wartość inną niż wartości domyślne. Dodaj następujące wiersze do `AutomobileWithModelNameCanStart` metody.

     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]

2. Kliknij tag inteligentny dla `myAuto.Start` wywołania metody, a następnie kliknij pozycję **Generuj procedurę zastępczą metody**.

3. Kliknij tag inteligentny dla `IsRunning` właściwości, a następnie kliknij pozycję **Generuj procedurę zastępczą właściwości**. `Automobile`Klasa zawiera teraz Poniższy kod.

     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]

### <a name="to-run-the-tests"></a>Aby uruchomić testy

1. W menu **test jednostki** wskaż polecenie **Uruchom testy jednostkowe**, a następnie kliknij pozycję **wszystkie testy**. To polecenie uruchamia wszystkie testy we wszystkich strukturach testowych, które są zapisywane dla bieżącego rozwiązania.

     W takim przypadku istnieją dwa testy i w oczekiwany sposób kończą się niepowodzeniem. `DefaultAutomobileIsInitializedCorrectly`Test zakończy się niepowodzeniem, ponieważ `Assert.IsTrue` zwraca warunek `False` . `AutomobileWithModelNameCanStart`Test nie powiódł się, ponieważ `Start` Metoda w `Automobile` klasie zgłasza wyjątek.

     Okno **wyniki testów** jest pokazane na poniższej ilustracji.

     ![Wyniki testu, które zakończyły się niepowodzeniem](../ide/media/testsfailed.png "TestsFailed") Okno Wyniki testów

2. W oknie **wyniki testów** kliknij dwukrotnie każdy wiersz wyniku testu, aby przejść do lokalizacji każdego błędu testu.

### <a name="to-implement-the-source-code"></a>Aby zaimplementować kod źródłowy

1. Dodaj następujący kod do konstruktora domyślnego, aby `Model` `TopSpeed` `IsRunning` wszystkie właściwości i wszystkie były zainicjowane do ich prawidłowych wartości domyślnych `"Not specified"` , `-1` i `True` ( `true` ).

     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]

2. Gdy `Start` Metoda jest wywoływana, należy ustawić `IsRunning` flagę na wartość true tylko wtedy, gdy `Model` `TopSpeed` właściwości lub są ustawione na inną niż wartość domyślna. Usuń `NotImplementedException` z treści metody i Dodaj następujący kod.

     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]

### <a name="to-run-the-tests-again"></a>Aby ponownie uruchomić testy

1. W menu **test** wskaż polecenie **Uruchom**, a następnie kliknij pozycję **wszystkie testy w rozwiązaniu**. Ta godzina przebiegu testów. Okno **wyniki testów** jest pokazane na poniższej ilustracji.

     ![Wyniki testów, które zostały zakończone](../ide/media/testspassed.png "TestsPassed") Okno Wyniki testów

## <a name="see-also"></a>Zobacz też
 [Generuj na podstawie](../misc/generate-from-usage.md) [pisania kodu](../ide/writing-code-in-the-code-and-text-editor.md) użycie [za pomocą](../ide/using-intellisense.md) [testu jednostkowego IntelliSense kod](../test/unit-test-your-code.md)
