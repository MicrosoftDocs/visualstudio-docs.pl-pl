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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f333cc3409056739cef7c378d9815f10439ab37e
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880367"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Użyj testu kodowany interfejsu użytkownika, aby przetestować kod

Kodowane testy interfejsu użytkownika (CUIT) dysku aplikacji za pośrednictwem interfejsu użytkownika (UI). Testy te obejmują testy funkcjonalne formantów interfejsu użytkownika. Umożliwiają one sprawdzenie, czy cała aplikacja, w tym jej interfejs użytkownika, działa poprawnie. Kodowane testy interfejsu użytkownika są przydatne, gdy istnieje sprawdzanie poprawności lub innej logiki w interfejsie użytkownika, na przykład na stronie sieci web. Są one również często używane do automatyzacji istniejącego testu ręcznego.

Tworzenie kodowany test interfejsu użytkownika w programie Visual Studio jest łatwe. Po prostu wykonać test ręcznie, gdy **Coded UI Test Builder** działa w tle. Można również określić, jakie wartości powinny być wyświetlane w określonych polach. **Konstruktor kodowanych testów interfejsu użytkownika** rejestruje twoje akcje i generuje z nich kod. Po utworzeniu testu można go edytować w specjalistycznym edytorze, który umożliwia modyfikowanie sekwencji akcji.

Wyspecjalizowany **konstruktor** i edytor kodowanych testów interfejsu użytkownika ułatwiają tworzenie i edytowanie kodowanych testów interfejsu użytkownika, nawet jeśli główne umiejętności są skoncentrowane na testowaniu, a nie kodowaniu. Ale jeśli jesteś deweloperem i chcesz rozszerzyć test w bardziej zaawansowany sposób, kod jest skonstruowany tak, że jest łatwy do skopiowania i dostosowania. Na przykład można nagrać test, aby kupić coś w witrynie sieci Web, a następnie edytować wygenerowany kod, aby dodać pętlę, która kupuje wiele elementów.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Wymagania

- Visual Studio Enterprise
- Składnik testu kodowany interfejs użytkownika

