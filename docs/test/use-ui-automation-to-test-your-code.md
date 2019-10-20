---
title: Kodowane testy interfejsu użytkownika
ms.date: 12/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a6491a6b9ac9312befbf0c8c6c3fb0f293885ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659865"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Używanie kodowanego testu interfejsu użytkownika do testowania kodu

Kodowane testy interfejsu użytkownika (CUITs) są dyskami aplikacji za poorednictwem interfejsu użytkownika. Te testy obejmują Testowanie funkcjonalne formantów interfejsu użytkownika. Umożliwiają one sprawdzenie, czy cała aplikacja, w tym jej interfejs użytkownika, działa poprawnie. Kodowane testy interfejsu użytkownika są przydatne w przypadku, gdy na stronie sieci Web występuje Walidacja lub inna logika. Są one również często używane do automatyzowania istniejącego testu ręcznego.

Tworzenie kodowanego testu interfejsu użytkownika w programie Visual Studio jest proste. Po prostu wykonujesz test ręcznie, gdy **Konstruktor kodowanego testu interfejsu użytkownika** działa w tle. Możesz również określić, jakie wartości powinny być wyświetlane w określonych polach. **Konstruktor kodowanego testu interfejsu użytkownika** rejestruje akcje i generuje z nich kod. Po utworzeniu testu można go edytować w wyspecjalizowanym edytorze, który pozwala modyfikować sekwencję akcji.

Wyspecjalizowany **Konstruktor kodowanego testu interfejsu użytkownika** i Edytor ułatwiają tworzenie i edytowanie kodowanych testów interfejsu użytkownika, nawet jeśli główne umiejętności są skoncentrowane na testowaniu zamiast kodowania. Ale jeśli jesteś deweloperem i chcesz przetworzyć test w bardziej zaawansowany sposób, kod jest strukturalny, dzięki czemu będzie on prosty do kopiowania i dostosowywania. Na przykład możesz zarejestrować test, aby kupić coś w witrynie sieci Web, a następnie edytować wygenerowany kod, aby dodać pętlę, która kupuje wiele elementów.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Wymagania

- Visual Studio Enterprise
- Składnik kodowanego testu interfejsu użytkownika

