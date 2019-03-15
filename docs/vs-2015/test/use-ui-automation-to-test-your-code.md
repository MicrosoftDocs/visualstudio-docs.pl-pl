---
title: Używanie automatyzacji interfejsu użytkownika do testowania kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
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
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92d59e722b78e389bf355eeac8a1aa267979fc5b
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873861"
---
# <a name="use-ui-automation-to-test-your-code"></a>Używanie automatyzacji interfejsu użytkownika do testowania kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy automatyczne, które kontrolują aplikację przez jej interfejs użytkownika (UI) są znane jako *kodowane testy interfejsu użytkownika* (CUITs). Te testy obejmują, aplikacja jest funkcjonalna kontrolek interfejsu użytkownika. Umożliwiają one możesz sprawdzić, czy całej aplikacji, w tym interfejs użytkownika działa poprawnie. Kodowane testy interfejsu użytkownika są szczególnie przydatne, gdy sprawdzanie poprawności lub inna logika interfejsu użytkownika, na przykład na stronie sieci web. Są one również często używane do automatyzowania istniejącego testu ręcznego.

 Jak pokazano na poniższej ilustracji, w środowisku projektowym typowe może być where, początkowo wystarczy skompilować aplikację (F5) i kliknij przycisk za pomocą kontrolek interfejsu użytkownika, aby sprawdzić, czy wszystko działa poprawnie. Użytkownik może zdecydować się utworzyć kodowany test, dzięki czemu nie trzeba ręcznie przetestować aplikację w dalszym ciągu. W zależności od konkretnej funkcji testowane w aplikacji można napisać kod dla funkcjonalności testu lub test integracji, który może być lub może nie zawierać testowania na poziomie interfejsu użytkownika. Jeśli po prostu chcesz uzyskać bezpośredni dostęp do niektórych logiki biznesowej, może być kodu testu jednostkowego. Jednak w pewnych okolicznościach może być korzystne uwzględnić testowania różnych kontrolek interfejsu użytkownika w aplikacji. Kodowany test interfejsu użytkownika można zautomatyzować początkowej scenariusza (F5), sprawdzający, czy ten postęp dokonany w kodzie nie ma wpływu na funkcjonalność aplikacji.

 ![Testowanie podczas tworzenia aplikacji](../test/media/cuit-overview.png "CUIT_Overview")

 Tworzenie kodowanego testu interfejsu użytkownika jest proste. Możesz po prostu ręcznego wykonywania testu podczas konstruktora testu CUIT działa w tle. Można również określić, jakie wartości powinna zostać wyświetlona w określonych polach. Konstruktor testu CUIT rejestruje swoje działania i generuje kod z nich. Po utworzeniu testu można edytować go w edytorze specjalistyczne, która umożliwia modyfikowanie sekwencję akcji.

 Alternatywnie Jeśli przypadek testowy, który został zarejestrowany w programie Microsoft Test Manager, istnieje możliwość wygenerowania kodu przy jego użyciu. Aby uzyskać więcej informacji, zobacz [rekordu i odtwarzać ponownie ręcznych testów](/azure/devops/test/mtm/record-play-back-manual-tests).

 Konstruktor testu CUIT wyspecjalizowanych i Edytor ułatwiają tworzenie i edytowanie kodowanych testów interfejsu użytkownika, nawet wtedy, gdy umiejętności w zakresie głównym jest skoncentrowana testowania zamiast kodowania. Ale jeśli jesteś deweloperem i chcesz rozszerzyć test w sposób bardziej zaawansowane, kod mają strukturę, aby był prosty skopiować i dostosowania. Na przykład Nagraj test do zakupu w witrynie sieci Web, a następnie edytuj wygenerowany kod, aby dodać pętlę, która kupuje się wiele elementów.

 **Wymagania**

