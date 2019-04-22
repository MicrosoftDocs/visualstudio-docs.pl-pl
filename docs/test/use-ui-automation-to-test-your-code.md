---
title: Zautomatyzowane testy interfejsu użytkownika
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6798af3630f81aa50eaae05b23b6844dcba1f38
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58897728"
---
# <a name="use-ui-automation-to-test-your-code"></a>Używanie automatyzacji interfejsu użytkownika do testowania kodu

Testy automatyczne, które kontrolują aplikację przez jej interfejs użytkownika (UI) są znane jako *kodowane testy interfejsu użytkownika* (CUITs) w programie Visual Studio. Te testy obejmują, aplikacja jest funkcjonalna kontrolek interfejsu użytkownika. Umożliwiają one możesz sprawdzić, czy całej aplikacji, w tym interfejs użytkownika działa poprawnie. Kodowane testy interfejsu użytkownika są szczególnie przydatne, gdy sprawdzanie poprawności lub inna logika interfejsu użytkownika, na przykład na stronie sieci web. Są one również często używane do automatyzowania istniejącego testu ręcznego.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Jak pokazano na poniższej ilustracji, w środowisku projektowym typowe może być where, początkowo wystarczy skompilować aplikację i kliknij przycisk za pomocą kontrolek interfejsu użytkownika, aby sprawdzić, czy wszystko działa poprawnie. Następnie można zdecydować, do tworzenia automatycznych testów, dzięki czemu nie trzeba ręcznie przetestować aplikację w dalszym ciągu. W zależności od konkretnej funkcji testowane w aplikacji można napisać kod dla funkcjonalności testu lub test integracji, który może być lub może nie zawierać testowania na poziomie interfejsu użytkownika. Jeśli chcesz uzyskać bezpośredni dostęp do niektórych logiki biznesowej, może być kodu testu jednostkowego. Jednak w pewnych okolicznościach może być korzystne uwzględnić testowania różnych kontrolek interfejsu użytkownika w aplikacji. Kodowany test interfejsu użytkownika sprawdzić, czy ten postęp dokonany w kodzie nie ma wpływu na funkcjonalność aplikacji.

![Testowanie podczas tworzenia aplikacji](../test/media/cuit_overview.png)

Tworzenie kodowanego testu interfejsu użytkownika jest proste. Po prostu wykonywania testu ręcznego podczas **Konstruktor kodowanego testu IU** działa w tle. Można również określić, jakie wartości powinna zostać wyświetlona w określonych polach. **Konstruktor kodowanego testu interfejsu użytkownika** rejestruje swoje działania i generuje kod z nich. Po utworzeniu testu można edytować go w edytorze specjalistyczne, która umożliwia modyfikowanie sekwencję akcji.

Alternatywnie Jeśli przypadek testowy, który został zarejestrowany w programie Microsoft Test Manager, istnieje możliwość wygenerowania kodu przy jego użyciu. Aby uzyskać więcej informacji, zobacz [rekordu i odtwarzać ponownie ręcznych testów](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts).

Wyspecjalizowane **kodowanego testu interfejsu użytkownika** i Edytor testów ułatwiają tworzenie i Edycja kodowanego interfejsu użytkownika, nawet wtedy, gdy umiejętności w zakresie głównym jest skoncentrowana testowania zamiast kodowania. Ale jeśli jesteś deweloperem i chcesz rozszerzyć test w sposób bardziej zaawansowane, kod mają strukturę, aby był prosty skopiować i dostosowania. Na przykład Nagraj test do zakupu w witrynie sieci Web, a następnie edytuj wygenerowany kod, aby dodać pętlę, która kupuje się wiele elementów.

**Wymagania**

- Visual Studio Enterprise
- Kodowane składnik testu interfejsu użytkownika