Aby uzyskać więcej informacji o platformach i konfiguracjach obsługiwanych przez kodowane testy interfejsu użytkownika, zobacz [Obsługiwane platformy](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Instalowanie składnika testu kodowany interfejs użytkownika

Aby uzyskać dostęp do kodowanych narzędzi testowych interfejsu użytkownika i szablonów, zainstaluj składnik **testu kodowany interfejs użytkownika** programu Visual Studio.

1. Uruchom **Instalatora programu Visual Studio,** wybierając **pozycję Narzędzia** > **Pobierz narzędzia i funkcje**.

1. W **Instalatorze programu Visual Studio**wybierz kartę Poszczególne **składniki,** a następnie przewiń w dół do sekcji **Debugowanie i testowanie.** Wybierz składnik **testu kodowany interfejs użytkownika.**

   ![Składnik testu kodowany interfejs użytkownika](media/coded-ui-test-component.png)

1. Wybierz **pozycję Modyfikuj**.

## <a name="create-a-coded-ui-test"></a>Tworzenie zakodowany test interfejsu użytkownika

1. Tworzenie projektu testu kodowany interfejs użytkownika.

   Kodowane testy interfejsu użytkownika muszą być zawarte w projekcie testu kodowanego interfejsu użytkownika. Jeśli nie masz jeszcze projektu testu kodowany interfejsu użytkownika, utwórz jeden. Wybierz **pozycję Plik** > **nowego** > **projektu**. Wyszukaj i wybierz szablon projektu **projektu testu kodowany** interfejs użytkownika.

   ::: moniker range="vs-2017"

   ![Kodowany szablon projektu testu interfejsu użytkownika w oknie dialogowym Nowy projekt](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli nie widzisz szablonu **projektu testu kodowany** interfejs użytkownika, musisz [zainstalować składnik testu kodowany interfejs użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Dodaj plik testowy kodowany interfejs użytkownika.

     Jeśli właśnie utworzono projekt kodowany interfejs użytkownika, pierwszy plik CUIT jest dodawany automatycznie. Aby dodać kolejny plik testowy, otwórz menu skrótów w projekcie testu kodowany interfejs użytkownika w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Dodaj** > **kodowany test interfejsu użytkownika**.

     W oknie dialogowym **Generowanie kodu dla zakodowanych testów interfejsu użytkownika** wybierz pozycję **Record actions** > **Edit UI map (Edytuj mapę interfejsu użytkownika) lub dodaj potwierdzenia**.

     ![Generowanie kodu dla okna dialogowego testu kodowany interfejs użytkownika](media/generate-code-for-coded-ui-test.png)

     Pojawi **się konstruktor testów kodowanych interfejsów** użytkownika.

     ![Konstruktor testów kodowanych interfejsów użytkownika](../test/media/codedui_testbuilder.png)

3. Nagraj sekwencję akcji.

     **Aby rozpocząć nagrywanie,** wybierz ikonę **Nagrywania.** Wykonaj akcje, które chcesz przetestować w aplikacji, w tym uruchamianie aplikacji, jeśli jest to wymagane. Na przykład jeśli testujesz aplikację sieci web, możesz uruchomić przeglądarkę, przejść do witryny sieci Web i zalogować się do aplikacji.

     **Aby wstrzymać nagrywanie**, na przykład jeśli masz do czynienia z pocztą przychodzącą, wybierz **pozycję Wstrzymaj**.

    > [!WARNING]
    > Wszystkie czynności wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do włączenia poufnych danych do nagrania.

     **Aby usunąć akcje** zarejestrowane przez pomyłkę, wybierz pozycję **Edytuj kroki**.

     **Aby wygenerować kod,** który będzie replikować akcje, wybierz ikonę **Generuj kod** i wpisz nazwę i opis metody testu kodowany interfejs użytkownika.

4. Sprawdź wartości w polach interfejsu użytkownika, takich jak pola tekstowe.

     Wybierz **pozycję Dodaj potwierdzenia** w **konstruktorze testów kodowanych interfejsu użytkownika,** a następnie wybierz kontrolkę interfejsu użytkownika w uruchomionej aplikacji. Na wyświetlona lista właściwości wybierz właściwość, na przykład **Tekst** w polu tekstowym. W menu skrótów wybierz polecenie **Dodaj asercja**. W oknie dialogowym wybierz operator porównania, wartość porównania i komunikat o błędzie.

     Zamknij okno potwierdzenia i wybierz pozycję **Generuj kod**.

     ![Zakodowany element kierowania testu interfejsu użytkownika](../test/media/codedui_1.png)

    > [!TIP]
    > Naprzemienne między nagrywaniem akcji i weryfikowaniem wartości. Generowanie kodu na końcu każdej sekwencji akcji lub weryfikacji. Jeśli chcesz, będziesz mógł później wstawić nowe akcje i weryfikacje.

     Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności właściwości formantów](#validate-the-properties-of-ui-controls).

5. Wyświetl wygenerowany kod testowy.

     Aby wyświetlić wygenerowany kod, zamknij okno Konstruktora testów interfejsu użytkownika. W kodzie można zobaczyć nazwy, które nadały się do każdego kroku. Kod znajduje się w utworzonym pliku CUIT:

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

   Umieść kursor w odpowiednim punkcie metody testowej, a następnie w menu skrótów wybierz polecenie **Generuj kod dla zakodowanych testów interfejsu użytkownika**. Nowy kod zostanie wstawiony w tym momencie.

7. Edytuj szczegóły akcji testowych i potwierdzeń.

     Otwórz *UIMap.uitest*. Ten plik zostanie otwarty w **Edytorze kodowanych testów interfejsu użytkownika,** w którym można edytować dowolną sekwencję nagranych akcji, a także edytować potwierdzenia.

     ![Edytor kodowanego testu interfejsu użytkownika](../test/media/cuit_editor_edit.png)

     Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika przy użyciu edytora kodowany test interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Uruchom test.

   Użyj Eksploratora testów lub otwórz menu skrótów w metodzie testowej, a następnie wybierz polecenie **Uruchom testy**. Aby uzyskać więcej informacji na temat uruchamiania testów, zobacz [Uruchamianie testów jednostkowych z Eksploratorem testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje uruchamiania kodowanych testów interfejsu użytkownika* w sekcji Co [dalej?](#whats-next)

Pozostałe sekcje w tym temacie zawierają więcej szczegółów na temat kroków w tej procedurze.

Aby uzyskać bardziej szczegółowy przykład, zobacz [Instruktaż: Tworzenie, edytowanie i obsługa testu kodowany interfejs użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W instruktażu utworzysz prostą aplikację Windows Presentation Foundation (WPF), aby zademonstrować sposób tworzenia, edytowania i obsługi testu kodowany interfejs użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

## <a name="start-and-stop-the-application-under-test"></a>Uruchamianie i zatrzymywania testowej aplikacji

Jeśli nie chcesz uruchamiać i zatrzymywać aplikacji, przeglądarki lub bazy danych oddzielnie dla każdego testu, wykonaj jedną z następujących czynności:

- Jeśli nie chcesz rejestrować akcji, aby uruchomić aplikację w ramach testu, należy uruchomić aplikację przed wybraniem ikony **Rekord.**

- Po zakończeniu testu proces, w którym test jest zakończony. Po uruchomieniu aplikacji w teście, aplikacja zwykle zamyka.  Jeśli nie chcesz, aby test, aby zamknąć aplikację po jej zamknięciu, dodaj plik `KeepExecutorAliveAfterLegacyRun` *.runsettings* do rozwiązania i użyj tej opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Dodaj metodę inicjowania testu, `[TestInitialize]` identyfikowaną przez atrybut, który uruchamia kod na początku każdej metody testowej. Na przykład można uruchomić aplikację z TestInitialize metody.

- Dodaj metodę oczyszczania testu, identyfikowaną przez `[TestCleanup]` atrybut, która uruchamia kod na końcu każdej metody testowej. Na przykład metoda zamknięcia aplikacji może być wywoływana z TestCleanup metody.

## <a name="validate-the-properties-of-ui-controls"></a>Sprawdzanie poprawności właściwości formantów interfejsu użytkownika

**Konstruktora testów interfejsu użytkownika kodowany** służy do dodawania formantu interfejsu użytkownika do [interfejsu użytkownika](/previous-versions/dd580454(v=vs.140)) dla testu lub do generowania kodu dla metody sprawdzania poprawności, która używa potwierdzenia dla formantu interfejsu użytkownika.

Aby wygenerować potwierdzenia dla **formantów** interfejsu użytkownika, wybierz narzędzie Dodaj potwierdzenia w **konstruktorze testów kodowanych interfejsów użytkownika** i przeciągnij je do formantu w testowej aplikacji, którą chcesz sprawdzić, czy jest poprawna. Gdy pole przedstawia formant, zwolnij mysz. Kod klasy formantu jest natychmiast tworzony w pliku *UIMap.Designer.cs.*

![Zakodowany element kierowania testu interfejsu użytkownika](../test/media/codedui_1.png)

Właściwości tego formantu są teraz wymienione w oknie dialogowym **Dodawanie potwierdzeń.**

Innym sposobem przechodzenia do określonego formantu jest wybranie strzałki **(<<),** aby rozwinąć widok mapy **sterowania interfejsu użytkownika**. Aby znaleźć kontrolkę nadrzędną, równorzędną lub podrzędną, możesz kliknąć dowolne miejsce na mapie i poruszać się po drzewie za pomocą klawiszy strzałek.

![Zakodowane właściwości testu interfejsu użytkownika](../test/media/codedui_2.png)

> [!TIP]
> Jeśli nie widzisz żadnych właściwości po wybraniu formantu w aplikacji lub nie widzisz formantu w mapie sterowania interfejsu użytkownika, sprawdź, czy formant ma unikatowy identyfikator w kodzie aplikacji. Unikatowy identyfikator może być atrybutem identyfikatora HTML lub identyfikatorem UId WPF.

Następnie otwórz menu skrótów we właściwości formantu interfejsu użytkownika, który chcesz zweryfikować, a następnie wskaż polecenie **Dodaj asercja**. W oknie dialogowym **Dodawanie potwierdzenia** wybierz na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> **komparator** dla potwierdzenia i wpisz wartość potwierdzenia w **polu Wartość porównania**.

![Zakodowane potwierdzenia testu interfejsu użytkownika](../test/media/codedui_3.png)

Po dodaniu wszystkich potwierdzeń do testu wybierz przycisk **OK**.

Aby wygenerować kod dla potwierdzeń i dodać formant do mapy interfejsu użytkownika, wybierz ikonę **Generuj kod.** Wpisz nazwę metody testu kodowany interfejs użytkownika i opis metody, która zostanie dodana jako komentarze do metody. Wybierz **pozycję Dodaj i wygeneruj**. Następnie wybierz ikonę **Zamknij,** aby zamknąć **konstruktora testów interfejsu użytkownika kodowane**. Spowoduje to wygenerowanie kodu podobnego do następującego kodu. Na przykład, jeśli wprowadzona `AssertForAddTwoNumbers`nazwa jest , kod będzie wyglądać w tym przykładzie:

- Dodaje wywołanie metody assert AssertForAddTwoNumbers do metody testowej w pliku testowym kodowany interfejs użytkownika:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Można edytować ten plik, aby zmienić kolejność kroków i potwierdzeń lub utworzyć nowe metody testowania. Aby dodać więcej kodu, umieść kursor w metodzie testowej i w menu skrótów wybierz polecenie **Generuj kod dla kodowany test interfejsu użytkownika**.

- Dodaje metodę `AssertForAddTwoNumbers` wywoływaną do mapy interfejsu użytkownika (*UIMap.uitest*). Ten plik zostanie otwarty w **Edytorze kodowanych testów interfejsu użytkownika,** w którym można edytować potwierdzenia.

     ![Edytuj potwierdzanie przy użyciu edytora testów kodowanych interfejsu użytkownika](../test/media/cuit_editor_assert.png)

     Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika przy użyciu edytora testów kodowany interfejs użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Można również wyświetlić wygenerowany kod metody potwierdzenia w *UIMap.Designer.cs*. Nie należy jednak edytować tego pliku. Jeśli chcesz stworzyć dostosowaną wersję kodu, skopiuj metody do innego pliku, takiego jak *UIMap.cs*, zmień nazwę metody i edytuj je tam.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Wybieranie ukrytego formantu za pomocą klawiatury

Jeśli formant, który chcesz wybrać, traci fokus i znika po wybraniu narzędzia **Dodaj potwierdzenia** z **konstruktora testów kodowanych interfejsów użytkownika:**

Czasami podczas dodawania formantów i weryfikowania ich właściwości może być trzeba użyć klawiatury. Na przykład podczas próby nagrywania kodowany test interfejsu użytkownika, który używa formantu menu po kliknięciu prawym przyciskiem myszy, lista elementów menu w formancie straci fokus i zniknie podczas próby **wybrania** narzędzia Dodaj potwierdzenia z **Konstruktora testów interfejsu użytkownika kodowane**. Jest to pokazane na poniższej ilustracji, gdzie menu prawym przyciskiem myszy w programie Internet Explorer traci fokus i znika, jeśli spróbujesz go **zaznaczyć** za pomocą narzędzia Dodaj potwierdzenia.

![&#95;tablica kodu&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Aby wybrać kontrolkę interfejsu użytkownika za pomocą klawiatury, umieść wskaźnik myszy nad formantem. Następnie przytrzymaj klawisz **Ctrl** i klawisz **I** w tym samym czasie. Zwolnij klawisze. Formant jest rejestrowany przez **coded UI Test Builder**.

#### <a name="manually-record-mouse-hovers"></a>Ręczne rejestrowanie kursorów myszy

Jeśli nie możesz nagrać wskaźnika myszy na formancie:

W pewnych okolicznościach określonego formantu, który jest używany w teście kodowany interfejsu użytkownika może wymagać użycia klawiatury do ręcznego rejestrowania zdarzeń myszy aktywować. Na przykład podczas testowania formularza systemu Windows lub aplikacji Windows Presentation Foundation (WPF), może istnieć kod niestandardowy. Lub może istnieć specjalne zachowanie zdefiniowane do najechania na formant, takich jak węzeł drzewa rozwija się, gdy użytkownik najedzie nad nim. Aby przetestować takie okoliczności, należy ręcznie powiadomić **konstruktora kodowanych testów interfejsu użytkownika,** że najechasz kursorem na kontrolki, naciskając wstępnie zdefiniowane klawisze klawiatury.

Podczas wykonywania testu kodowany interfejs użytkownika, umieść wskaźnik myszy na formancie. Następnie naciśnij i przytrzymaj **klawisz Ctrl**, naciskając i przytrzymaj klawisze **Shift** i **R** na klawiaturze. Zwolnij klawisze. Zdarzenie aktywowania myszy jest rejestrowane przez **konstruktora testów kodowanych interfejsu użytkownika**.

![Hover&#95;&#95;Kodu](../test/media/codedui_hover.png)

Po wygenerowaniu metody testowej kod podobny do następującego przykładu zostanie dodany do pliku *UIMap.Designer.cs:*

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurowanie przypisań klawiatury kursoru myszy

Jeśli przypisanie klawiszy do przechwytywania zdarzeń aktywowania myszy jest używane w innym miejscu w moim środowisku:

W razie potrzeby domyślne przypisanie klawiatury **Ctrl**+**Shift**+**R,** który jest używany do stosowania zdarzeń myszy hover w kodowanych testów interfejsu użytkownika można skonfigurować do używania różnych klawiszy.

> [!WARNING]
> Nie należy zmieniać przypisań klawiatury dla zdarzeń aktywowania myszy w zwykłych okolicznościach. Podczas ponownego przypisywania przypisania klawiatury należy zachować ostrożność. Wybór może być już używany w innym miejscu w programie Visual Studio lub testowana aplikacja.

Aby zmienić przypisania klawiatury, zmodyfikuj następujący plik konfiguracyjny:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

W pliku konfiguracyjnym `HoverKeyModifier` zmień `HoverKey` wartości klawiszy i klawiszy, aby zmodyfikować przypisania klawiatury:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Ustawianie niejawnych najeżdżanych myszy dla przeglądarki internetowej

Jeśli masz problemy z nagrywaniem myszy kursorów na stronie internetowej:

W wielu witrynach sieci Web po umieszczeniu wskaźnika myszy na określonym formancie rozwija się, aby wyświetlić dodatkowe szczegóły. Ogólnie rzecz biorąc, wyglądają one jak menu w aplikacjach klasycznych. Ponieważ jest to typowy wzorzec, testy kodowany interfejsu użytkownika włączyć niejawne hovers do przeglądania sieci Web. Na przykład jeśli rekord zostanie najechany w programie Internet Explorer, zdarzenie zostanie podpalone. Zdarzenia te mogą prowadzić do nadmiaru najechań kursorów coraz rejestrowane. Z tego powodu niejawne `ContinueOnError` hovers `true` są rejestrowane z zestawem w pliku konfiguracji testu interfejsu użytkownika. Dzięki temu odtwarzanie jest kontynuowane w przypadku niepowodzenia zdarzenia aktywowania.

Aby włączyć rejestrowanie niejawnych najechań kursorów w przeglądarce internetowej, otwórz plik konfiguracyjny:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Sprawdź, czy w pliku `RecordImplicitiHovers` konfiguracyjnym klucz ma ustawioną `true` wartość, jak pokazano w poniższym przykładzie:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Dostosowywanie testu kodowany interfejs użytkownika

Po utworzeniu testu kodowany interfejs użytkownika, można edytować go przy użyciu dowolnego z następujących narzędzi w programie Visual Studio:

- Użyj **Konstruktora testów interfejsu użytkownika kodowane,** aby dodać dodatkowe formanty i sprawdzanie poprawności do testów. Zobacz sekcję [Dodawanie formantów i sprawdzanie poprawności ich właściwości](#validate-the-properties-of-ui-controls) w tym temacie.

- **Edytor kodowanych testów interfejsu użytkownika** umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą **Edytora testów kodowanych interfejsu**użytkownika można zlokalizować, wyświetlić i edytować metody testowe. Akcje interfejsu użytkownika i skojarzone z nimi formanty można również edytować na mapie sterowania interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika przy użyciu edytora testów kodowany interfejs użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Edytor kodu:**

  - Ręcznie dodaj kod formanty w teście, zgodnie z opisem w [coded ui kontroli akcji i właściwości](#coded-ui-control-actions-and-properties) sekcji w tym temacie.

  - Po utworzeniu testu kodowany interfejs użytkownika, można zmodyfikować go do danych. Aby uzyskać więcej informacji, zobacz [Tworzenie opartego na danych testu kodowego interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md).

  - W kodowany interfejs użytkownika odtwarzania testu, można poinstruować test czekać na pewne zdarzenia wystąpią, takie jak okno, aby pojawić się, pasek postępu zniknąć i tak dalej. Aby to zrobić, należy dodać odpowiednią metodę UITestControl.WaitForControlXXX(). Aby uzyskać pełną listę dostępnych metod, [zobacz, aby kodowane testy interfejsu użytkownika czekały na określone zdarzenia podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Na przykład kodowany test interfejsu użytkownika, który czeka na formant, który ma być włączony przy użyciu WaitForControlEnabled metody, zobacz [Instruktaż: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5, które są zawarte w programach Internet Explorer 9 i Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [Używanie formantów HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).

  - Kodowane wskazówki dotyczące kodowania testu interfejsu użytkownika:

    - [Anatomia zakodowany test interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)

    - [Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)

    - [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Wygenerowany kod

Po **wybraniu opcji Generuj kod**tworzonych jest kilka fragmentów kodu:

- Linia w metodzie testowej.

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

     Możesz kliknąć tę metodę prawym przyciskiem myszy, aby dodać więcej zarejestrowanych akcji i weryfikacji. Można również edytować ręcznie, aby rozszerzyć lub zmodyfikować kod. Na przykład można ująć niektóre kodu w pętli.

     Można również dodać nowe metody testowania i dodać do nich kod w ten sam sposób. Każda metoda testowa `[TestMethod]` musi mieć atrybut.

- Metoda w *UIMap.uitest*.

     Ta metoda zawiera szczegóły akcji, które zostały zarejestrowane lub wartość, która została zweryfikowana. Możesz edytować ten kod, otwierając *UIMap.uitest*. Otwiera się w wyspecjalizowanym edytorze, w którym można usunąć lub refaktoryzować zarejestrowane akcje.

     Można również wyświetlić wygenerowaną metodę w *UIMap.Designer.cs*. Ta metoda wykonuje akcje, które zostały zarejestrowane po uruchomieniu testu.

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
    > Nie należy edytować ten plik, ponieważ zostanie on ponownie wygenerowany podczas tworzenia większej liczby testów.

     Można tworzyć dostosowane wersje tych metod, kopiując je w *celu UIMap.cs*. Na przykład można wprowadzić sparametryzowaną wersję, którą można wywołać z metody testowej:

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

    Te deklaracje reprezentują formanty interfejsu użytkownika aplikacji, które są używane przez test. Są one używane przez wygenerowany kod do obsługi formantów i dostępu do ich właściwości.

    Można ich również użyć, jeśli piszesz swój własny kod. Na przykład metoda testowa może wybrać hiperłącze w aplikacji sieci web, wpisać wartość w polu tekstowym lub odgałęzić i podjąć różne akcje testowania na podstawie wartości w polu.

    Można dodać wiele kodowanych testów interfejsu użytkownika i wiele obiektów i plików mapy interfejsu użytkownika, aby ułatwić testowanie dużej aplikacji. Aby uzyskać więcej informacji, zobacz [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md).

Aby uzyskać więcej informacji na temat wygenerowanego kodu, zobacz [Anatomia zakodowany test interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Zakodowane akcje kontroli interfejsu użytkownika i właściwości

Podczas pracy z formantami testu interfejsu użytkownika w testach interfejsu użytkownika kodowane są one podzielone na dwie części: akcje i właściwości.

- Pierwsza część składa się z akcji, które można wykonać na formanty testu interfejsu użytkownika. Na przykład testy kodowanego interfejsu użytkownika mogą symulować kliknięcia myszy na formancie testu interfejsu użytkownika lub symulować klawisze wpisane na klawiaturze, aby wpłynąć na formant testu interfejsu użytkownika.

- Druga część składa się z umożliwienia uzyskania i ustawić właściwości na kontrolki testu interfejsu użytkownika. Na przykład testy kodowany interfejs użytkownika można uzyskać `ListBox`liczbę elementów w , lub ustawić do `CheckBox` wybranego stanu.

**Uzyskiwanie dostępu do akcji kontroli testu interfejsu użytkownika**

Aby wykonać akcje na formanty testu interfejsu użytkownika, takie jak <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> kliknięcia myszą lub akcje klawiatury, należy użyć metod w i <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> klas:

- Aby wykonać akcję zorientowaną na myszy, taką jak kliknięcie myszą, na formancie testu interfejsu użytkownika użyj . <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>

     `Mouse.Click(buttonCancel);`

- Aby wykonać akcję zorientowaną na klawiaturę, na przykład <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>wpisując formant edycji, użyj programu .

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Uzyskiwanie dostępu do właściwości formantu testu interfejsu użytkownika**

Aby uzyskać i ustawić wartości właściwości określonego sterowania interfejsu użytkownika, można bezpośrednio uzyskać lub ustawić wartości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> właściwości formantu lub można użyć i metody z nazwą określonej właściwości, które chcesz uzyskać lub ustawić.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>zwraca obiekt, który następnie można rzutować na odpowiedni <xref:System.Type>plik . <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>przyjmuje obiekt dla wartości nieruchomości.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Aby uzyskać lub ustawić właściwości bezpośrednio z formantów testu interfejsu użytkownika

Za pomocą formantów, które wynikają z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, takich jak [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) lub [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), można uzyskać lub ustawić ich wartości właściwości bezpośrednio. Poniższy kod zawiera kilka przykładów:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z formantów testu interfejsu użytkownika

- Aby uzyskać wartość właściwości z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>formantu, użyj .

- Aby określić właściwość formantu, aby uzyskać, należy użyć odpowiedniego ciągu z `PropertyNames` klasy w każdym formancie jako parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>zwraca odpowiedni typ danych, ale ta zwracana wartość jest rzutowana jako . <xref:System.Object> Return <xref:System.Object> musi być następnie rzutowy jako odpowiedni typ.

     Przykład:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości dla kontrolek testu interfejsu użytkownika

- Aby ustawić właściwość w <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>formancie, należy użyć programu .

- Aby określić właściwość formantu, aby ustawić, należy użyć odpowiedniego ciągu z `PropertyNames` klasy jako pierwszy parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, z wartością właściwości jako drugi parametr.

     Przykład:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Debugowanie

Można analizować kodowane testy interfejsu użytkownika przy użyciu dzienników testów interfejsu użytkownika kodowane. Kodowane dzienniki testów interfejsu użytkownika filtrują i rejestrują ważne informacje o przebiegach testu kodowany interfejs użytkownika. Format dzienników umożliwia szybkie debugowanie problemów. Aby uzyskać więcej informacji, zobacz [Analizowanie zakodowanych testów interfejsu użytkownika przy użyciu kodowanych dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co dalej?

::: moniker range="vs-2017"
**Dodatkowe opcje uruchamiania kodowanych testów interfejsu użytkownika:** Można uruchomić kodowane testy interfejsu użytkownika bezpośrednio z programu Visual Studio, zgodnie z opisem wcześniej w tym temacie. Ponadto można uruchomić zautomatyzowane testy interfejsu użytkownika z menedżera testów firmy Microsoft lub przy użyciu potoków platformy Azure. Gdy testy interfejsu użytkownika kodowane są zautomatyzowane, muszą one współdziałać z pulpitu po uruchomieniu ich, w przeciwieństwie do innych testów automatycznych.
::: moniker-end
::: moniker range=">=vs-2019"
**Dodatkowe opcje uruchamiania kodowanych testów interfejsu użytkownika:** Można uruchomić kodowane testy interfejsu użytkownika bezpośrednio z programu Visual Studio, zgodnie z opisem wcześniej w tym temacie. Ponadto można uruchomić zautomatyzowane testy interfejsu użytkownika przy użyciu usługi Azure Potoki. Gdy testy interfejsu użytkownika kodowane są zautomatyzowane, muszą one współdziałać z pulpitu po uruchomieniu ich, w przeciwieństwie do innych testów automatycznych.
::: moniker-end

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)

- [Uruchamianie testów w procesie kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Jak: Konfigurowanie agenta testowego do uruchamiania testów, które wchodzą w interakcję z pulpitem](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Dodawanie obsługi formantów niestandardowych:**  Struktura testowania kodowanych interfejsu użytkownika nie obsługuje wszystkich możliwych interfejsu użytkownika i może nie obsługiwać interfejsu użytkownika, który chcesz przetestować. Na przykład nie można natychmiast utworzyć kodowany test interfejsu użytkownika interfejsu użytkownika dla programu Microsoft Excel. Można jednak utworzyć rozszerzenie do struktury testowania kodowanych interfejsu użytkownika, która obsługuje formant niestandardowy.

- [Włącz kodowane testowanie formantów interfejsu użytkownika](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Kodowane testy interfejsu użytkownika są często używane do automatyzacji testów ręcznych. Aby uzyskać więcej informacji na temat testów automatycznych, zobacz [Narzędzia testowe w programie Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Zobacz też

- [Nagrywanie i odtwarzanie testów ręcznych](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Test platformy Xamarin.UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Instruktaż: Tworzenie, edytowanie i obsługa testu kodowany interfejs użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Tworzenie zakodowany test interfejsu użytkownika, aby przetestować aplikację platformy uniwersalnej systemu i platformy uniwersalnej](test-uwp-app-with-coded-ui-test.md)
- [Anatomia testu kodowany interfejs użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