- Visual Studio Enterprise

  Aby uzyskać więcej informacji o tym, które platformy i konfiguracje są obsługiwane przez kodowane testy interfejsu użytkownika, zobacz [obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

  **W tym temacie**

- [Tworzenie kodowanych testów interfejsu użytkownika](#VerifyingCodeUsingCUITCreate)

  -   [Główne procedury](#VerifyingCodeUsingCUITCreate)

  -   [Uruchamianie i zatrzymywanie aplikacji](#starting)

  -   [Sprawdzanie poprawności właściwości formantów interfejsu użytkownika](#VerifyingCodeUsingCUITGenerateAssertions)

- [Dostosowywanie kodowanego testu interfejsu użytkownika](#VerifyingCodeCUITModify)

  -   [Wygenerowany kod](#generatedCode)

  -   [Kodowanie akcji kontrolki UI oraz właściwości](#actions)

  -   [Debugowanie](#debugging)

- [Jaka jest przyszłość](#VerifyCodeUsingCUITWhatsNext)

##  <a name="VerifyingCodeUsingCUITCreate"></a> Tworzenie kodowanych testów interfejsu użytkownika

1. **Utwórz projekt kodowanego testu interfejsu użytkownika.**

    Kodowane testy interfejsu użytkownika musi być zawarty w projekt kodowanego testu interfejsu użytkownika. Jeśli nie masz jeszcze projektu kodowanego testu interfejsu użytkownika, zrób to. W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt** a następnie wybierz opcję **języka Visual Basic** lub **Visual C#**. Następnie wybierz pozycję **testu**, **kodowanego testu interfejsu użytkownika**.

   - <em>Nie widzę **kodowanego testu interfejsu użytkownika</em>* szablony projektów.*

      Być może używasz wersji programu Visual Studio, który nie obsługuje kodowanych testów interfejsu użytkownika. Aby utworzyć kodowane testy interfejsu użytkownika, należy użyć programu Visual Studio Enterprise.

2. **Dodaj plik kodowanego testu interfejsu użytkownika.**

    Jeśli właśnie utworzone projektu kodowanego interfejsu użytkownika, pierwszy plik CUIT jest automatycznie dodawany. Aby dodać inny plik testowy, otwórz menu skrótów projektu kodowanego testu interfejsu użytkownika, wskaż opcję **Dodaj**, a następnie wybierz **kodowanego testu interfejsu użytkownika**.

    ![Tworzenie kodowanego testu interfejsu użytkownika](../test/media/codedui-create.png "CodedUI_Create")

    W **Generuj kod dla kodowanego testu interfejsu użytkownika** okna dialogowego wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia**.

    ![Wybierz pozycję Zarejestruj akcje](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")

    Konstruktor kodowanego testu interfejsu użytkownika jest wyświetlany, i Visual Studio jest zminimalizowany.

    ![Konstruktor kodowanego testu interfejsu użytkownika](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")

3. **Zarejestruj sekwencję akcji**.

    **Aby rozpocząć rejestrowanie**, wybierz **rekordu** ikony. Wykonywanie akcji, które mają zostać przetestowane w aplikacji, w tym uruchamianie aplikacji, jeśli jest to wymagane.

    Na przykład jeśli testujesz aplikację sieci web możesz może uruchamiają przeglądarkę, przejdź do witryny sieci web i zaloguj się do aplikacji.

    **Aby Wstrzymaj nagrywanie**, na przykład jeśli masz do czynienia z przychodzących wiadomości e-mail, wybierz **wstrzymać**.

   > [!WARNING]
   >  Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, jeśli są wykonywane działania, które mogą prowadzić do danych poufnych jest zawarty w nagraniu.

    **Można usunąć akcji** zapisane przez pomyłkę, wybierz polecenie **edytować akcje**.

    **Do generowania kodu** , będzie replikowanie Twoje działania, wybierz **Generuj kod** ikonę i wpisz nazwę i opis dla kodowanego interfejsu użytkownika metoda testowa.

4. **Sprawdź wartości w polach interfejsu użytkownika, takie jak pola tekstowe**.

    Wybierz **dodawania potwierdzeń** w kodowanego testu interfejsu użytkownika, a następnie wybierz kontrolkę interfejsu użytkownika w uruchomionej aplikacji. Pojawia się liście właściwości wybierz właściwość, na przykład **tekstu** w polu tekstowym. W menu skrótów wybierz **Dodaj potwierdzenie**. W oknie dialogowym Wybierz operator porównania, wartość porównania i komunikat o błędzie.

    Zamknij okno potwierdzenia, a następnie wybierz **Generuj kod**.

    ![Kodowany test interfejsu użytkownika, przeznaczonych dla elementu](../test/media/codedui-1.png "CodedUI_1")

   > [!TIP]
   >  Przełącza między rejestrowanie akcji i weryfikowanie wartości. Generowanie kodu na końcu każdego sekwencję akcji lub weryfikacji. Jeśli chcesz, będzie można później Wstaw nowe akcje i weryfikacji.

    Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności właściwości formantów](#VerifyingCodeUsingCUITGenerateAssertions).

5. **Wyświetl kod wygenerowany test**.

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

6. **Dodawanie więcej akcji i potwierdzenia**.

    Umieść kursor we właściwym miejscu w metodzie testowej, a następnie w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**. Nowy kod zostanie wstawiony w tym momencie.

7. **Edytuj szczegóły działań testów i potwierdzenia**.

    Otwórz UIMap.uitest. Ten plik zostanie otwarty w interfejsie użytkownika edytora kodowanego testu, gdzie można edytować dowolnej sekwencji akcji, które nagrałeś oraz jak edytować swoje potwierdzenia.

    ![Edytor testu interfejsu użytkownika kodowany](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")

    Aby uzyskać więcej informacji, zobacz [testy interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. **Uruchom test**.

    Eksplorator testów lub Otwórz menu skrótów w metodzie testowej, a następnie wybierz **Uruchom testy**. Aby uzyskać więcej informacji o sposobach uruchamiania testów, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika* w [co przyniesie przyszłość?](#VerifyCodeUsingCUITWhatsNext) sekcji w zakończenie tego tematu.

   Pozostałe sekcje w tym temacie więcej szczegółowych informacji o krokach w tej procedurze.

   Aby uzyskać bardziej szczegółowym przykładem, zobacz [instruktażu: Tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W instruktażu utworzysz prostą aplikację Windows Presentation Foundation (WPF) w celu zademonstrowania sposobu tworzenia, edytowania i obsługa kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

###  <a name="starting"></a> Uruchamianie i zatrzymywanie testowaną aplikację
 *Nie chcę uruchomić i zatrzymać mojej aplikacji, przeglądarki lub bazy danych oddzielnie dla każdego testu. Jak uniknąć,?*

-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") Jeśli nie chcesz Rejestruj akcje, które można uruchomić Twojej aplikacji poddawanej testom, należy uruchomić aplikację przed wybraniem **rekordu** ikony.

-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik")na końcu testu, proces, w którym przeprowadzany jest test zostanie zakończony. Jeśli aplikacja jest uruchomiona w teście, zwykle powoduje zamknięcie aplikacji.  Jeśli użytkownik nie chce test, aby zamknąć aplikację, kiedy wychodzi, należy dodać plik .runsettings do rozwiązania i użyj `KeepExecutorAliveAfterLegacyRun` opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") można dodać metodę initialize badania identyfikowany przez atrybut [TestInitialize], która uruchamia kod na początku każdej metody testowej. Na przykład można uruchomić aplikacji z metody TestInitialize.

-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") można dodać metoda czyszcząca testu, identyfikowany przez atrybut [TestCleanup], która uruchamia kod na końcu każdej metody testowej. Na przykład metody, aby zamknąć aplikację może być wywołana z metoda TestCleanup.

###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a> Sprawdzanie poprawności właściwości formantów interfejsu użytkownika
 Możesz użyć **Konstruktor kodowanego testu IU** można dodać kontrolki interfejsu użytkownika do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> dla testu lub do generowania kodu dla metody sprawdzania poprawności, który używa potwierdzenie dla kontrolki interfejsu użytkownika.

 Aby wygenerować potwierdzenia dla Twoich kontrolek interfejsu użytkownika, wybierz opcję **dodawania potwierdzeń** narzędzia Konstruktor kodowanego testu IU i przeciągnij go do formantu w aplikacji poddawanej testowi, który chcesz zweryfikować jest poprawna. Gdy pole zawiera opis kontrolki, zwolnij przycisk myszy. Kod klasy formantu natychmiast jest tworzony w `UIMap.Designer.cs` pliku.

 ![Kodowany test interfejsu użytkownika, przeznaczonych dla elementu](../test/media/codedui-1.png "CodedUI_1")

 Właściwości dla tego formantu są wyświetlane w **dodawania potwierdzeń** okno dialogowe.

 Inny sposób przejścia do określonego formantu jest wybierz strzałkę **(<<)** rozszerzania widok **mapy formantów UI**. Aby znaleźć nadrzędnego, element równorzędny lub kontrolki podrzędnej, możesz kliknij w dowolnym miejscu na mapie i używaj klawiszy strzałek Aby poruszać się po drzewie.

 ![Kodowanego testu interfejsu użytkownika właściwości](../test/media/codedui-2.png "CodedUI_2")

- *Nie widzisz żadnych właściwości, gdy mogę wybrać kontrolkę w mojej aplikacji lub nie jest wyświetlane na formant mapy formantów interfejsu użytkownika.*

   W kodzie aplikacji formant, który chcesz zweryfikować musi mieć unikatowy identyfikator, takie jak atrybutu HTML Identyfikatora lub WPF UId. Może być konieczne zaktualizowanie kodu aplikacji w celu dodania tych identyfikatorów.

  Następnie otwórz menu skrótów dla właściwości do kontrolki interfejsu użytkownika, który chcesz sprawdzić, a następnie wskaż **Dodaj potwierdzenie**. W **Dodaj potwierdzenie** okno dialogowe, wybierz opcję **Komparator** do potwierdzenia, na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, a następnie wpisz wartość dla Twojego potwierdzenia w **porównywana wartość**.

  ![Kodowanego testu interfejsu użytkownika potwierdzenia](../test/media/codedui-3.png "CodedUI_3")

  Po dodaniu wszystkich asercje o dla testu wybierz **OK**.

  Aby wygenerować kod dla potwierdzenia usługi i Dodaj formant do mapy interfejsu użytkownika, wybierz **Generuj kod** ikony. Wpisz nazwę metodę kodowanego testu interfejsu użytkownika i opis metody, które zostaną dodane jako komentarze do metody. Wybierz **Dodaj i wygeneruj**. Następnie wybierz pozycję **Zamknij** ikoną, aby zamknąć **kodowanego testu interfejsu użytkownika**. Spowoduje to wygenerowanie kodu podobne do następującego kodu. Na przykład, jeśli wprowadzona nazwa jest `AssertForAddTwoNumbers`, kod będzie wyglądać następująco:

- Dodaje wywołanie metody assert AssertForAddTwoNumbers do metody testowej w pliku kodowanego testu interfejsu użytkownika:

  ```
  [TestMethod]
  public void CodedUITestMethod1()
  {
      this.UIMap.AddTwoNumbers();
      this.UIMap.AssertForAddTwoNumbers();
  }
  ```

   Możesz edytować ten plik, aby zmienić kolejność kroków i potwierdzenia lub tworzenie nowych metod testowych. Aby dodać więcej kodu, umieść kursor na metodzie testowej, jak i w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**.

- Dodaje metodę o nazwie `AssertForAddTwoNumbers` do mapy interfejsu użytkownika (UIMap.uitest). Ten plik zostanie otwarty w interfejsie użytkownika edytora kodowanego testu, którym można edytować potwierdzenia.

   ![Edytuj assert, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")

   Aby uzyskać więcej informacji, zobacz [testy interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

   Można również wyświetlić wygenerowany kod metody asercji w UIMap.Designer.cs. Jednak nie należy edytować ten plik. Aby dostosować wersję kodu kopiowanie metody do innego pliku, takie jak UIMap.cs, Zmień nazwę metody i tam edytować.

  ```
  public void AssertForAddTwoNumbers()
  {
      ...
  }
  ```

  *Formant, który chcę wybrać traci fokus i znika przy próbie wybierz narzędzie Dodaj Asercje z konstruktora kodowanego testu interfejsu użytkownika. Jak wybrać formant? * 
   **Wybierając ukrytą kontrolkę za pomocą klawiatury**

  Czasami, gdy [dodawanie formantów i weryfikowania ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions), może być konieczne użycie klawiatury. Na przykład podczas próby rejestrowania kodowanego testu interfejsu użytkownika, używającej formant menu kontekstowego na liście elementów menu w formancie utracić fokus i znikają w przypadku próby wybierz narzędzie Dodaj Asercje z Konstruktor kodowanego testu IU. Zostało to przedstawione na poniższej ilustracji, gdzie tracić fokus i znika, jeśli zostanie podjęta próba wybierz ją przy użyciu narzędzia Dodaj Asercje przez menu kontekstowego w programie Internet Explorer.

  ![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

  Aby użyć klawiatury, aby wybrać kontrolkę interfejsu użytkownika, umieść kursor nad kontrolką za pomocą myszy. Wciśnij klawisz **Ctrl** klucza i **I** klucza w tym samym czasie. Wydawanie kluczy. Kontrolka jest rejestrowana przez konstruktora kodowanego testu UT.

> [!WARNING]
>  Jeśli używasz Microsoft Lync, należy zamknąć Lync, przed rozpoczęciem korzystania z konstruktora kodowanego testu interfejsu użytkownika. Microsoft Lync zakłóca **Ctrl + I** skróty klawiaturowe.

 *Nie można zarejestrować umieść kursor myszy na kontrolce. Czy istnieje rozwiązanie tego problemu?*
 **Ręcznie wskaźnika myszy nagrywanie**

 W niektórych okolicznościach określonego formantu, który jest używany w coded UI test może wymagać użycia klawiatury do zdarzenia po wskazaniu wskaźnikiem myszy ręcznie rekordów. Na przykład podczas testowania formularza Windows lub aplikacji Windows Presentation Foundation (WPF), może być kod niestandardowy. Lub może być specjalnego zachowania zdefiniowane dla przenosząc kursor myszy nad formant, takich jak rozwijanie, gdy użytkownik zatrzyma na niej węzła drzewa. Aby przetestować okoliczności, takie jak te, musisz ręcznie otrzymywać powiadomienia, Konstruktor kodowanego testu IU który kursor myszy nad formantem, naciskając klawisz wstępnie zdefiniowane klawisze klawiatury.

 Podczas wykonywania kodowanego testu interfejsu użytkownika, umieść kursor nad kontrolką. Naciśnij i przytrzymaj klawisz Ctrl, naciśnij i przytrzymaj klawisze Shift i języka R na klawiaturze. Wydawanie kluczy. Zdarzenia myszy po wskazaniu wskaźnikiem są rejestrowane przez konstruktora kodowanego testu UT.

 ![CodedUI&#95;Hover](../test/media/codedui-hover.png "CodedUI_Hover")

 Po wygenerowaniu metody testowej kod podobny do poniższego przykładu zostaną dodane do pliku UIMap.Desinger.cs:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));

```

 *Przypisanie klucza do przechwytywania zdarzeń po wskazaniu wskaźnikiem myszy jest używana gdzie indziej w mojej środowisku. Czy mogę zmienić domyślne przypisanie klucza*
 **Konfigurowanie przypisań klawiatury po wskazaniu wskaźnikiem myszy**

 Jeśli to konieczne, można skonfigurować domyślne przypisanie klawiatura Ctrl + Shift + R, który służy do stosowania aktywowania zdarzeń myszy w kodowanych testach interfejsu użytkownika do używania różnych kluczy.

> [!WARNING]
>  Zmień przypisania klawiatury dla zdarzeń po wskazaniu wskaźnikiem myszy w zwykłych okolicznościach nie powinna mieć. Ponowne przypisywanie przypisania klawiatury, należy zachować ostrożność. Wybór mogą być już używany w ramach programu Visual Studio lub aplikacja poddawana testom.

 Aby zmienić przypisania klawiatury, należy zmodyfikować następującego pliku konfiguracji:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 W pliku konfiguracji, zmień wartości `HoverKeyModifier` i `HoverKey` klucze do modyfikowania przydziałów klawiatury:

```
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>

```

 *Mam problemy z rejestrowanie ruchów myszy w witrynie internetowej. Jest rozwiązaniem w tym celu zbyt?*
 **Wskaźnika myszy niejawne ustawienia przeglądarki sieci web**

 W wielu witryn sieci Web po najechaniu kursorem na określonego formantu rozszerza on Aby wyświetlić dodatkowe szczegóły. Ogólnie rzecz biorąc one wyglądać podobnie jak menu w aplikacji klasycznych. Ponieważ jest to typowy wzorzec, kodowane testy interfejsu użytkownika Włącz niejawny ruchów do przeglądania sieci Web. Na przykład jeśli rekord użytkownik znajduje się w programie Internet Explorer, zdarzenie jest wywoływane. Te zdarzenia może prowadzić do nadmiarowego ruchów rejestrowane. W związku z tym, niejawny ruchów są rejestrowane przy użyciu `ContinueOnError` równa `true` w pliku konfiguracji testu interfejsu użytkownika. Dzięki temu odtwarzania kontynuować, jeśli zdarzenie po wskazaniu wskaźnikiem zakończy się niepowodzeniem.

 Aby włączyć rejestrowanie ruchów niejawne w przeglądarce sieci Web, otwórz plik konfiguracji:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 Sprawdź, czy plik konfiguracyjny ma klucz `RecordImplicitiHovers` ustawiona na wartość `true` jak pokazano w następującym przykładzie:

```
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>

```

##  <a name="VerifyingCodeCUITModify"></a> Dostosowywanie kodowanego testu interfejsu użytkownika
 Po utworzeniu kodowanego testu interfejsu użytkownika można edytować jej za pomocą jednej z następujących narzędzi w programie Visual Studio:

-   **Konstruktor testu kodowanego interfejsu użytkownika:** Aby dodać dodatkowe elementy sterujące i walidacji do testów, należy użyć konstruktora kodowanego testu interfejsu użytkownika. Zobacz sekcję [dodawanie formantów i weryfikowania ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions) w tym temacie.

-   **Edytor testu kodowanego interfejsu użytkownika:** Edytor kodowanego testu interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika, możesz zlokalizować, wyświetlić i edytować swoje metody testowe. Można również edytować akcje interfejsu użytkownika oraz skojarzone z nimi kontrolki w mapy formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [testy interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

-   **Edytor kodu:**

    -   Ręcznie Dodaj kod dla formantów w teście, zgodnie z opisem w [akcji kontrolki UI kodowania i właściwości](#actions) w tym temacie.

    -   Po utworzeniu kodowanego testu interfejsu użytkownika, można zmodyfikować, aby była opartych na danych. Aby uzyskać więcej informacji, zobacz [tworzenie ze kodowanego testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md).

    -   Podczas odtwarzania testu kodowanego interfejsu użytkownika można nakazać testu oczekiwania dla określonych zdarzeń, takiego jak okno pojawia się pasek postępu zniknąć i tak dalej. Aby to zrobić, należy dodać odpowiednią metodę UITestControl.WaitForControlXXX(). Aby uzyskać pełną listę dostępnych metod, zobacz [wprowadzania kodowanego interfejsu użytkownika testy oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Na przykład kodowane testy interfejsu użytkownika, która czeka na formant włączyć przy użyciu metody WaitForControlEnabled zobacz [instruktażu: Tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    -   Kodowane testy interfejsu użytkownika obsługują niektóre formanty języka HTML5, które są dołączone do programu Internet Explorer 9 i Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [za pomocą kontrolek HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).

    -   **Wskazówki dotyczące kodowania kodowanego testu interfejsu użytkownika:**

        -   [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)

        -   [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)

        -   [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)

        -   [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

###  <a name="generatedCode"></a> Wygenerowany kod
 Po wybraniu **Generuj kod**, tworzonych jest kilka fragmentów kodu:

- **Wiersz w metodzie testowej.**

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

- **Metoda w UIMap.uitest**

   Ta metoda obejmuje szczegółów nagrane akcje lub wartość, która Cię o zweryfikowanie informacji. Ten kod można edytować, otwierając UIMap.uitest. Zostanie otwarty w edytorze specjalistyczne, można usunąć lub refaktoryzować zarejestrowane akcje.

   Youcan również wyświetlić wygenerowana metoda w UIMap.Designer.cs. Ta metoda wykonuje akcje rejestrowane po uruchomieniu testu.

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
  >  Nie należy edytować tego pliku, ponieważ zostaną wygenerowane, gdy tworzysz więcej testów.

   Można tworzyć dostosowane wersji tych metod, kopiując je do UIMap.cs. Na przykład można dokonać sparametryzowane wersji, który można wywołać z metody testowej:

  ```csharp
  // File: UIMap.cs
  public partial class UIMap // Same partial class
  {
    /// <summary>
    /// Add two numbers – parameterized version
    /// </summary>
    public void AddTwoNumbers(int firstNumber, int secondNumber)
    { ...   // Code modified to use parameters.
    }
  }
  ```

- **Deklaracje w UIMap.uitest**

   Te deklaracje reprezentują kontrolek interfejsu użytkownika aplikacji, które są używane w ramach testu. Służą one przez wygenerowany kod do obsługi formantów i uzyskiwanie dostępu do ich właściwości.

   Umożliwia także je w przypadku pisania własnego kodu. Na przykład można mieć swojej metody testowej, wybierz hiperłącze w aplikacji sieci Web, wpisz wartość w polu tekstowym lub gałęzie i wykonać różne operacje testowania na podstawie wartości w polu.

   Można dodać wiele kodowane testy interfejsu użytkownika i wiele obiektów mapy interfejsu użytkownika i pliki, aby usprawnić testowanie dużej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).

  Aby uzyskać więcej informacji na temat wygenerowany kod, zobacz [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

###  <a name="actions"></a> Kodowanie akcji kontrolki UI oraz właściwości
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

##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Aby pobierać lub ustawiać właściwości z kontrolek testu interfejsu użytkownika bezpośrednio

-   Za pomocą kontrolek, które wynikają z T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, takie jak T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList lub w: Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox, można uzyskać lub ustawić wartości właściwości bezpośrednio, wykonując następujące czynności:

    ```
    int i = myHtmlList.ItemCount;
    myWinCheckBox.Checked = true;
    ```

##### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z kontrolek testu interfejsu użytkownika

-   Aby uzyskać wartość właściwości w kontrolce, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

-   Aby określić właściwość kontrolki, które można pobrać, użyj odpowiedni ciąg z `PropertyNames` klasy w każdej kontrolce jako parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> zwraca odpowiedni typ danych, ale zwraca wartość jest rzutowany jako <xref:System.Object>. Zwracany <xref:System.Object> następnie musi być rzutowany jako odpowiedniego typu.

     Przykład:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

##### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości formantów testu interfejsu użytkownika

-   Aby ustawić właściwości w kontrolce, należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

-   Aby określić właściwość kontrolki, które można ustawić, użyj odpowiedni ciąg z `PropertyNames` klasę jako pierwszy parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, z wartością właściwości jako drugi parametr.

     Przykład:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

###  <a name="debugging"></a> Debugowanie
 Możesz analizować kodowanych testów interfejsu użytkownika za pomocą zakodowanych dziennikach testów interfejsu użytkownika. Kodowane filtr dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje dotyczące Twojego kodowanego testu interfejsu użytkownika. Format dzienniki umożliwia szybkie debugowanie problemów. Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

##  <a name="VerifyCodeUsingCUITWhatsNext"></a> Jaka jest przyszłość?
 **Dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika:** Można uruchomić kodowane testy interfejsu użytkownika bezpośrednio z programu Visual Studio, zgodnie z opisem we wcześniejszej części tego tematu. Ponadto można uruchomić zautomatyzowane testy interfejsu użytkownika z [!INCLUDE[TCMext](../includes/tcmext-md.md)], lub z [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]. Kodowane testy interfejsu użytkownika są automatyzowane, mają wchodzić w interakcje z pulpitem po uruchomieniu, w przeciwieństwie do innych testów automatycznych.

- [Instrukcje: Uruchamianie testów z programu Microsoft Visual Studio](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

- [Uruchamianie automatycznych testów w programie Microsoft Test Manager](http://msdn.microsoft.com/0632f265-63fe-4859-a413-9bb934c66835)

- [Instrukcje: Konfigurowanie i przeprowadzanie zaplanowanych testów po skompilowaniu aplikacji](http://msdn.microsoft.com/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)

- [Uruchom testy w procesie kompilacji](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)

- [Uruchamianie testów automatycznych z wiersza polecenia](http://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)

- [Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem](/visualstudio/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop?view=vs-2015)

- [&#91;wycofane&#93; za pomocą kodowanych testów interfejsu użytkownika w testach obciążenia](http://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)

  **Dodawanie obsługi kontrolek niestandardowych:**  Kodowanych testów interfejsu użytkownika nie obsługuje każdego możliwego interfejsu użytkownika i może nie obsługiwać interfejsu użytkownika, którą chcesz przetestować. Na przykład nie można od razu utworzyć kodowany test interfejsu użytkownika interfejsu użytkownika dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Można jednak utworzyć rozszerzenie kodowanych testów interfejsu użytkownika, który będzie obsługiwać formant niestandardowy.

- [Włączanie testowania kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

  Kodowane testy interfejsu użytkownika są często używane do automatyzacji testów ręcznych. Aby uzyskać dodatkowe wskazówki, zobacz [testowanie dostarczania ciągłego w programie Visual Studio 2012 – rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196). Aby uzyskać więcej informacji na temat testów ręcznych, zobacz [ &#91;wycofane&#93; tworzenie ręcznych przypadków testowych za pomocą programu Microsoft Test Manager](http://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Aby uzyskać więcej informacji na temat automatycznych testów systemowych, zobacz [tworzenie zautomatyzowanych testów przy użyciu programu Microsoft Test Manager](http://msdn.microsoft.com/7b5075ee-ddfe-411d-b1d4-94283550a5d0).

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
- [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)

- [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="faq"></a>Najczęściej zadawane pytania
- [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](http://go.microsoft.com/fwlink/?LinkID=230576)

- [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Forum
- [Visual Studio automatyczne testowanie interfejsu użytkownika (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Podnoszenie jakości kodu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
- [Przewodnik: Tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Uaktualnianie kodowanych testów interfejsu użytkownika programu Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
- [Generowanie kodowanego testu interfejsu użytkownika na podstawie dotychczasowego rejestrowania akcji](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
