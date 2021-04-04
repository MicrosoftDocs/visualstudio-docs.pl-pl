---
title: Testowanie pierwszego środowiska przy użyciu generowania na podstawie użycia
description: Dowiedz się, jak włączyć podejście do programowania w pierwszej kolejności, korzystając z funkcji generowania z użycia.
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a1f115dfff92b1c5e5979e62af257cde6a92360
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216595"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Przewodnik: testowanie pierwszego środowiska przy użyciu funkcji generowania na podstawie użycia

W tym temacie pokazano, jak używać funkcji [Generuj z użycia](../ide/visual-csharp-intellisense.md#generate-from-usage) , która obsługuje programowanie po raz pierwszy.

 *Programowanie w pierwszej kolejności* jest podejściem do projektowania oprogramowania, w którym najpierw można napisać testy jednostkowe na podstawie specyfikacji produktu, a następnie napisać kod źródłowy, który jest wymagany do pomyślnego wykonania testów. Program Visual Studio obsługuje testy w pierwszej kolejności, generując nowe typy i elementy członkowskie w kodzie źródłowym podczas pierwszego odwoływania się do nich w przypadkach testowych, zanim zostaną zdefiniowane.

Program Visual Studio generuje nowe typy i elementy członkowskie z minimalnymi przerwami w przepływie pracy. Można tworzyć wycinki dla typów, metod, właściwości, pól lub konstruktorów bez opuszczania bieżącej lokalizacji w kodzie. Po otwarciu okna dialogowego, aby określić opcje generowania typów, fokus wraca natychmiast do bieżącego otwartego pliku po zamknięciu okna dialogowego.

Funkcja **generowania z użycia** może być używana z platformami testów, które integrują się z programem Visual Studio. W tym temacie przedstawiono strukturę testowania jednostkowego firmy Microsoft.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Tworzenie projektu biblioteki klas systemu Windows i projektu testowego

1. W języku C# lub Visual Basic Utwórz nowy projekt **biblioteki klas systemu Windows** . Nadaj mu nazwę `GFUDemo_VB` lub `GFUDemo_CS` , w zależności od języka, którego używasz.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy ikonę rozwiązania u góry, a następnie wybierz polecenie **Dodaj**  >  **Nowy projekt**.

3. Utwórz nowy projekt **testu jednostkowego (.NET Framework)** .

   ::: moniker range="vs-2017"

   Na poniższej ilustracji przedstawiono okno dialogowe **Nowy projekt** dla szablonów języka C#.

   ![Szablon projektu testów jednostkowych](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Dodaj odwołanie do projektu biblioteki klas

1. W **Eksplorator rozwiązań**, w ramach projektu testów jednostkowych, kliknij prawym przyciskiem myszy wpis **odwołania** i wybierz polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **projekty** , a następnie wybierz projekt Biblioteka klas.

3. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Menedżer odwołań** .

4. Zapisz rozwiązanie. Teraz możesz zacząć pisać testy.

### <a name="generate-a-new-class-from-a-unit-test"></a>Generowanie nowej klasy na podstawie testu jednostkowego

1. Projekt testowy zawiera plik o nazwie *UnitTest1*. Kliknij dwukrotnie ten plik w **Eksplorator rozwiązań** , aby otworzyć go w edytorze kodu. Wygenerowano klasę testową i metodę testową.

2. Znajdź deklarację klasy `UnitTest1` i zmień jej nazwę na `AutomobileTest` .

   > [!NOTE]
   > Technologia IntelliSense oferuje teraz dwa alternatywy dla uzupełniania instrukcji IntelliSense: *Tryb uzupełniania* i *tryb sugestii*. Tryb sugestii służy do sytuacji, w których klasy i składowe są używane przed zdefiniowaniem. Gdy okno **IntelliSense** jest otwarte, możesz nacisnąć **klawisze CTRL**, +  +  aby przełączać się między trybem ukończenia i trybem sugestii. Aby uzyskać więcej informacji, zobacz [Używanie technologii IntelliSense](../ide/using-intellisense.md) . Tryb sugestii ułatwia wprowadzanie tekstu `Automobile` w następnym kroku.

3. Znajdź `TestMethod1()` metodę i zmień jej nazwę na `DefaultAutomobileIsInitializedCorrectly()` . Wewnątrz tej metody Utwórz nowe wystąpienie klasy o nazwie `Automobile` , jak pokazano na poniższych zrzutach ekranu. Zostanie wyświetlone faliste podkreślenie, które wskazuje na błąd w czasie kompilacji, a żarówka błędu [szybkie akcje](../ide/quick-actions.md) pojawia się na lewym marginesie lub bezpośrednio poniżej, gdy umieścisz na niej wskaźnik myszy.

    ![Szybkie akcje w Visual Basic](../ide/media/genclass_underlinevb.png)

    ![Szybkie akcje w języku C&#35;](../ide/media/genclass_underline.png)

4. Wybierz lub kliknij żarówkę **szybkie akcje** . Zobaczysz komunikat o błędzie z informacją, że typ `Automobile` nie jest zdefiniowany. Dostępne są również rozwiązania.

5. Kliknij przycisk **Generuj nowy typ** , aby otworzyć okno dialogowe **generowanie typu** . To okno dialogowe zawiera opcje, które obejmują generowanie typu w innym projekcie.

6. Na liście **projekt** kliknij pozycję **GFUDemo \_ VB** lub **GFUDemo_CS** , aby nakazać programowi Visual Studio dodanie pliku do projektu biblioteki klas zamiast projektu testowego. Jeśli nie została jeszcze wybrana, wybierz pozycję **Utwórz nowy plik** i nadaj jej nazwę *automobile. cs* lub *automobile. vb*.

     ![Okno dialogowe generowanie nowego typu](../ide/media/genotherdialog.png)

7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe i utworzyć nowy plik.

8. W **Eksplorator rozwiązań**, poszukaj w węźle projektu **GFUDemo_VB** lub **GFUDemo_CS** , aby sprawdzić, czy nowy plik *automobile. vb* lub *automobile. cs* znajduje się w tym miejscu. W edytorze kodu fokus jest nadal w `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` , co umożliwia dalsze pisanie testu z minimalnym przerwaniem.

### <a name="generate-a-property-stub"></a>Generowanie właściwości zastępczej
Załóżmy, że Specyfikacja produktu wskazuje, że `Automobile` Klasa ma dwie właściwości publiczne o nazwie `Model` i `TopSpeed` . Te właściwości muszą zostać zainicjowane przy użyciu wartości domyślnych `"Not specified"` i `-1` przez konstruktora domyślnego. Poniższy test jednostkowy sprawdzi, czy domyślny Konstruktor ustawi odpowiednie wartości domyślne.

1. Dodaj następujący wiersz kodu do `DefaultAutomobileIsInitializedCorrectly` metody testowej.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet1":::

2. Ponieważ kod odwołuje się do dwóch niezdefiniowanych właściwości w `Automobile` , w obszarze `Model` i `TopSpeed` . Zatrzymaj wskaźnik myszy `Model` i wybierz żarówkę błędu **szybkie akcje** , a następnie wybierz polecenie **Generuj Właściwość "Automobile. model"**.

3. Wygeneruj Właściwość zastępczą dla `TopSpeed` właściwości w ten sam sposób.

     W `Automobile` klasie typy nowych właściwości są prawidłowo wnioskowane w kontekście.

### <a name="generate-a-stub-for-a-new-constructor"></a>Generuj element zastępczy dla nowego Konstruktora
Teraz utworzysz metodę testową, która spowoduje wygenerowanie klasy zastępczej konstruktora w celu zainicjowania `Model` `TopSpeed` właściwości i. Później dodasz więcej kodu do ukończenia testu.

1. Dodaj następującą dodatkową metodę testową do `AutomobileTest` klasy.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb" id="Snippet2":::

2. Kliknij żarówkę błędu **szybkie akcje** w czerwonej części, a następnie kliknij pozycję **Generuj Konstruktor w "Automobile"**.

     W `Automobile` pliku klasy należy zauważyć, że nowy Konstruktor zbadał nazwy zmiennych lokalnych, które są używane w wywołaniu konstruktora, znaleziono właściwości, które mają takie same nazwy w `Automobile` klasie, i dostarczony kod w treści konstruktora do przechowywania wartości argumentów we `Model` `TopSpeed` właściwościach i.

3. Po wygenerowaniu nowego konstruktora faliste podkreślenie pojawia się pod wywołaniem konstruktora domyślnego w `DefaultAutomobileIsInitializedCorrectly` . Komunikat o błędzie stwierdza, że `Automobile` Klasa nie ma konstruktora, który przyjmuje zero argumentów. Aby wygenerować jawny Konstruktor domyślny, który nie ma parametrów, kliknij żarówkę błędu **szybkie akcje** , a następnie kliknij pozycję **Generuj Konstruktor w elemencie "samochód Mobile"**.

### <a name="generate-a-stub-for-a-method"></a>Generowanie klasy zastępczej dla metody
Przyjęto założenie, że Specyfikacja wskazuje, że nowy `Automobile` może być umieszczony w `IsRunning` stanie, jeśli jego `Model` `TopSpeed` właściwości i są ustawione na wartość inną niż wartości domyślne.

1. Dodaj następujące wiersze do `AutomobileWithModelNameCanStart` metody.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet3":::

2. Kliknij żarówkę błędu **szybkie akcje** dla `myAuto.Start` wywołania metody, a następnie kliknij pozycję **Generuj metodę "Automobile. Start"**.

3. Kliknij żarówkę **Quick Actions** dla `IsRunning` właściwości, a następnie kliknij pozycję **Generate Property "Automobile. isrunningd"**.

     `Automobile`Klasa zawiera teraz metodę o nazwie `Start()` i właściwość o nazwie `IsRunning` .

### <a name="run-the-tests"></a>Uruchamianie testów

1. W menu **test** wybierz polecenie **Uruchom**  >  **wszystkie testy**.

     Polecenie **Uruchom**  >  **wszystkie testy** uruchamia wszystkie testy w ramach wszystkich platform testowych, które są zapisywane dla bieżącego rozwiązania. W takim przypadku istnieją dwa testy i w oczekiwany sposób kończą się niepowodzeniem. `DefaultAutomobileIsInitializedCorrectly`Test zakończy się niepowodzeniem, ponieważ `Assert.IsTrue` zwraca warunek `False` . `AutomobileWithModelNameCanStart`Test nie powiódł się, ponieważ `Start` Metoda w `Automobile` klasie zgłasza wyjątek.

     Okno **wyniki testów** jest pokazane na poniższej ilustracji.

     ![Wyniki testu, które zakończyły się niepowodzeniem](../ide/media/testsfailed.png)

2. W oknie **wyniki testów** kliknij dwukrotnie każdy wiersz wyniku testu, aby przejść do lokalizacji każdego testu.

### <a name="implement-the-source-code"></a>Zaimplementuj kod źródłowy

1. Dodaj następujący kod do konstruktora domyślnego, aby `Model` `TopSpeed` `IsRunning` wszystkie właściwości i wszystkie były zainicjowane do ich prawidłowych wartości domyślnych `"Not specified"` , `-1` , i `False` (lub `false` dla języka C#).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet5":::

2. Gdy `Start` Metoda jest wywoływana, należy ustawić `IsRunning` flagę na wartość true tylko wtedy, gdy `Model` `TopSpeed` właściwości lub są ustawione na inną niż wartość domyślna. Usuń `NotImplementedException` z treści metody i Dodaj następujący kod.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet6":::

### <a name="run-the-tests-again"></a>Uruchom testy ponownie

- W menu **test** wskaż polecenie **Uruchom**, a następnie kliknij pozycję **wszystkie testy**.

     Ta godzina przebiegu testów. Okno **wyniki testów** jest pokazane na poniższej ilustracji.

     ![Wyniki testów, które zostały zakończone](../ide/media/testspassed.png)

## <a name="see-also"></a>Zobacz też

- [Generuj na podstawie użycia](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Szybkie akcje](../ide/quick-actions.md)