Aby uzyskać więcej informacji o tym, które platformy i konfiguracje są obsługiwane przez kodowane testy interfejsu użytkownika, zobacz [obsługiwane platformy](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Zainstaluj składnik kodowanego testu interfejsu użytkownika

Aby uzyskać dostęp do narzędzi i szablonów kodowanych testów interfejsu użytkownika, Zainstaluj składnik **kodowanego testu interfejsu użytkownika** programu Visual Studio.

1. Uruchom **Instalator programu Visual Studio** , wybierając pozycję **Narzędzia**  > **Pobierz narzędzia i funkcje**.

1. W **Instalator programu Visual Studio**wybierz kartę **poszczególne składniki** , a następnie przewiń w dół do sekcji **debugowanie i testowanie** . Wybierz składnik **kodowanego testu interfejsu użytkownika** .

   ![Składnik kodowanego testu interfejsu użytkownika](media/coded-ui-test-component.png)

1. Wybierz pozycję **Modyfikuj**.

## <a name="create-a-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika

1. Utwórz projekt kodowanego testu interfejsu użytkownika.

   Kodowane testy interfejsu użytkownika muszą być zawarte w projekcie kodowanego testu interfejsu użytkownika. Jeśli nie masz jeszcze projektu kodowanego testu interfejsu użytkownika, utwórz go. Wybierz pozycję **plik**  > **Nowy**  > **projekt**. Wyszukaj i wybierz szablon projektu **kodowanego testu interfejsu użytkownika** .

   ::: moniker range="vs-2017"

   ![Szablon projektu kodowanego testu interfejsu użytkownika w oknie dialogowym Nowy projekt](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli szablon **projektu kodowanego testu interfejsu użytkownika** nie jest widoczny, należy [zainstalować składnik KODOWANEGO testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Dodaj kodowany plik testu interfejsu użytkownika.

     Jeśli właśnie utworzono kodowany projekt interfejsu użytkownika, pierwszy plik CUIT jest dodawany automatycznie. Aby dodać inny plik testowy, otwórz menu skrótów dla projektu kodowanego testu interfejsu użytkownika w **Eksplorator rozwiązań**, a następnie wybierz **Dodaj**  > **kodowany test interfejsu użytkownika**.

     W oknie dialogowym **generowanie kodu dla kodowanego testu interfejsu użytkownika** wybierz pozycję **Rejestruj akcje**  > **Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia**.

     ![Okno dialogowe generowanie kodu dla kodowanego testu interfejsu użytkownika](media/generate-code-for-coded-ui-test.png)

     Zostanie wyświetlony **Konstruktor kodowanego testu interfejsu użytkownika** .

     ![Konstruktor kodowanego testu interfejsu użytkownika](../test/media/codedui_testbuilder.png)

3. Rejestruje sekwencję akcji.

     **Aby rozpocząć nagrywanie**, wybierz ikonę **rekordu** . Wykonaj czynności, które chcesz przetestować w aplikacji, w tym uruchamianie aplikacji, jeśli jest to wymagane. Na przykład jeśli testujesz aplikację sieci Web, możesz uruchomić przeglądarkę, przejdź do witryny sieci Web i zalogować się do aplikacji.

     **Aby wstrzymać nagrywanie**, na przykład w przypadku konieczności zajmowania się pocztą przychodzącą wybierz pozycję **Wstrzymaj**.

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do zarejestrowania poufnych danych.

     **Aby usunąć akcje** , które zostały zarejestrowane przez pomyłkę, wybierz polecenie **Edytuj kroki**.

     **Aby wygenerować kod** , który będzie replikować akcje, wybierz ikonę **Generuj kod** i wpisz nazwę i opis dla KODOWANEJ metody testowania interfejsu użytkownika.

4. Sprawdź wartości w polach interfejsu użytkownika, takich jak pola tekstowe.

     Wybierz pozycję **Dodaj potwierdzenia** w **konstruktorze KODOWANEGO testu interfejsu użytkownika**, a następnie wybierz kontrolkę interfejs użytkownika w działającej aplikacji. Na liście właściwości, które pojawiają się, wybierz właściwość, na przykład **tekst** w polu tekstowym. W menu skrótów wybierz polecenie **Dodaj potwierdzenie**. W oknie dialogowym wybierz operator porównania, wartość porównania i komunikat o błędzie.

     Zamknij okno potwierdzenia i wybierz polecenie **Generuj kod**.

     ![Element docelowy kodowanego testu interfejsu użytkownika](../test/media/codedui_1.png)

    > [!TIP]
    > Alternatywa między akcjami rejestrowania i weryfikowaniem wartości. Generuj kod na końcu każdej sekwencji akcji lub weryfikacji. Jeśli chcesz, będzie można później wstawiać nowe akcje i weryfikacje.

     Aby uzyskać więcej informacji, zobacz [Weryfikowanie właściwości kontrolek](#validate-the-properties-of-ui-controls).

5. Wyświetl wygenerowany kod testu.

     Aby wyświetlić wygenerowany kod, Zamknij okno Konstruktor testu interfejsu użytkownika. W kodzie można zobaczyć nazwy, które zostały nadaną do każdego kroku. Kod znajduje się w utworzonym pliku CUIT:

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          this.UIMap.VerifyResultValue();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.
      }
    }
    ```

6. Dodaj więcej akcji i potwierdzeń.

   Umieść kursor w odpowiednim punkcie w metodzie testowej, a następnie w menu skrótów wybierz polecenie **Generuj kod dla kodowanego testu interfejsu użytkownika**. Nowy kod zostanie wstawiony w tym momencie.

7. Edytuj szczegóły akcji testowych i potwierdzeń.

     Otwórz *UIMap. UITest*. Ten plik zostanie otwarty w **Edytorze kodowanego testu interfejsu użytkownika**, w którym można edytować dowolną sekwencję zarejestrowanych akcji, a także edytować potwierdzenia.

     ![Edytor kodowanego testu interfejsu użytkownika](../test/media/cuit_editor_edit.png)

     Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Uruchom test.

   Użyj Eksploratora testów lub Otwórz menu skrótów w metodzie testowej, a następnie wybierz polecenie **Uruchom testy**. Aby uzyskać więcej informacji na temat sposobu uruchamiania testów, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje uruchamiania KODOWANYCH testów interfejsu użytkownika* w sekcji [co dalej?](#whats-next) na końcu tego tematu.

Pozostałe sekcje w tym temacie zawierają więcej szczegółowych informacji na temat kroków opisanych w tej procedurze.

Aby zapoznać się z bardziej szczegółowym przykładem, zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W tym przewodniku utworzysz prostą aplikację Windows Presentation Foundation (WPF), która pokazuje, jak tworzyć, edytować i obsługiwać kodowane testy interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

## <a name="start-and-stop-the-application-under-test"></a>Uruchamianie i zatrzymywanie testowanej aplikacji

Jeśli nie chcesz uruchamiać i zatrzymywać aplikacji, przeglądarki lub bazy danych osobno dla każdego testu, wykonaj jedną z następujących czynności:

- Jeśli nie chcesz rejestrować akcji do uruchamiania testowanej aplikacji, musisz uruchomić aplikację przed wybraniem ikony **rekordu** .

- Na końcu testu proces, w którym są kończone przebiegi testowe. Jeśli aplikacja została uruchomiona w teście, aplikacja zwykle zostanie zamknięta.  Jeśli nie chcesz, aby test zamykał aplikację po jej zakończeniu, Dodaj plik *. runsettings* do rozwiązania i użyj opcji `KeepExecutorAliveAfterLegacyRun`. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Dodaj metodę inicjowania testu, identyfikowaną przez atrybut `[TestInitialize]`, który uruchamia kod na początku każdej metody testowej. Na przykład można uruchomić aplikację z metody TestInitialize.

- Dodaj metodę oczyszczania testu, identyfikowaną przez atrybut `[TestCleanup]`, który uruchamia kod na końcu każdej metody testowej. Na przykład Metoda zamykania aplikacji może być wywołana z metody TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Weryfikowanie właściwości formantów interfejsu użytkownika

Możesz użyć **konstruktora kodowanego testu interfejsu** użytkownika, aby dodać formant interfejsu użytkownika do [UIMap](/previous-versions/dd580454(v=vs.140)) dla testu lub wygenerować kod dla metody walidacji, która używa potwierdzenia dla kontrolki interfejsu użytkownika.

Aby wygenerować potwierdzenia dla formantów interfejsu użytkownika, wybierz narzędzie **Dodaj potwierdzenia** w **konstruktorze KODOWANEGO testu interfejsu użytkownika** i przeciągnij je do kontrolki w testowanej aplikacji, która ma zostać zweryfikowana. Gdy pole zawiera opis kontrolki, zwolnij przycisk myszy. Kod klasy kontrolki jest natychmiast tworzony w pliku *UIMap.Designer.cs* .

![Element docelowy kodowanego testu interfejsu użytkownika](../test/media/codedui_1.png)

Właściwości tej kontrolki są teraz wyświetlane w oknie dialogowym **Dodawanie potwierdzeń** .

Innym sposobem przechodzenia do konkretnej kontrolki jest wybranie strzałki **(< <)** , aby rozwinąć widok **mapy formantów interfejsu użytkownika**. Aby znaleźć kontrolkę nadrzędną, równorzędną lub podrzędną, można kliknąć dowolne miejsce na mapie i użyć klawiszy strzałek do poruszania się po drzewie.

![Właściwości kodowanego testu interfejsu użytkownika](../test/media/codedui_2.png)

> [!TIP]
> Jeśli nie widzisz żadnych właściwości w przypadku wybrania kontrolki w aplikacji lub nie widzisz kontrolki na mapie formantów interfejsu użytkownika, sprawdź, czy kontrolka ma unikatowy identyfikator w kodzie aplikacji. Unikatowy identyfikator może być atrybutem identyfikatora HTML lub identyfikatorem UId WPF.

Następnie otwórz menu skrótów dla właściwości kontrolki interfejsu użytkownika, którą chcesz zweryfikować, a następnie wskaż polecenie **Dodaj potwierdzenie**. W oknie dialogowym **Dodaj potwierdzenie** wybierz **komparator** dla potwierdzenia, na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, i wpisz wartość dla potwierdzenia w polu **wartość porównania**.

![Zatwierdzeń kodowanego testu interfejsu użytkownika](../test/media/codedui_3.png)

Po dodaniu wszystkich potwierdzeń dla testu wybierz **przycisk OK**.

Aby wygenerować kod dla potwierdzeń i dodać formant do mapy interfejsu użytkownika, wybierz ikonę **Generuj kod** . Wpisz nazwę metody kodowanego testu interfejsu użytkownika i opis metody, która zostanie dodana jako komentarz dla metody. Wybierz pozycję **Dodaj i Generuj**. Następnie wybierz ikonę **Zamknij** , aby zamknąć **konstruktora KODOWANEGO testu interfejsu użytkownika**. Spowoduje to wygenerowanie kodu podobnego do poniższego kodu. Na przykład jeśli wprowadzona nazwa jest `AssertForAddTwoNumbers`, kod będzie wyglądać podobnie do tego przykładu:

- Dodaje wywołanie metody Assert AssertForAddTwoNumbers do metody testowej w pliku kodowanego testu interfejsu użytkownika:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Można edytować ten plik, aby zmienić kolejność kroków i potwierdzeń lub utworzyć nowe metody testowe. Aby dodać więcej kodu, umieść kursor w metodzie testowej, a następnie w menu skrótów wybierz polecenie **Generuj kod dla kodowanego testu interfejsu użytkownika**.

- Dodaje metodę o nazwie `AssertForAddTwoNumbers` do mapy interfejsu użytkownika (*UIMap. UITest*). Ten plik zostanie otwarty w **Edytorze kodowanego testu interfejsu użytkownika**, w którym można edytować potwierdzenia.

     ![Edytuj potwierdzenie przy użyciu edytora kodowanego testu interfejsu użytkownika](../test/media/cuit_editor_assert.png)

     Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Możesz również wyświetlić wygenerowany kod metody Assert w *UIMap.Designer.cs*. Nie należy jednak edytować tego pliku. Jeśli chcesz dostosować wersję kodu, skopiuj metody do innego pliku, takiego jak *UIMap.cs*, Zmień nazwę metod i zmodyfikuj je w tym miejscu.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Wybieranie ukrytego formantu przy użyciu klawiatury

Jeśli formant, który chcesz wybrać, utraci fokus i znika po wybraniu narzędzia **Dodaj potwierdzenia** z **konstruktora KODOWANEGO testu interfejsu użytkownika**:

Czasami podczas dodawania kontrolek i weryfikowania ich właściwości może być konieczne korzystanie z klawiatury. Na przykład podczas próby zarejestrowania kodowanego testu interfejsu użytkownika, który używa kontrolki menu dostępnego po kliknięciu prawym przyciskiem myszy, lista elementów menu w kontrolce spowoduje utratę fokusu i znika przy próbie wybrania narzędzia **Dodaj potwierdzenia** z **konstruktora KODOWANEGO testu interfejsu użytkownika**. Jest to zademonstrowane na poniższej ilustracji, gdzie menu dostępne po kliknięciu prawym przyciskiem myszy w programie Internet Explorer traci fokus i znika, gdy użytkownik próbuje wybrać go za pomocą narzędzia **dodawania potwierdzeń** .

![Zestaw SDK CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Aby użyć klawiatury do wybrania kontrolki interfejsu użytkownika, umieść kursor nad kontrolką za pomocą myszy. Następnie trzymaj wciśnięty klawisz **Ctrl** i klawisz **i** w tym samym czasie. Zwolnij klawisze. Formant jest rejestrowany przez **konstruktora kodowanego testu interfejsu użytkownika**.

#### <a name="manually-record-mouse-hovers"></a>Ręcznie Rejestruj przesuwanie myszy

Jeśli nie możesz zarejestrować wskaźnika myszy na kontrolce:

W pewnych okolicznościach konkretna kontrolka, która jest używana w kodowanym teście interfejsu użytkownika, może wymagać użycia klawiatury do ręcznego rejestrowania zdarzeń przesuwania myszy. Na przykład podczas testowania formularza systemu Windows lub aplikacji Windows Presentation Foundation (WPF) może istnieć kod niestandardowy. Można też mieć specjalne zachowanie zdefiniowane do przesuwania nad formantem, takie jak drzewo drzewa rozwijane po umieszczeniu na nim wskaźnika myszy. Aby przetestować takie okoliczności, trzeba ręcznie powiadomić **konstruktora kodowanego testu interfejsu użytkownika** , który jest przesuwany nad formantem, naciskając wstępnie zdefiniowane klawisze klawiatury.

Po wykonaniu kodowanego testu interfejsu użytkownika Umieść wskaźnik myszy nad kontrolką. Naciśnij i przytrzymaj klawisz **Ctrl**, a następnie naciśnij i przytrzymaj klawisze **SHIFT** i **R** na klawiaturze. Zwolnij klawisze. Zdarzenie przesuwania myszy jest rejestrowane przez **konstruktora kodowanego testu interfejsu użytkownika**.

![CodedUI&#95;aktywowany](../test/media/codedui_hover.png)

Po wygenerowaniu metody testowej kod podobny do następującego przykładu zostanie dodany do pliku *UIMap.Designer.cs* :

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurowanie przypisań klawiatury do przesuwania myszy

Jeśli przypisanie klucza do przechwytywania zdarzeń aktywowania myszy jest używane w innym miejscu w środowisku:

W razie potrzeby domyślne przypisanie klawiatury **Ctrl** +**SHIFT** +**R** , które służy do zastosowania zdarzeń aktywowania myszy w kodowanych testach interfejsu użytkownika, można skonfigurować tak, aby używały różnych kluczy.

> [!WARNING]
> Nie należy zmieniać przypisań klawiatury dla zdarzeń aktywowania myszy w normalnych warunkach. Należy zachować ostrożność podczas ponownego przypisywania przypisania klawiatury. Wybór może być już używany w innym miejscu w programie Visual Studio lub w testowanej aplikacji.

Aby zmienić przypisania klawiatury, zmodyfikuj następujący plik konfiguracji:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

W pliku konfiguracji Zmień wartości `HoverKeyModifier` i `HoverKey` klucze, aby zmodyfikować przypisania klawiatury:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Ustawianie niejawnego przesuwania myszy dla przeglądarki sieci Web

Jeśli masz problemy z nagrywaniem myszy na stronie internetowej:

W wielu witrynach sieci Web, gdy wskaźnik myszy znajduje się nad określoną kontrolką, rozszerza się, aby wyświetlić dodatkowe szczegóły. Ogólnie rzecz biorąc, wyglądają jak menu w aplikacjach komputerowych. Ponieważ jest to typowy wzorzec, kodowane testy interfejsu użytkownika umożliwiają niejawne przechodzenie do przeglądania w sieci Web. Na przykład, Jeśli rejestrujesz aktywowane w programie Internet Explorer, zdarzenie zostanie wyzwolone. Te zdarzenia mogą prowadzić do nagrania nadmiarowych kursorów. Z tego powodu niejawne aktywowanie są rejestrowane przy użyciu `ContinueOnError` ustawione na `true` w pliku konfiguracyjnym testu interfejsu użytkownika. Dzięki temu odtwarzanie będzie kontynuowane w przypadku niepowodzenia zdarzenia aktywowania.

Aby włączyć rejestrowanie niejawnych kursorów w przeglądarce internetowej, Otwórz plik konfiguracji:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Sprawdź, czy plik konfiguracji ma klucz `RecordImplicitiHovers` ustawiony na wartość `true`, jak pokazano w następującym przykładzie:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Dostosowywanie kodowanego testu interfejsu użytkownika

Po utworzeniu kodowanego testu interfejsu użytkownika można go edytować przy użyciu dowolnego z następujących narzędzi w programie Visual Studio:

- Użyj **konstruktora kodowanego testu interfejsu użytkownika** , aby dodać dodatkowe kontrolki i weryfikację do testów. Zobacz sekcję [Dodawanie kontrolek i sprawdzanie poprawności ich właściwości](#validate-the-properties-of-ui-controls) w tym temacie.

- **Edytor kodowanego testu interfejsu użytkownika** pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą **edytora kodowanego testu interfejsu użytkownika**można lokalizować, wyświetlać i edytować metody testowe. Możesz również edytować akcje interfejsu użytkownika i ich skojarzone kontrolki na mapie formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Edytor kodu:**

  - Ręcznie Dodaj kod dla kontrolek w teście zgodnie z opisem w sekcji [kodowane akcje i właściwości kontrolki interfejsu użytkownika](#coded-ui-control-actions-and-properties) w tym temacie.

  - Po utworzeniu kodowanego testu interfejsu użytkownika można go zmodyfikować w taki sposób, aby był oparty na danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kodowanego testu interfejsu użytkownika opartego na danych](../test/creating-a-data-driven-coded-ui-test.md).

  - W przypadku odtwarzania kodowanego testu interfejsu użytkownika można nakazać testowi zaczekać na wystąpienie niektórych zdarzeń, takich jak okno, które ma zostać wyświetlone, pasek postępu, który ma być znikany itd. Aby to zrobić, Dodaj odpowiednią metodę UITestControl. WaitForControlXXX (). Aby uzyskać pełną listę dostępnych metod, zobacz [wykonywanie kodowanych testów interfejsu użytkownika w przypadku określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Przykład kodowanego testu interfejsu użytkownika, który czeka na włączenie formantu przy użyciu metody metody WaitForControlEnabled, zawiera [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5 zawartych w programie Internet Explorer 9 i Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).

  - Wskazówki dotyczące kodowania kodowanego testu interfejsu użytkownika:

    - [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)

    - [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)

    - [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Wygenerowany kod

Gdy wybierzesz opcję **Generuj kod**, tworzone są kilka fragmentów kodu:

- Wiersz w metodzie testowej.

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.      }
    }
    ```

     Możesz kliknąć prawym przyciskiem myszy tę metodę, aby dodać bardziej zarejestrowane akcje i weryfikacje. Możesz również ręcznie ją edytować, aby zwiększyć lub zmodyfikować kod. Na przykład można ująć część kodu w pętli.

     Możesz także dodać nowe metody testowe i dodać kod do nich w taki sam sposób. Każda metoda testowa musi mieć atrybut `[TestMethod]`.

- Metoda w *UIMap. UITest*.

     Ta metoda zawiera szczegółowe informacje o zarejestrowanych akcjach lub zweryfikowanej wartości. Możesz edytować ten kod, otwierając *UIMap. UITest*. Zostanie otwarta w wyspecjalizowanym edytorze, w którym można usunąć lub refaktoryzację zarejestrowanych akcji.

     Możesz również wyświetlić wygenerowaną metodę w *UIMap.Designer.cs*. Ta metoda wykonuje działania zarejestrowane podczas wykonywania testu.

    ```csharp
    // File: UIMap.Designer.cs
    public partial class UIMap
    {
      /// <summary>
      /// Add two numbers
      /// </summary>
      public void AddTwoNumbers()
      { ...   }
    }
    ```

    > [!WARNING]
    > Nie należy edytować tego pliku, ponieważ zostanie on wygenerowany ponownie podczas tworzenia kolejnych testów.

     Można dostosować wersje tych metod, kopiując je do *UIMap.cs*. Na przykład można utworzyć sparametryzowanej wersji, którą można wywołać z metody testowej:

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- Deklaracje w *UIMap. UITest*.

    Te deklaracje reprezentują kontrolki interfejsu użytkownika aplikacji, które są używane przez test. Są one używane przez wygenerowany kod do obsługi kontrolek i uzyskiwania dostępu do ich właściwości.

    Można ich również użyć w przypadku pisania własnego kodu. Na przykład możesz mieć metodę testową, aby wybrać hiperłącze w aplikacji sieci Web, wpisać wartość w polu tekstowym lub rozgałęzić i wykonać różne akcje testowania na podstawie wartości w polu.

    Można dodać wiele kodowanych testów interfejsu użytkownika i wiele obiektów i plików map interfejsu użytkownika w celu ułatwienia testowania dużej aplikacji. Aby uzyskać więcej informacji, zobacz [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md).

Aby uzyskać więcej informacji na temat wygenerowanego kodu, zobacz [anatomię kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Kodowane akcje i właściwości kontrolki interfejsu użytkownika

Podczas pracy z kontrolkami testu interfejsu użytkownika w kodowanych testach interfejsu użytkownika są one podzielone na dwie części: akcje i właściwości.

- Pierwsza część składa się z akcji, które można wykonać na kontrolkach testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika mogą symulować kliknięcia myszą w kontrolce testu interfejsu użytkownika lub symulować klucze wpisane na klawiaturze, aby mieć wpływ na kontrolę testu interfejsu użytkownika.

- Druga część obejmuje umożliwienie pobierania i ustawiania właściwości kontrolki testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika mogą pobierać liczbę elementów w `ListBox` lub ustawiać `CheckBox` do wybranego stanu.

**Uzyskiwanie dostępu do akcji kontroli testu interfejsu użytkownika**

Aby wykonać akcje na kontrolkach testów interfejsu użytkownika, takich jak kliknięcia myszą lub akcje klawiatury, użyj metod z klas <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> i <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>:

- Aby wykonać akcję zorientowaną myszą, taką jak kliknięcie myszą, na kontrolce testu interfejsu użytkownika Użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- Aby wykonać akcję zorientowaną na klawiaturę, taką jak wpisywanie do kontrolki edycji, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Uzyskiwanie dostępu do właściwości kontrolki testu interfejsu użytkownika**

Aby uzyskać i ustawić wartości właściwości dla kontrolki interfejsu użytkownika, można bezpośrednio pobrać lub ustawić wartości właściwości kontrolki lub użyć metod <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> z nazwą konkretnej właściwości, która ma zostać pobrana lub ustawiona.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> zwraca obiekt, który następnie może być rzutowany na odpowiedni <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> akceptuje obiekt dla wartości właściwości.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Aby uzyskać lub ustawić właściwości z kontrolek testu interfejsu użytkownika bezpośrednio

Z kontrolkami, które pochodzą z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, takich jak [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) lub [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), można bezpośrednio uzyskać lub ustawić wartości właściwości. Poniższy kod przedstawia kilka przykładów:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z kontrolek testu interfejsu użytkownika

- Aby uzyskać wartość właściwości z kontrolki, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Aby określić właściwość kontrolki do pobrania, użyj odpowiedniego ciągu z klasy `PropertyNames` w każdej kontrolce jako parametru do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> zwraca odpowiedni typ danych, ale ta wartość zwracana jest rzutowana jako <xref:System.Object>. Zwracane <xref:System.Object> muszą następnie być rzutowane jako odpowiedni typ.

     Przykład:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości dla kontrolek testu interfejsu użytkownika

- Aby ustawić właściwość w kontrolce, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Aby określić właściwość kontrolki do ustawienia, użyj odpowiedniego ciągu z klasy `PropertyNames` jako pierwszy parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, z wartością właściwości jako drugi parametr.

     Przykład:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Debugowanie

Kodowane testy interfejsu użytkownika można analizować za pomocą dzienników kodowanego testu interfejsu użytkownika. Dzienniki kodowanych testów interfejsu użytkownika filtru i rejestrowania ważnych informacji o kodowanych przebiegach testów interfejsu użytkownika. Format dzienników pozwala szybko debugować problemy. Aby uzyskać więcej informacji, zobacz [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co dalej?

**Dodatkowe opcje uruchamiania kodowanych testów interfejsu użytkownika:** Kodowane testy interfejsu użytkownika można uruchomić bezpośrednio z programu Visual Studio, zgodnie z opisem we wcześniejszej części tego tematu. Dodatkowo można uruchamiać zautomatyzowane testy interfejsu użytkownika z Microsoft Test Manager lub przy użyciu Azure Pipelines. Gdy kodowane testy interfejsu użytkownika są zautomatyzowane, muszą one współdziałać z pulpitem podczas jego uruchamiania, w przeciwieństwie do innych automatycznych testów.

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)

- [Uruchom testy w procesie kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Dodawanie obsługi niestandardowych formantów:**  Struktura testowania kodowanego interfejsu użytkownika nie obsługuje wszystkich możliwych interfejsów użytkownika i może nie obsługiwać interfejsu użytkownika, który ma zostać przetestowany. Na przykład nie można natychmiast utworzyć kodowanego testu interfejsu użytkownika dla programu Microsoft Excel. Można jednak utworzyć rozszerzenie dla kodowanego środowiska testowania interfejsu użytkownika, które obsługuje kontrolkę niestandardową.

- [Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md)

- [Poszerzenie kodowanych testów interfejsu użytkownika i nagrań akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodowane testy interfejsu użytkownika są często używane do automatyzowania ręcznych testów. Aby uzyskać więcej informacji na temat testów ręcznych, zobacz [Uruchamianie testów ręcznych z Microsoft Test Manager](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Aby uzyskać więcej informacji o zautomatyzowanych testach, zobacz [narzędzia testowe w programie Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Zobacz także

- [Rejestrowanie i odtwarzanie testów ręcznych](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Xamarin. UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Tworzenie kodowanego testu interfejsu użytkownika w celu przetestowania aplikacji platformy UWP](test-uwp-app-with-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