Aby uzyskać więcej informacji o tym, które platformy i konfiguracje są obsługiwane przez kodowane testy interfejsu użytkownika, zobacz [obsługiwanych platform](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Zainstaluj składnik kodowanego testu interfejsu użytkownika

Aby uzyskać dostęp do narzędzi do testowania interfejsu użytkownika kodowany i szablonów, należy zainstalować **kodowanego testu interfejsu użytkownika** składnika programu Visual Studio.

1. Uruchom **Instalatora programu Visual Studio** , wybierając **narzędzia** > **Pobierz narzędzia i funkcje**.

1. W **Instalatora programu Visual Studio**, wybierz **poszczególne składniki** kartę, a następnie przewiń w dół do **debugowanie i testowanie** sekcji. Wybierz **kodowanego testu interfejsu użytkownika** składnika.

   ![Kodowane składnik testu interfejsu użytkownika](media/coded-ui-test-component.png)

1. Wybierz **zmodyfikować**.

## <a name="create-a-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika

1. Utwórz projekt kodowanego testu interfejsu użytkownika.

   Kodowane testy interfejsu użytkownika musi być zawarty w projekt kodowanego testu interfejsu użytkownika. Jeśli nie masz jeszcze projektu kodowanego testu interfejsu użytkownika, zrób to. Wybierz **pliku** > **nowe** > **projektu**. Wyszukaj i wybierz pozycję **projekt kodowanego testu interfejsu użytkownika** szablonu projektu.

   ::: moniker range="vs-2017"

   ![Kodowanego testu interfejsu użytkownika szablonu projektu w oknie dialogowym Nowy projekt](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli nie widzisz **projekt testu kodowanego interfejsu użytkownika** szablonu, trzeba [instalacji składnika należy kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Dodaj plik kodowanego testu interfejsu użytkownika.

     Jeśli właśnie utworzone projektu kodowanego interfejsu użytkownika, pierwszy plik CUIT jest automatycznie dodawany. Aby dodać inny plik testowy, otwórz menu skrótów projektu kodowanego testu interfejsu użytkownika w **Eksploratora rozwiązań**, a następnie wybierz **Dodaj** > **kodowanego testu interfejsu użytkownika**.

     W **Generuj kod dla kodowanego testu interfejsu użytkownika** okna dialogowego wybierz **Rejestruj akcje** > **Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia**.

     ![Generuj kod dla okno dialogowe kodowanego testu interfejsu użytkownika](media/generate-code-for-coded-ui-test.png)

     **Kodowanego testu interfejsu użytkownika** pojawia się.

     ![Konstruktor testu kodowanego interfejsu użytkownika](../test/media/codedui_testbuilder.png)

3. Rekord sekwencję akcji.

     **Aby rozpocząć rejestrowanie**, wybierz **rekordu** ikony. Wykonywanie akcji, które mają zostać przetestowane w aplikacji, w tym uruchamianie aplikacji, jeśli jest to wymagane. Na przykład jeśli testujesz aplikację sieci web możesz może uruchamiają przeglądarkę, przejdź do witryny sieci Web i zaloguj się do aplikacji.

     **Aby Wstrzymaj nagrywanie**, na przykład jeśli masz do czynienia z przychodzących wiadomości e-mail, wybierz **wstrzymać**.

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, jeśli są wykonywane działania, które mogą prowadzić do danych poufnych jest zawarty w nagraniu.

     **Można usunąć akcji** zapisane przez pomyłkę, wybierz polecenie **edytować kroki**.

     **Do generowania kodu** , będzie replikowanie Twoje działania, wybierz **Generuj kod** ikonę i wpisz nazwę i opis dla kodowanego interfejsu użytkownika metoda testowa.

4. Sprawdź wartości w polach interfejsu użytkownika, takie jak pola tekstowe.

     Wybierz **dodawania potwierdzeń** w **kodowanego testu interfejsu użytkownika**, a następnie wybierz kontrolkę interfejsu użytkownika w uruchomionej aplikacji. Pojawia się liście właściwości wybierz właściwość, na przykład **tekstu** w polu tekstowym. W menu skrótów wybierz **Dodaj potwierdzenie**. W oknie dialogowym Wybierz operator porównania, wartość porównania i komunikat o błędzie.

     Zamknij okno potwierdzenia, a następnie wybierz **Generuj kod**.

     ![Kodowane element określania wartości docelowej testu interfejsu użytkownika](../test/media/codedui_1.png)

    > [!TIP]
    > Przełącza między rejestrowanie akcji i weryfikowanie wartości. Generowanie kodu na końcu każdego sekwencję akcji lub weryfikacji. Jeśli chcesz, będzie można później Wstaw nowe akcje i weryfikacji.

     Aby uzyskać więcej informacji, zobacz [zweryfikować właściwości formantów](#validate-the-properties-of-ui-controls).

5. Wyświetl kod wygenerowany test.

     Aby wyświetlić wygenerowany kod, zamknij okno konstruktora testu interfejsu użytkownika. W kodzie widać nazwy, które na każdym kroku. Kod znajduje się w pliku CUIT, który został utworzony:

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

6. Dodaj więcej akcji i potwierdzenia.

   Umieść kursor we właściwym miejscu w metodzie testowej, a następnie w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**. Nowy kod zostanie wstawiony w tym momencie.

7. Edytuj szczegóły działań testów i potwierdzenia.

     Otwórz *UIMap.uitest*. Ten plik zostanie otwarty w **edytora kodowanego testu interfejsu użytkownika**, gdzie można edytować dowolnej sekwencji akcji, które nagrałeś oraz jak edytować swoje potwierdzenia.

     ![Edytor kodowanego testu interfejsu użytkownika](../test/media/cuit_editor_edit.png)

     Aby uzyskać więcej informacji, zobacz [Edycja kodowanych testów interfejsu użytkownika, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Uruchom test.

   Eksplorator testów lub Otwórz menu skrótów w metodzie testowej, a następnie wybierz **Uruchom testy**. Aby uzyskać więcej informacji o sposobach uruchamiania testów, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika* w [co przyniesie przyszłość?](#whats-next) sekcji w zakończenie tego tematu.

Pozostałe sekcje w tym temacie więcej szczegółowych informacji o krokach w tej procedurze.

Aby uzyskać bardziej szczegółowym przykładem, zobacz [instruktażu: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W instruktażu utworzysz prostą aplikację Windows Presentation Foundation (WPF) w celu zademonstrowania sposobu tworzenia, edytowania i obsługa kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

## <a name="start-and-stop-the-application-under-test"></a>Uruchamianie i zatrzymywanie testowaną aplikację

Jeśli nie chcesz uruchomić i zatrzymać aplikację, przeglądarki lub bazy danych oddzielnie dla każdego testu, wykonaj jedną z następujących czynności:

- Jeśli nie chcesz Rejestruj akcje, które można uruchomić Twojej aplikacji poddawanej testom, należy uruchomić aplikację przed wybraniem **rekordu** ikony.

- Po zakończeniu testu zakończenia procesu, w którym przeprowadzany jest test. Jeśli aplikacja jest uruchomiona w teście, zwykle powoduje zamknięcie aplikacji.  Jeśli nie chcesz, aby test, aby zamknąć aplikację, kiedy wychodzi, Dodaj *.runsettings* plików do rozwiązania, a następnie użyj `KeepExecutorAliveAfterLegacyRun` opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Dodaj metodę initialize badania identyfikowane przez `[TestInitialize]` atrybut, który uruchamia kod na początku każdej metody testowej. Na przykład można uruchomić aplikacji z metody TestInitialize.

- Metoda czyszcząca testu, identyfikowane przez dodawanie `[TestCleanup]` atrybutu, która uruchamia kod na końcu każdej metody testowej. Na przykład metody, aby zamknąć aplikację może być wywołana z metoda TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Sprawdzanie poprawności właściwości formantów interfejsu użytkownika

Możesz użyć **Konstruktor kodowanego testu IU** można dodać kontrolki interfejsu użytkownika do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> dla testu lub do generowania kodu dla metody sprawdzania poprawności, który używa potwierdzenie dla kontrolki interfejsu użytkownika.

Aby wygenerować potwierdzenia dla Twoich kontrolek interfejsu użytkownika, wybierz opcję **dodawania potwierdzeń** narzędzia w **Konstruktor kodowanego testu IU** i przeciągnij go do formantu w aplikacji poddawanej testowi, który chcesz zweryfikować jest poprawna. Gdy pole zawiera opis kontrolki, zwolnij przycisk myszy. Kod klasy formantu natychmiast jest tworzony w *UIMap.Designer.cs* pliku.

![Kodowane element określania wartości docelowej testu interfejsu użytkownika](../test/media/codedui_1.png)

Właściwości dla tego formantu są wyświetlane w **dodawania potwierdzeń** okno dialogowe.

Inny sposób przejścia do określonego formantu jest wybierz strzałkę **(<<)** rozszerzania widok **mapy formantów UI**. Aby znaleźć nadrzędnego, element równorzędny lub kontrolki podrzędnej, możesz kliknij w dowolnym miejscu na mapie i używaj klawiszy strzałek Aby poruszać się po drzewie.

![Kodowane właściwości testu interfejsu użytkownika](../test/media/codedui_2.png)

> [!TIP]
> Jeśli nie widzisz żadnych właściwości, po wybraniu kontrolki w aplikacji lub nie jest widoczny na formant mapy formantów interfejsu użytkownika, sprawdź, czy kontrolka ma unikatowy identyfikator w kodzie aplikacji. Unikatowy identyfikator może być atrybutu HTML Identyfikatora lub WPF UId.

Następnie otwórz menu skrótów dla właściwości do kontrolki interfejsu użytkownika, który chcesz sprawdzić, a następnie wskaż **Dodaj potwierdzenie**. W **Dodaj potwierdzenie** okno dialogowe, wybierz opcję **Komparator** do potwierdzenia, na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, a następnie wpisz wartość dla Twojego potwierdzenia w **porównywana wartość**.

![Kodowane asercji test interfejsu użytkownika](../test/media/codedui_3.png)

Po dodaniu wszystkich asercje o dla testu wybierz **OK**.

Aby wygenerować kod dla potwierdzenia usługi i Dodaj formant do mapy interfejsu użytkownika, wybierz **Generuj kod** ikony. Wpisz nazwę metodę kodowanego testu interfejsu użytkownika i opis metody, które zostaną dodane jako komentarze do metody. Wybierz **Dodaj i wygeneruj**. Następnie wybierz pozycję **Zamknij** ikoną, aby zamknąć **kodowanego testu interfejsu użytkownika**. Spowoduje to wygenerowanie kodu podobne do następującego kodu. Na przykład, jeśli wprowadzona nazwa jest `AssertForAddTwoNumbers`, kod będzie wyglądać następująco:

- Dodaje wywołanie metody assert AssertForAddTwoNumbers do metody testowej w pliku kodowanego testu interfejsu użytkownika:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Możesz edytować ten plik, aby zmienić kolejność kroków i potwierdzenia lub tworzenie nowych metod testowych. Aby dodać więcej kodu, umieść kursor na metodzie testowej, jak i w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**.

- Dodaje metodę o nazwie `AssertForAddTwoNumbers` do mapy interfejsu użytkownika (*UIMap.uitest*). Ten plik zostanie otwarty w **edytora kodowanego testu interfejsu użytkownika**, w którym można edytować potwierdzenia.

     ![Edytuj assert, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/media/cuit_editor_assert.png)

     Aby uzyskać więcej informacji, zobacz [Edycja kodowanych testów interfejsu użytkownika, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Można również wyświetlić wygenerowany kod w metody asercji *UIMap.Designer.cs*. Jednak nie należy edytować ten plik. Jeśli chcesz utworzyć dostosowane wersję kodu, skopiuj metody do innego pliku takich jak *UIMap.cs*, Zmień nazwę metody i edytować je ma.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Wybierz ukrytą kontrolkę za pomocą klawiatury

Jeśli chcesz wybrać traci fokus i kontrolki zniknie po wybraniu **dodawania potwierdzeń** narzędzia z **kodowanego testu interfejsu użytkownika**:

Czasami podczas dodawania kontrolek i sprawdzić ich właściwości może być za pomocą klawiatury. Na przykład podczas próby rejestrowania kodowanego testu interfejsu użytkownika, który używa formant menu kliknij prawym przyciskiem myszy listę elementów menu w formancie zostanie utratę fokus i znikają w przypadku próby wybrania **dodawania potwierdzeń** narzędzia z **kodowanego interfejsu użytkownika Testowanie konstruktora**. Zostało to przedstawione na poniższej ilustracji, gdzie menu kliknij prawym przyciskiem myszy w programie Internet Explorer traci fokus i znika, jeśli zostanie podjęta próba wybierz ją z **dodawania potwierdzeń** narzędzia.

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Aby użyć klawiatury, aby wybrać kontrolkę interfejsu użytkownika, umieść kursor nad kontrolką za pomocą myszy. Wciśnij klawisz **Ctrl** klucza i **I** klucza w tym samym czasie. Wydawanie kluczy. Kontrolka jest rejestrowana przez **kodowanego testu interfejsu użytkownika**.

#### <a name="manually-record-mouse-hovers"></a>Ręcznie wskaźnika myszy rekordu

Jeśli nie można zarejestrować umieść kursor myszy na kontrolce:

W niektórych okolicznościach określonego formantu, który jest używany w coded UI test może wymagać użycia klawiatury do zdarzenia po wskazaniu wskaźnikiem myszy ręcznie rekordów. Na przykład podczas testowania formularza Windows lub aplikacji Windows Presentation Foundation (WPF), może być kod niestandardowy. Lub może być specjalnego zachowania zdefiniowane dla przenosząc kursor myszy nad formant, takich jak rozwijanie, gdy użytkownik zatrzyma na niej węzła drzewa. Aby przetestować okoliczności, takie jak te, musisz ręcznie Powiadom **Konstruktor kodowanego testu IU** , są się na formancie, naciskając wstępnie zdefiniowane klawisze klawiatury.

Podczas wykonywania kodowanego testu interfejsu użytkownika, umieść kursor nad kontrolką. Naciśnij i przytrzymaj **Ctrl**, podczas gdy naciśnij i przytrzymaj klawisz **Shift** i **R** za pomocą klawiszy. Wydawanie kluczy. Zdarzenie po wskazaniu wskaźnikiem myszy jest rejestrowana przez **kodowanego testu interfejsu użytkownika**.

![CodedUI&#95;Hover](../test/media/codedui_hover.png)

Po wygenerowaniu metody testowej kod podobny do poniższego przykładu zostaną dodane do *UIMap.Designer.cs* pliku:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurowanie przypisań klawiatury umieść kursor myszy

Jeśli przypisanie klucza do przechwytywania zdarzeń po wskazaniu wskaźnikiem myszy jest on używany w innym miejscu w mojego środowiska:

Jeśli to konieczne, domyślnie za pomocą klawiatury przypisanie **Ctrl**+**Shift**+**R** umożliwiający stosowanie zdarzenia po wskazaniu wskaźnikiem myszy w kodowanych testach interfejsu użytkownika można skonfigurować do używania różnych kluczy.

> [!WARNING]
> Zmień przypisania klawiatury dla zdarzeń po wskazaniu wskaźnikiem myszy w zwykłych okolicznościach nie powinna mieć. Ponowne przypisywanie przypisania klawiatury, należy zachować ostrożność. Wybór mogą być już używany w ramach programu Visual Studio lub aplikacja poddawana testom.

Aby zmienić przypisania klawiatury, zmodyfikuj następujący plik konfiguracji:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

W pliku konfiguracji, zmień wartości `HoverKeyModifier` i `HoverKey` klucze do modyfikowania przydziałów klawiatury:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Ustaw niejawne myszy ruchów przeglądarki sieci web

Jeśli występują problemy dotyczące rejestrowania wskaźnik myszy znajdzie się w witrynie internetowej:

W wielu witryn sieci Web po najechaniu kursorem na określonego formantu rozszerza on Aby wyświetlić dodatkowe szczegóły. Ogólnie rzecz biorąc one wyglądać podobnie jak menu w aplikacji klasycznych. Ponieważ jest to typowy wzorzec, kodowane testy interfejsu użytkownika Włącz niejawny ruchów do przeglądania sieci web. Na przykład jeśli rekord użytkownik znajduje się w programie Internet Explorer, zdarzenie jest wywoływane. Te zdarzenia może prowadzić do nadmiarowego ruchów rejestrowane. W związku z tym, niejawny ruchów są rejestrowane przy użyciu `ContinueOnError` równa `true` w pliku konfiguracji testu interfejsu użytkownika. Dzięki temu odtwarzania kontynuować, jeśli zdarzenie po wskazaniu wskaźnikiem zakończy się niepowodzeniem.

Aby włączyć rejestrowanie ruchów niejawne w przeglądarce sieci web, otwórz plik konfiguracji:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Sprawdź, czy plik konfiguracyjny ma klucz `RecordImplicitiHovers` ustawiona na wartość `true` jak pokazano w następującym przykładzie:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Dostosowywanie kodowanego testu interfejsu użytkownika

Po utworzeniu kodowanego testu interfejsu użytkownika można edytować jej za pomocą jednej z następujących narzędzi w programie Visual Studio:

- Użyj **kodowanego testu interfejsu użytkownika** można dodać dodatkowe elementy sterujące i walidacji do testów. Zobacz sekcję [do dodawania kontrolek i sprawdzić ich właściwości](#validate-the-properties-of-ui-controls) w tym temacie.

- **Edytor testu interfejsu użytkownika kodowany** umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą **edytora testu interfejsu użytkownika**, można zlokalizować, wyświetlić i edytować swoje metody testowe. Można również edytować akcje interfejsu użytkownika oraz skojarzone z nimi kontrolki w mapy formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edycja kodowanych testów interfejsu użytkownika, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Edytor kodu:**

    - Ręcznie Dodaj kod dla formantów w teście, zgodnie z opisem w [kodowanego interfejsu użytkownika akcji i właściwości formantów](#coded-ui-control-actions-and-properties) w tym temacie.

    - Po utworzeniu kodowanego testu interfejsu użytkownika, można zmodyfikować, aby była opartych na danych. Aby uzyskać więcej informacji, zobacz [tworzenie opartych na danych kodowanego testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md).

    - Podczas odtwarzania testu kodowanego interfejsu użytkownika można nakazać testu oczekiwania dla określonych zdarzeń, takiego jak okno pojawia się pasek postępu zniknąć i tak dalej. Aby to zrobić, należy dodać odpowiednią metodę UITestControl.WaitForControlXXX(). Aby uzyskać pełną listę dostępnych metod, zobacz [utworzyć kodowane testy interfejsu użytkownika oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Na przykład kodowane testy interfejsu użytkownika, która czeka na formant włączyć przy użyciu metody WaitForControlEnabled zobacz [instruktażu: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    - Kodowane testy interfejsu użytkownika obsługują niektóre formanty języka HTML5, które są dołączone do programu Internet Explorer 9 i Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [HTML5 za pomocą kontrolki w kodowanych testów interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).

    - Wskazówki dotyczące kodowania kodowanego testu interfejsu użytkownika:

       - [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)

       - [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)

       - [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)

       - [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Wygenerowany kod

Po wybraniu **Generuj kod**, tworzonych jest kilka fragmentów kodu:

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

     Możesz kliknąć prawym przyciskiem myszy w przypadku tej metody, aby dodać więcej zarejestrowane akcje i weryfikacji. Można również edytować je ręcznie, aby rozszerzyć lub zmodyfikować kod. Na przykład można część kodu ująć w pętli.

     Można także dodać nowe metody testowe i dodać kod do nich w taki sam sposób. Każda metoda testowa musi mieć `[TestMethod]` atrybutu.

- Metoda w *UIMap.uitest*.

     Ta metoda obejmuje szczegółów nagrane akcje lub wartość, która Cię o zweryfikowanie informacji. Ten kod można edytować, otwierając *UIMap.uitest*. Zostanie otwarty w edytorze specjalistyczne, można usunąć lub refaktoryzować zarejestrowane akcje.

     Można również wyświetlić wygenerowana metoda w *UIMap.Designer.cs*. Ta metoda wykonuje akcje rejestrowane po uruchomieniu testu.

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
    > Nie należy edytować tego pliku, ponieważ zostaną wygenerowane, gdy tworzysz więcej testów.

     Możesz wprowadzić dostosowane wersji tych metod, kopiując je do *UIMap.cs*. Na przykład można dokonać sparametryzowane wersji, który można wywołać z metody testowej:

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

- Deklaracje w *UIMap.uitest*.

    Te deklaracje reprezentują kontrolek interfejsu użytkownika aplikacji, które są używane w ramach testu. Służą one przez wygenerowany kod do obsługi formantów i uzyskiwanie dostępu do ich właściwości.

    Umożliwia także je w przypadku pisania własnego kodu. Na przykład można mieć swojej metody testowej, wybierz hiperłącze w aplikacji sieci web, wpisz wartość w polu tekstowym lub gałęzie i wykonać różne operacje testowania na podstawie wartości w polu.

    Można dodać wiele kodowane testy interfejsu użytkownika i wiele obiektów mapy interfejsu użytkownika i pliki, aby usprawnić testowanie dużej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).

Aby uzyskać więcej informacji na temat wygenerowany kod, zobacz [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Kodowane akcji kontrolki UI oraz właściwości

Podczas pracy z kontrolkami testu interfejsu użytkownika w programie kodowane testy interfejsu użytkownika, są one podzielone na dwie części: właściwości i akcje.

- Pierwsza część składa się z akcji, które można wykonywać na kontrolek testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika można symulować kliknięcia myszy na kontrolce testu interfejsu użytkownika lub symulacji wpisywane znaki na klawiaturze, aby wpłynąć na kontrolkę interfejsu użytkownika testu.

- Druga część składa się z pozwala na pobieranie i ustawianie właściwości formantu testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika można uzyskać liczbę elementów w `ListBox`, lub ustawić `CheckBox` do wybranego stanu.

**Uzyskiwanie dostępu do akcji testu IU**

Aby wykonać akcje na test UI, takie jak kliknięcia myszy lub klawiatury akcji, należy użyć metod w <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> i <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> klasy:

- Aby wykonać zorientowane na myszy akcji, takich jak kliknięcie myszą, sterowanie testu interfejsu użytkownika, należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- Aby wykonać akcję korzystający z klawiatury, np. do kontrolki edycji należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Uzyskiwanie dostępu do właściwości kontrolki testu interfejsu użytkownika**

Aby uzyskać i ustawić określone wartości właściwości kontrolki interfejsu użytkownika, można bezpośrednio uzyskać lub ustawić wartości właściwości kontrolki, możesz też <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> metody o nazwie określone właściwości, które chcesz pobrać lub ustawić.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> Zwraca obiekt, który następnie można rzutować na odpowiedni <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> akceptuje obiekt do wartości właściwości.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Aby pobierać lub ustawiać właściwości z kontrolek testu interfejsu użytkownika bezpośrednio

Za pomocą kontrolek, które wynikają z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, takich jak [listy HTML](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) lub [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), można uzyskać lub ustawić bezpośrednio ich wartości właściwości. Poniższy kod pokazuje kilka przykładów:

 ```csharp
 int i = myHtmlList.ItemCount;
 myWinCheckBox.Checked = true;
 ```

### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z kontrolek testu interfejsu użytkownika

- Aby uzyskać wartość właściwości w kontrolce, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Aby określić właściwość kontrolki, które można pobrać, użyj odpowiedni ciąg z `PropertyNames` klasy w każdej kontrolce jako parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> zwraca odpowiedni typ danych, ale zwraca wartość jest rzutowany jako <xref:System.Object>. Zwracany <xref:System.Object> następnie musi być rzutowany jako odpowiedniego typu.

     Przykład:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości formantów testu interfejsu użytkownika

- Aby ustawić właściwości w kontrolce, należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Aby określić właściwość kontrolki, które można ustawić, użyj odpowiedni ciąg z `PropertyNames` klasę jako pierwszy parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, z wartością właściwości jako drugi parametr.

     Przykład:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Debugowanie

Możesz analizować kodowanych testów interfejsu użytkownika za pomocą zakodowanych dziennikach testów interfejsu użytkownika. Kodowane filtr dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje dotyczące Twojego kodowanego testu interfejsu użytkownika. Format dzienniki umożliwia szybkie debugowanie problemów. Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów interfejsu użytkownika, za pomocą zakodowanych dziennikach testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co dalej?

**Dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika:** Można uruchomić kodowane testy interfejsu użytkownika bezpośrednio z programu Visual Studio, zgodnie z opisem we wcześniejszej części tego tematu. Ponadto można uruchomić zautomatyzowane testy interfejsu użytkownika z programu Microsoft Test Manager lub za pomocą potoków usługi Azure. Kodowane testy interfejsu użytkownika są automatyzowane, mają wchodzić w interakcje z pulpitem po uruchomieniu, w przeciwieństwie do innych testów automatycznych.

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)

- [Uruchom testy w procesie kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Dodawanie obsługi kontrolek niestandardowych:**  Kodowanych testów interfejsu użytkownika nie obsługuje każdego możliwego interfejsu użytkownika i może nie obsługiwać interfejsu użytkownika, którą chcesz przetestować. Na przykład nie można od razu utworzyć kodowany test interfejsu użytkownika interfejsu użytkownika dla programu Microsoft Excel. Można jednak utworzyć rozszerzenie kodowanych testów interfejsu użytkownika, który będzie obsługiwać formant niestandardowy.

- [Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozszerzanie kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodowane testy interfejsu użytkownika są często używane do automatyzacji testów ręcznych. Aby uzyskać więcej informacji na temat testów ręcznych, zobacz [uruchamianiem ręcznych testów za pomocą programu Microsoft Test Manager](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Aby uzyskać więcej informacji na temat testów automatycznych, zobacz [narzędzia do testowania w programie Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Tworzenie kodowanego interfejsu użytkownika testu do testowania aplikacji platformy uniwersalnej systemu Windows](test-uwp-app-with-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
