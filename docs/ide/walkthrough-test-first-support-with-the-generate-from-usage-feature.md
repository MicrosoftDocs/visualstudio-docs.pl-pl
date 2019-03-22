---
title: 'Przewodnik: Rozwoju pierwszego badania za pomocą funkcji generowania na podstawie sposobu użycia'
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d4862bc9d4dc43549a1b0d5050035dbb8dd407b
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355633"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Przewodnik: Rozwoju pierwszego badania za pomocą funkcji generowania na podstawie sposobu użycia

W tym temacie przedstawiono sposób użycia [Generowanie z użycia](../ide/visual-csharp-intellisense.md#generate-from-usage) funkcji, która obsługuje rozwoju pierwszego badania.

 *Rozwoju pierwszego badania* to podejście do projektowania oprogramowania, w której najpierw pisanie testów jednostkowych, w oparciu o specyfikacje produktów, a następnie napisać kod źródłowy, który jest wymagana do udostępnienia testów powiodło się. Program Visual Studio obsługuje rozwoju pierwszego badania, generując nowe typy i członkowie w kodzie źródłowym, gdy użytkownik najpierw odwołać je w przypadki testowe, zanim nie zostaną zdefiniowane.

 Program Visual Studio generuje nowe typy i elementy członkowskie z minimalną przerwą do przepływu pracy. Możesz utworzyć wycinków dla typów, metod, właściwości, pola lub konstruktory bez opuszczania Twojej bieżącej lokalizacji w kodzie. Gdy otworzysz okno dialogowe, aby określić opcje dla generowania typów, powrót natychmiast do bieżący plik otwarty po zamknięciu okna dialogowego.

 **Generowanie z użycia** funkcja może być używana przy użyciu środowisk testowych, które integrują się z programem Visual Studio. W tym temacie przedstawiono Frameworka testów jednostkowych firmy Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Utwórz projekt biblioteki klas Windows i Projekt testowy

1. W C# lub Visual Basic, Utwórz nową **biblioteki klas Windows** projektu. Nadaj mu nazwę `GFUDemo_VB` lub `GFUDemo_CS`, w zależności od języka, których używasz.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy ikonę rozwiązanie u góry, wybierz pozycję **Dodaj** > **nowy projekt**.

3. Utwórz nową **projekt testów jednostkowych (.NET Framework)** projektu.

   ::: moniker range="vs-2017"

   Poniższa ilustracja przedstawia **nowy projekt** okno dialogowe C# szablonów.

   ![Szablon projektu testu jednostki](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Dodaj odwołanie do projektu biblioteki klas

1.  W **Eksploratora rozwiązań**, w obszarze jednostkowy projekt testowy, kliknij prawym przyciskiem myszy **odwołania** wejścia i wybierz polecenie **Dodaj odwołanie**.

2.  W **Menadżer odwołań** okno dialogowe, wybierz opcję **projektów** a następnie wybierz projekt biblioteki klas.

3.  Wybierz **OK** zamknąć **Menadżer odwołań** okno dialogowe.

4.  Zapisz swoje rozwiązanie. Teraz można przystąpić do rozpoczęcia pisania testów.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generuj nową klasę z testu jednostkowego

1. Projekt testowy zawiera plik o nazwie *UnitTest1*. Kliknij dwukrotnie ten plik w **Eksploratora rozwiązań** aby otworzyć go w edytorze kodu. Zostały wygenerowane klasy testowej i metody testowej.

2. Znajdź w deklaracji klasy `UnitTest1` i zmień jej nazwę na `AutomobileTest`.

   > [!NOTE]
   >  Technologia IntelliSense zawiera teraz dwa warianty dla instrukcji IntelliSense: *trybem uzupełniania* i *trybem sugestii*. Tryb sugestii w sytuacjach, w których klas i składowych są wykorzystywane przed są zdefiniowane. Gdy **IntelliSense** jest otwarte okno, możesz nacisnąć przycisk **Ctrl**+**Alt**+**miejsca** się przełączać między trybem uzupełniania a trybem sugestii. Zobacz [IntelliSense użyj](../ide/using-intellisense.md) Aby uzyskać więcej informacji. Tryb sugestii pomoże podczas wpisywania `Automobile` w następnym kroku.

3. Znajdź `TestMethod1()` metody i zmień jej nazwę na `DefaultAutomobileIsInitializedCorrectly()`. Tej metody, Utwórz nowe wystąpienie klasy o nazwie `Automobile`, jak pokazano na poniższych zrzutach ekranu. Pojawi się linią falistą, co oznacza błąd w czasie kompilacji i [szybkie akcje](../ide/quick-actions.md) żarówki błąd pojawia się na lewym marginesie, lub bezpośrednio pod wężyk po umieszczeniu wskaźnika myszy nad nim.

    ![Szybkie akcje w języku Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Szybkie akcje w języku C&#35;](../ide/media/genclass_underline.png)

4. Wybierz lub kliknij przycisk **szybkie akcje** żarówki. Zobaczysz komunikat o błędzie stwierdzający, że typ `Automobile` nie został zdefiniowany. Zostanie również wyświetlony niektóre rozwiązania.

5. Kliknij przycisk **Generuj nowy typ** otworzyć **Generowanie typu** okno dialogowe. To okno dialogowe zawiera opcje, takie jak Generowanie typu z innego projektu.

6. W **projektu** kliknij **GFUDemo\_VB** lub **GFUDemo_CS** można poinstruować Visual Studio, aby dodać plik do projektu biblioteki klas, zamiast testu Projekt. Jeśli nie została jeszcze wybrana, wybierz opcję **Utwórz nowy plik** i nadaj mu nazwę *Automobile.cs* lub *Automobile.vb*.

     ![Generuj nowy typ, okno dialogowe](../ide/media/genotherdialog.png)

7. Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć nowy plik.

8. W **Eksploratora rozwiązań**, sprawdź w obszarze **GFUDemo_VB** lub **GFUDemo_CS** węzeł projektu, aby sprawdzić, czy nowy *Automobile.vb* lub  *Automobile.cs* pliku ma. W edytorze kodu fokus nadal znajduje się w `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, co umożliwia Napisz test z co najmniej przeszkód w dalszym ciągu.

### <a name="generate-a-property-stub"></a>Generowania szkieletu właściwości
Przyjęto założenie, opis produktu stanowi, że `Automobile` klasa ma dwie właściwości publiczne, o nazwie `Model` i `TopSpeed`. Te właściwości musi zostać zainicjowany z wartościami domyślnymi `"Not specified"` i `-1` przez konstruktora domyślnego. Następujący test jednostkowy sprawdzi, czy domyślny konstruktor ustawia właściwości do wartości domyślnych poprawne.

1. Dodaj następujący wiersz kodu w celu `DefaultAutomobileIsInitializedCorrectly` metoda testowa.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Ponieważ kod odwołuje się do dwóch niezdefiniowanymi właściwościami na `Automobile`, falistą linią pojawia się w obszarze `Model` i `TopSpeed`. Umieść kursor nad `Model` i wybierz polecenie **szybkie akcje** błąd żarówka, a następnie wybierz **Generuj właściwość "Automobile.Model"**.

3. Generowania szkieletu właściwości dla `TopSpeed` właściwości w taki sam sposób.

     W `Automobile` klasy, typy nowe właściwości poprawnie są dedukowane z kontekstu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Wygenerować klasy zastępczej dla nowego Konstruktora
Teraz utworzymy metody testowej, który wygeneruje odcinek konstruktora, aby zainicjować `Model` i `TopSpeed` właściwości. Później dodasz więcej kodu, aby ukończyć test.

1. Dodaj następującą metodę dodatkowy test, aby Twoje `AutomobileTest` klasy.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2.  Kliknij przycisk **szybkie akcje** żarówka w obszarze czerwona fala błąd, a następnie kliknij przycisk **Generowanie konstruktora w "Samochód"**.

     W `Automobile` klasy pliku, zwróć uwagę, że nowy konstruktor ma zbadać nazwy zmiennych lokalnych, które są używane w wywołaniu konstruktora, podczas gdy znaleziono właściwości, które mają takie same nazwy w `Automobile` klasy i podany kod w treści konstruktora, celu przechowywanie wartości argumentu w `Model` i `TopSpeed` właściwości.


3.  Po wygenerowaniu nowego Konstruktora faliste podkreślenie pojawia się w obszarze wywołanie konstruktora domyślnego w `DefaultAutomobileIsInitializedCorrectly`. Komunikat o błędzie stwierdzający, że `Automobile` klasa nie ma konstruktora przyjmującego zero argumentów. Aby wygenerować Konstruktor jawne Tworzenie domyślnych, który nie ma parametrów, kliknij przycisk **szybkie akcje** błąd żarówki, a następnie kliknij **Generowanie konstruktora w "Samochód"**.

### <a name="generate-a-stub-for-a-method"></a>Wygenerować klasy zastępczej dla metody
Przyjęto założenie, specyfikacja stwierdza, że nowy `Automobile` można umieścić w `IsRunning` stanie, jeśli jego `Model` i `TopSpeed` właściwości są ustawione na coś innego niż wartości domyślne.

1. Dodaj następujące wiersze do `AutomobileWithModelNameCanStart` metody.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2.  Kliknij przycisk **szybkie akcje** żarówki błąd dla `myAuto.Start` wywołania metody, a następnie kliknij przycisk **Generuj metodę "Automobile.Start"**.

3.  Kliknij przycisk **szybkie akcje** żarówki dla `IsRunning` właściwości, a następnie kliknij przycisk **Generuj właściwość "Automobile.IsRunning"**.

     `Automobile` Klasa teraz zawiera metodę o nazwie `Start()` i właściwość o nazwie `IsRunning`.

### <a name="run-the-tests"></a>Uruchom testy

1.  Na **testu** menu, wybierz **Uruchom** > **wszystkie testy**.

     **Uruchom** > **wszystkie testy** polecenie uruchamia wszystkie testy w dowolnym platform testów, które zostały napisane dla bieżącego rozwiązania. W tym przypadku istnieją dwie próby, a nie ich obu, zgodnie z oczekiwaniami. `DefaultAutomobileIsInitializedCorrectly` Test zakończy się niepowodzeniem, ponieważ `Assert.IsTrue` warunku zwraca `False`. `AutomobileWithModelNameCanStart` Test zakończy się niepowodzeniem, ponieważ `Start` method in Class metoda `Automobile` klasy zgłasza wyjątek.

     **Wyniki testu** na poniższej ilustracji przedstawiono okno.

     ![Wyniki testów, które nie powiodło się](../ide/media/testsfailed.png)

2.  W **wyników testu** okna, kliknij dwukrotnie pozycję w każdym wierszu wyniku testu, aby przejść do lokalizacji każdego testu.

### <a name="implement-the-source-code"></a>Zaimplementuj kod źródłowy

1.  Dodaj następujący kod do konstruktora domyślnego tak, `Model`, `TopSpeed` i `IsRunning` właściwości są inicjowane na ich wartości domyślne poprawne `"Not specified"`, `-1`, i `False` (lub `false` Aby uzyskać C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2.  Gdy `Start` metoda jest wywoływana, należy ją ustawić `IsRunning` flagi na wartość true tylko wtedy, gdy `Model` lub `TopSpeed` właściwości są ustawione na coś innego niż jego wartość domyślną. Usuń `NotImplementedException` z metody treści i Dodaj następujący kod.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Uruchom ponownie testy

- Na **testu** menu wskaż **Uruchom**, a następnie kliknij przycisk **wszystkie testy**.

     Teraz kod przechodzi testy. **Wyniki testu** na poniższej ilustracji przedstawiono okno.

     ![Wyniki testów, które są przekazywane](../ide/media/testspassed.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie na podstawie użycia](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Szybkie akcje](../ide/quick-actions.md)