---
title: 'Przewodnik: Wcześniejsze testowanie obsługi przy użyciu użycia funkcji generowania na podstawie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1dd1598d73cdbd77bc6fe0cb35e639c0fb484b0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443422"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>Przewodnik: Wcześniejsze testowanie obsługi przy użyciu użycia funkcji generowania na podstawie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie przedstawiono sposób użycia [Generowanie z użycia](../misc/generate-from-usage.md) funkcji, która obsługuje rozwoju pierwszego badania.  
  
 *Rozwoju pierwszego badania* to podejście do projektowania oprogramowania, w której najpierw pisanie testów jednostkowych, w oparciu o specyfikacje produktów, a następnie napisać kod źródłowy, który jest wymagana do udostępnienia testów powiodło się. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Obsługa wczesnego testowania programowania, generując nowe typy i członkowie w kodzie źródłowym, gdy użytkownik najpierw odwołać je w przypadki testowe, zanim nie zostaną zdefiniowane.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje nowe typy i elementy członkowskie z minimalną przerwą do przepływu pracy. Możesz utworzyć wycinków dla typów, metod, właściwości, pola lub konstruktory bez opuszczania Twojej bieżącej lokalizacji w kodzie. Gdy otworzysz okno dialogowe, aby określić opcje dla generowania typów, powrót natychmiast do bieżący plik otwarty po zamknięciu okna dialogowego.  
  
 Funkcja Generowanie z użycia może być używana przy użyciu środowisk testowych, które integrują się z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W tym temacie przedstawiono Frameworka testów jednostkowych firmy Microsoft.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Aby utworzyć projekt biblioteki klas Windows i Projekt testowy  
  
1. W [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], Utwórz nowy projekt biblioteki klas Windows. Nadaj mu nazwę `GFUDemo_VB` lub `GFUDemo_CS`, w zależności od języka, których używasz.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy ikonę rozwiązanie u góry, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**. W **nowy projekt** dialogowym **typów projektów** w okienku po lewej stronie, kliknij pozycję **testu**.  
  
3. W **szablony** okienku kliknij **projektu testu jednostkowego** i zaakceptuj domyślną nazwę UnitTestProject1. Na poniższej ilustracji przedstawiono okno dialogowe, gdy zostanie on wyświetlony na [!INCLUDE[csprcs](../includes/csprcs-md.md)]. W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], okno dialogowe jest podobny.  
  
     ![Okno dialogowe Nowy projekt testowy](../ide/media/newproject-test.png "NewProject_Test")  
Okno dialogowe Nowy projekt  
  
4. Kliknij przycisk **OK** zamknąć **nowy projekt** okno dialogowe.

5. W projekcie klasy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** wpis, a następnie kliknij przycisk **Dodaj odwołanie**.

6. W **Menadżer odwołań** okno dialogowe, wybierz opcję **projektów** a następnie wybierz pozycję projektu testu jednostkowego.

7. Kliknij przycisk **OK** zamknąć **Menadżer odwołań** okno dialogowe.

8. W **klasa1** pliku natychmiast po ostatnim istniejącej **przy użyciu** instrukcji, Dodaj **przy użyciu** poufności informacji dla projektu testowego:

    * W języku Visual Basic Dodaj `Using UnitTestProject1`
    
    * W języku C# Dodaj `using UnitTestProject1;`
    
9. Zapisz swoje rozwiązanie. Teraz można przystąpić do rozpoczęcia pisania testów  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>Aby wygenerować nową klasę z testu jednostkowego  
  
1. Projekt testowy zawiera plik o nazwie Testjednostki1. Kliknij dwukrotnie ten plik w **Eksploratora rozwiązań** aby go otworzyć w edytorze kodu. Zostały wygenerowane klasy testowej i metody testowej.  
  
2. Znajdź w deklaracji klasy `UnitTest1` i zmień jej nazwę na `AutomobileTest`. W języku C# Jeśli `UnitTest1()` konstruktora, zmień jej nazwę na `AutomobileTest()`.  
  
    > [!NOTE]
    > Technologia IntelliSense zawiera teraz dwa warianty dla instrukcji IntelliSense: *trybem uzupełniania* i *trybem sugestii*. Tryb sugestii w sytuacjach, w których klas i składowych są wykorzystywane przed są zdefiniowane. Gdy okno technologii IntelliSense jest otwarty, możesz nacisnąć klawisze CTRL + ALT + SPACJA, aby przełączyć między trybem uzupełniania a trybem sugestii. Zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md) Aby uzyskać więcej informacji. Tryb sugestii pomoże podczas wpisywania `Automobile` w następnym kroku.  
  
