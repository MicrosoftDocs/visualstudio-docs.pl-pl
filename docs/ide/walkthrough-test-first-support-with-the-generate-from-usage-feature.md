---
title: Programowy testowy z funkcją Generuj z użycia
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bf9a7e613a482167a01739320282f9ba8fdea26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596895"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Instruktaż: Program rozwoju najpierw testowy z funkcją Generowanie z użycia

W tym temacie pokazano, jak używać funkcji [Generuj z użycia,](../ide/visual-csharp-intellisense.md#generate-from-usage) która obsługuje programowy testowy.

 *Program rozwoju najpierw test* jest podejście do projektowania oprogramowania, w którym najpierw napisać testy jednostkowe na podstawie specyfikacji produktu, a następnie napisać kod źródłowy, który jest wymagany do testów zakończyć się pomyślnie. Visual Studio obsługuje program rozwoju test-first przez generowanie nowych typów i elementów członkowskich w kodzie źródłowym, gdy po raz pierwszy odwoływać się do nich w przypadkach testowych, zanim zostaną zdefiniowane.

Visual Studio generuje nowe typy i członków z minimalnym przerwanie przepływu pracy. Można tworzyć wycinki dla typów, metod, właściwości, pól lub konstruktorów bez opuszczania bieżącej lokalizacji w kodzie. Po otwarciu okna dialogowego w celu określenia opcji generowania typów fokus powraca natychmiast do bieżącego otwartego pliku po zamknięciu okna dialogowego.

Funkcja **Generuj z użycia** może służyć z platformami testowymi, które integrują się z programem Visual Studio. W tym temacie zostanie zademonstrowana struktura testowania jednostek firmy Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Tworzenie projektu biblioteki klas systemu Windows i projektu testowego

1. W języku C# lub Visual Basic utwórz nowy projekt **biblioteki klas systemu Windows.** Nazwij go `GFUDemo_VB` lub `GFUDemo_CS`, w zależności od języka, którego używasz.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy ikonę rozwiązania u góry, wybierz polecenie **Dodaj** > **nowy projekt**.

3. Utwórz nowy projekt **testu jednostkowego (.NET Framework).**

   ::: moniker range="vs-2017"

   Na poniższej ilustracji przedstawiono okno dialogowe **Nowy projekt** dla szablonów języka C#.

   ![Szablon projektu testu jednostkowego](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Dodawanie odwołania do projektu Biblioteki klas

1. W **Eksploratorze rozwiązań**w obszarze projektu testu jednostkowego kliknij prawym przyciskiem myszy wpis **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **Projekty,** a następnie wybierz projekt biblioteki klas.

3. Wybierz **przycisk OK,** aby zamknąć okno dialogowe **Menedżer odwołań.**

4. Zapisz swoje rozwiązanie. Teraz możesz rozpocząć pisanie testów.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generowanie nowej klasy z testu jednostkowego

1. Projekt testowy zawiera plik o nazwie *UnitTest1*. Kliknij dwukrotnie ten plik w **Eksploratorze rozwiązań,** aby otworzyć go w edytorze kodu. Klasa testu i metoda badania zostały wygenerowane.

2. Znajdź deklarację `UnitTest1` dla klasy i `AutomobileTest`zmień jej nazwę na .

   > [!NOTE]
   > IntelliSense zapewnia teraz dwie alternatywy dla ukończenia instrukcji IntelliSense: *tryb ukończenia* i *tryb sugestii.* Użyj trybu sugestii dla sytuacji, w których klasy i elementy członkowskie są używane przed ich zdefiniowaniem. Po otwarciu okna **IntelliSense** można nacisnąć klawisz **Ctrl**+**Alt**+**Space,** aby przełączyć tryb ukończenia i tryb sugestii. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu IntelliSense.](../ide/using-intellisense.md) Tryb sugestii pomoże podczas `Automobile` pisania w następnym kroku.

3. Znajdź `TestMethod1()` metodę i zmień `DefaultAutomobileIsInitializedCorrectly()`jej nazwę na . Wewnątrz tej metody należy utworzyć nowe `Automobile`wystąpienie klasy o nazwie , jak pokazano na poniższych zrzutach ekranu. Pojawi się faliste podkreślenie, które wskazuje błąd w czasie kompilacji, a żarówka błędu [Szybkie akcje](../ide/quick-actions.md) pojawia się na lewym marginesie lub bezpośrednio pod falistym polem po umieszczeniu nad nim wskaźnika.

    ![Szybkie akcje w języku Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Szybkie akcje w&#35; C](../ide/media/genclass_underline.png)

4. Wybierz lub kliknij żarówkę **Szybkie akcje.** Zostanie wyświetlony komunikat o błędzie informujący, że typ `Automobile` nie jest zdefiniowany. Są również przedstawione z niektórych rozwiązań.

5. Kliknij **pozycję Generuj nowy typ,** aby otworzyć okno dialogowe **Generowanie typu.** To okno dialogowe zawiera opcje, które obejmują generowanie typu w innym projekcie.

6. Na liście **Projekt** kliknij **GFUDemo\_VB** lub **GFUDemo_CS,** aby poinstruować program Visual Studio, aby dodać plik do projektu biblioteki klas zamiast projektu testowego. Jeśli nie jest jeszcze zaznaczona, wybierz pozycję **Utwórz nowy plik** i nazwij go *Automobile.cs* lub *Automobile.vb*.

     ![Okno dialogowe Generowanie nowego typu](../ide/media/genotherdialog.png)

7. Kliknij **przycisk OK,** aby zamknąć okno dialogowe i utworzyć nowy plik.

8. W **Eksploratorze rozwiązań**poszukaj **w GFUDemo_VB** lub **GFUDemo_CS** węzła projektu, aby sprawdzić, czy istnieje nowy plik *Automobile.vb* lub *Automobile.cs.* W edytorze kodu fokus `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`jest nadal w , co pozwala na kontynuowanie pisania testu z minimalną przerwą.

### <a name="generate-a-property-stub"></a>Generowanie skrótu właściwości
Załóżmy, że specyfikacja produktu stwierdza, że `Automobile` klasa ma dwie właściwości publiczne o nazwie `Model` i `TopSpeed`. Te właściwości muszą być inicjowane z wartościami domyślnymi `"Not specified"` i `-1` przez domyślny konstruktor. Następujący test jednostkowy sprawdzi, czy domyślny konstruktor ustawia właściwości na ich poprawne wartości domyślne.

1. Dodaj następujący wiersz kodu `DefaultAutomobileIsInitializedCorrectly` do metody testowej.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Ponieważ kod odwołuje się do dwóch niezdefiniowanych właściwości `Automobile`na `Model` `TopSpeed`, faliste podkreślenie pojawia się w obszarze i . Najedź kursorem `Model` na i wybierz żarówkę błędu **Szybkie akcje,** a następnie wybierz polecenie **Wygeneruj właściwość "Automobile.Model"**.

3. Generowanie skrótu `TopSpeed` właściwości dla właściwości w ten sam sposób.

     W `Automobile` klasie typy nowych właściwości są poprawnie wywnioskowane z kontekstu.

### <a name="generate-a-stub-for-a-new-constructor"></a>Generowanie skrótu dla nowego konstruktora
Teraz utworzymy metodę testową, która wygeneruje `Model` skrót `TopSpeed` konstruktora, aby zainicjować i właściwości. Później dodasz więcej kodu, aby ukończyć test.

1. Dodaj następującą dodatkową metodę `AutomobileTest` testu do swojej klasy.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. Kliknij żarówkę błędu **Szybkie akcje** pod czerwoną falitwą, a następnie kliknij pozycję **Generuj konstruktora w "Samochodzie"**.

     W `Automobile` pliku klasy należy zauważyć, że nowy konstruktor zbadał nazwy zmiennych lokalnych, które są używane w wywołaniu `Automobile` konstruktora, znaleziono właściwości, które mają takie `Model` `TopSpeed` same nazwy w klasie i podana kod w treści konstruktora do przechowywania wartości argumentów w i właściwości.

3. Po wygenerowaniu nowego konstruktora podkreślenie faliste pojawia się `DefaultAutomobileIsInitializedCorrectly`pod wywołaniem domyślnego konstruktora w pliku . Komunikat o błędzie `Automobile` stwierdza, że klasa nie ma konstruktora, który przyjmuje zero argumentów. Aby wygenerować jawny domyślny konstruktor, który nie ma parametrów, kliknij żarówkę błędu **Szybkie akcje,** a następnie kliknij pozycję **Generuj konstruktor w polu "Samochód"**.

### <a name="generate-a-stub-for-a-method"></a>Generowanie skrótu dla metody
Załóżmy, że specyfikacja stwierdza, `Automobile` że nowy może być wprowadzony do `IsRunning` stanu, jeśli jego `Model` i `TopSpeed` właściwości są ustawione na coś innego niż wartości domyślne.

1. Dodaj następujące wiersze `AutomobileWithModelNameCanStart` do metody.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. Kliknij żarówkę błędu Szybkie `myAuto.Start` **akcje** dla wywołania metody, a następnie kliknij pozycję **Generuj metodę "Automobil.Start"**.

3. Kliknij żarówkę **Szybkie** `IsRunning` akcje dla właściwości, a następnie kliknij pozycję **Generuj właściwość "Automobile.IsRunning"**.

     Klasa `Automobile` zawiera teraz metodę `Start()` o nazwie `IsRunning`i właściwość o nazwie .

### <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **Test** wybierz polecenie **Uruchom** > **wszystkie testy**.

     Polecenie **Uruchom** > **wszystkie testy** uruchamia wszystkie testy w dowolnej ramach testów, które są zapisywane dla bieżącego rozwiązania. W tym przypadku istnieją dwa testy i oba nie, zgodnie z oczekiwaniami. Test `DefaultAutomobileIsInitializedCorrectly` zakończy się `Assert.IsTrue` niepowodzeniem, ponieważ warunek zwraca `False`. Test `AutomobileWithModelNameCanStart` kończy się `Start` niepowodzeniem, ponieważ metoda w `Automobile` klasie zgłasza wyjątek.

     Okno **Wyniki testu** jest pokazane na poniższej ilustracji.

     ![Wyniki testów, które nie powiodły się](../ide/media/testsfailed.png)

2. W oknie **Wyniki testu** kliknij dwukrotnie każdy wiersz wyników testu, aby przejść do lokalizacji każdego testu.

### <a name="implement-the-source-code"></a>Implementowanie kodu źródłowego

1. Dodaj następujący kod do konstruktora `Model` `TopSpeed` domyślnego, tak aby `IsRunning` wszystkie właściwości i `"Not specified"` `-1`właściwości `False` zostały `false` zainicjowane do poprawnych wartości domyślnych , i (lub dla języka C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. Gdy `Start` metoda jest wywoływana, `IsRunning` należy ustawić flagę `Model` `TopSpeed` true tylko wtedy, gdy lub właściwości są ustawione na coś innego niż ich wartość domyślna. Usuń `NotImplementedException` z treści metody i dodaj następujący kod.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Ponowne uruchomienie testów

- W menu **Test** wskaż polecenie **Uruchom**, a następnie kliknij polecenie **Wszystkie testy**.

     Tym razem testy zdają. Okno **Wyniki testu** jest pokazane na poniższej ilustracji.

     ![Wyniki testów, które przeszły](../ide/media/testspassed.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie z użycia](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
- [Szybkie akcje](../ide/quick-actions.md)