3. Znajdź `TestMethod1()` metody i zmień jej nazwę na `DefaultAutomobileIsInitializedCorrectly()`. Tej metody, Utwórz nowe wystąpienie klasy o nazwie `Automobile`, jak pokazano na poniższych ilustracjach. Faliste podkreślenie pojawia się, co oznacza błąd w czasie kompilacji i tagów inteligentnych pojawia się pod nazwą typu. Dokładna lokalizacja tagu inteligentnego różni się w zależności od tego, czy używasz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
     ![Inteligentne podkreślenie tagu w języku Visual Basic](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB")  
Visual Basic  
  
     ![Inteligentne podkreślenie tagu w języku C&#35;](../ide/media/genclass-underline.png "GenClass_Underline")  
Visual C#  
  
4. Zatrzymaj wskaźnik myszy nad tagu inteligentnego, aby wyświetlić komunikat o błędzie z informacją, że żaden typ o nazwie `Automobile` jeszcze zdefiniowana. Kliknij tag inteligentny, lub naciśnij klawisze CTRL +. (CTRL + okres) aby otworzyć menu skrótów Generowanie z użycia, jak pokazano na poniższych ilustracjach.  
  
     ![Blokada Smart Menu kontekstowe tagu w języku Visual Basic](../ide/media/genclass-smartvb.png "GenClass_SmartVB")  
Visual Basic  
  
     ![Blokada Smart Menu kontekstowe tagu w języku C&#35;](../ide/media/genclass-smartcs.png "GenClass_SmartCS")  
Visual C#  
  
5. Teraz masz dwie możliwości. Możesz kliknąć przycisk **Wygeneruj "Klasy samochodów"** Utwórz nowy plik w projekcie testu i wypełnić je z pustą klasę o nazwie `Automobile`. Jest to szybki sposób tworzenia nowych klas w nowym plikiem oznaczonym ma domyślne modyfikatory dostępu w bieżącym projekcie. Możesz również kliknąć **Generuj nowy typ** otworzyć **Generuj nowy typ** okno dialogowe. Zapewnia to opcje, takie jak wysyłanie klasy w istniejącym pliku i dodawania pliku do innego projektu.  
  
     Kliknij przycisk **Generuj nowy typ** otworzyć **Generuj nowy typ** okno dialogowe, co zostało pokazane na poniższej ilustracji. W **projektu** kliknij **GFUDemo_VB** lub **GFUDemo_CS** nakazać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można dodać plik do projektu kodu źródłowego, a nie projekt testowy.  
  
     ![Okno dialogowe Nowy typ Generowanie](../ide/media/genotherdialog.png "GenOtherDialog")  
Generuj nowy typ, okno dialogowe  
  
6. Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć nowy plik.  
  
7. W **Eksploratora rozwiązań**, Szukaj w węźle projektu GFUDemo_VB lub GFUDemo_CS, aby sprawdzić, czy nowe Automobile.vb lub pliku Automobile.cs ma. W edytorze kodu fokus nadal znajduje się w `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. Można nadal Napisz test z co najmniej przerwania.  
  
### <a name="to-generate-a-property-stub"></a>Do generowania szkieletu właściwości  
  
1. Przyjęto założenie, opis produktu stanowi, że `Automobile` klasa ma dwie właściwości publiczne, o nazwie `Model` i `TopSpeed`. Te właściwości musi zostać zainicjowany z wartościami domyślnymi `"Not specified"` i `-1` przez konstruktora domyślnego. Następujący test jednostkowy sprawdzi, czy domyślny konstruktor ustawia właściwości do wartości domyślnych poprawne.  
  
     Dodaj następujący wiersz kodu w celu `DefaultAutomobileIsInitializedCorrectly`.  
  
     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]  
  
     Ponieważ kod odwołuje się do dwóch niezdefiniowanymi właściwościami na `Automobile`, tagu inteligentnego. Kliknij tag inteligentny dla `Model` a następnie kliknij przycisk **generowania szkieletu właściwości**. Generowania szkieletu właściwości dla `TopSpeed` właściwości również.  
  
     W `Automobile` klasy, typy nowe właściwości poprawnie są dedukowane z kontekstu.  
  
     Poniższa ilustracja przedstawia menu skrótów tagu inteligentnego.  
  
     ![Generuj właściwość menu kontekstowego w języku Visual Basic](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB")  
Visual Basic  
  
     ![Generuj właściwość menu kontekstowego w języku C&#35;](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS")  
Visual C#  
  
### <a name="to-locate-the-source-code"></a>Aby zlokalizować kod źródłowy  
  
1. Użyj **przejdź do** funkcji przejdź do pliku kodu źródłowego Automobile.cs lub Automobile.vb, dzięki czemu może sprawdzić, czy zostały wygenerowane nowe właściwości.  
  
     **Przejdź do** pozwala szybko wprowadzić ciąg tekstowy, na przykład wpisz nazwę lub część nazwy i przejdź do odpowiedniej lokalizacji, klikając element na liście wyników.  
  
     Otwórz **przejdź do** okno dialogowe, klikając w edytorze kodu, a następnie naciskając klawisze CTRL +, (CTRL + przecinek). W polu tekstowym wpisz `automobile`. Kliknij przycisk **samochodów** klasy na liście, a następnie kliknij przycisk **OK**.  
  
     **Przejdź do** na poniższej ilustracji przedstawiono okno.  
  
     ![Nawiguj do okna dialogowego](../ide/media/navigate-2.png "Navigate_2")  
Nawiguj do okna  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>Można wygenerować klasy zastępczej dla nowego Konstruktora  
  
1. W przypadku tej metody testu wygeneruje odcinek Konstruktor, który będzie inicjował `Model` i `TopSpeed` właściwości mogą mieć wartości, które określisz. Później dodasz więcej kodu, aby ukończyć test. Dodaj następującą metodę dodatkowy test, aby Twoje `AutomobileTest` klasy.  
  
     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]  
  
2. Kliknij tag inteligentny w ramach nowego konstruktora klasy, a następnie kliknij przycisk **Generuj Konstruktor wycinka**. W `Automobile` klasy pliku, zwróć uwagę, że nowy konstruktor ma zbadać nazwy zmiennych lokalnych, które są używane w wywołaniu konstruktora, podczas gdy znaleziono właściwości, które mają takie same nazwy w `Automobile` klasy i podany kod w treści konstruktora, celu przechowywanie wartości argumentu w `Model` i `TopSpeed` właściwości. (W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `_model` i `_topSpeed` pól w Konstruktorze nowe są pola zapasowego niejawnie zdefiniowanych dla `Model` i `TopSpeed` właściwości.)  
  
3. Po wygenerowaniu nowego Konstruktora faliste podkreślenie pojawia się w obszarze wywołanie konstruktora domyślnego w `DefaultAutomobileIsInitializedCorrectly`. Komunikat o błędzie stwierdzający, że `Automobile` klasa nie ma konstruktora przyjmującego zero argumentów. Aby wygenerować Konstruktor jawne Tworzenie domyślnych, który nie ma parametrów, kliknij tag inteligentny, a następnie kliknij przycisk **Generuj Konstruktor wycinka**.  
  
### <a name="to-generate-a-stub-for-a-method"></a>Można wygenerować klasy zastępczej dla metody  
  
1. Przyjęto założenie, specyfikacja stwierdza, że nowy `Automobile` można umieścić w stan uruchomienia, jeśli jego `Model` i `TopSpeed` właściwości są ustawione na coś innego niż wartości domyślne. Dodaj następujące wiersze do `AutomobileWithModelNameCanStart` metody.  
  
     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]  
  
2. Kliknij tag inteligentny dla `myAuto.Start` wywołania metody, a następnie kliknij przycisk **generowania szkieletu metody**.  
  
3. Kliknij tag inteligentny dla `IsRunning` właściwości, a następnie kliknij przycisk **generowania szkieletu właściwości**. `Automobile` Klasy zawiera teraz następujący kod.  
  
     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]  
  
### <a name="to-run-the-tests"></a>Aby uruchomić testy  
  
1. Na **testu jednostkowego** menu wskaż **uruchomić testy jednostkowe**, a następnie kliknij przycisk **wszystkie testy**. To polecenie uruchamia wszystkie testy w wszystkich środowisk testowych, które zostały napisane dla bieżącego rozwiązania.  
  
     W tym przypadku istnieją dwie próby, a nie ich obu, zgodnie z oczekiwaniami. `DefaultAutomobileIsInitializedCorrectly` Test zakończy się niepowodzeniem, ponieważ `Assert.IsTrue` warunku zwraca `False`. `AutomobileWithModelNameCanStart` Test zakończy się niepowodzeniem, ponieważ `Start` method in Class metoda `Automobile` klasy zgłasza wyjątek.  
  
     **Wyniki testu** na poniższej ilustracji przedstawiono okno.  
  
     ![Wyniki testu, który uległ awarii](../ide/media/testsfailed.png "TestsFailed")  
Wyniki testów - Okno  
  
2. W **wyników testu** okna, kliknij dwukrotnie pozycję w każdym wierszu wyniku testu, aby przejść do lokalizacji każdego niepowodzenia testu.  
  
### <a name="to-implement-the-source-code"></a>Aby zaimplementować kod źródłowy  
  
1. Dodaj następujący kod do konstruktora domyślnego tak, `Model`, `TopSpeed` i `IsRunning` właściwości są inicjowane na ich wartości domyślne poprawne `"Not specified"`, `-1`, i `True` (`true`).  
  
     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]  
  
2. Gdy `Start` metoda jest wywoływana, należy ją ustawić `IsRunning` flagi na wartość true tylko wtedy, gdy `Model` lub `TopSpeed` właściwości są ustawione na coś innego niż jego wartość domyślną. Usuń `NotImplementedException` z metody treści i Dodaj następujący kod.  
  
     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]  
  
### <a name="to-run-the-tests-again"></a>Aby ponownie uruchomić testy  
  
1. Na **testu** menu wskaż **Uruchom**, a następnie kliknij przycisk **wszystkie testy w rozwiązaniu**. Teraz kod przechodzi testy. **Wyniki testu** na poniższej ilustracji przedstawiono okno.  
  
     ![Wyniki testu, które przekazane](../ide/media/testspassed.png "TestsPassed")  
Wyniki testów - Okno  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie na podstawie użycia](../misc/generate-from-usage.md)   
 [Pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md)   
 [Za pomocą funkcji IntelliSense](../ide/using-intellisense.md)   
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)
