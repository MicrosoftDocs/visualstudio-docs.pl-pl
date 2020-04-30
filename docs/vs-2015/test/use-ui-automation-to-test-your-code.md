---
title: Używanie automatyzacji interfejsu użytkownika do testowania kodu | Microsoft Docs
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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e054909bb8f020ed496185f0ba64aafec016358b
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586452"
---
# <a name="use-ui-automation-to-test-your-code"></a>Używanie automatyzacji interfejsu użytkownika do testowania kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy automatyczne, które obsługują aplikację za poorednictwem interfejsu użytkownika (UI), są znane jako *kodowane testy interfejsów* użytkownika (CUITs). Te testy obejmują Testowanie funkcjonalne formantów interfejsu użytkownika. Umożliwiają one sprawdzenie, czy cała aplikacja, w tym jej interfejs użytkownika, działa poprawnie. Kodowane testy interfejsu użytkownika są szczególnie przydatne w przypadku, gdy na stronie sieci Web występuje Walidacja lub inna logika. Są one również często używane do automatyzowania istniejącego testu ręcznego.

 Jak pokazano na poniższej ilustracji, typowe środowisko programistyczne może znajdować się w jednym miejscu, w którym po prostu kompilujesz aplikację (F5) i klikaj przez kontrolki interfejsu użytkownika, aby sprawdzić, czy elementy działają prawidłowo. Następnie możesz zdecydować się na utworzenie kodowanego testu, aby nie trzeba było kontynuować testowania aplikacji ręcznie. W zależności od konkretnej funkcji testowanej w aplikacji można napisać kod dla testu funkcjonalnego lub dla testu integracji, który może lub nie może obejmować testowania na poziomie interfejsu użytkownika. Jeśli po prostu chcesz bezpośrednio uzyskać dostęp do niektórych logiki biznesowej, możesz zakodować test jednostkowy. Jednak w pewnych okolicznościach może być korzystne do uwzględnienia testowania różnych formantów interfejsu użytkownika w aplikacji. Kodowany test interfejsu użytkownika może zautomatyzować początkowy (F5) scenariusz, sprawdzając, czy zmiany kodu nie wpływają na działanie aplikacji.

 ![Testowanie podczas opracowywania aplikacji](../test/media/cuit-overview.png "CUIT_Overview")

 Tworzenie kodowanego testu interfejsu użytkownika jest proste. Po prostu wykonujesz test ręcznie, podczas gdy Konstruktor testów CUIT działa w tle. Możesz również określić, jakie wartości powinny być wyświetlane w określonych polach. Konstruktor testu CUIT rejestruje akcje i generuje z nich kod. Po utworzeniu testu można go edytować w wyspecjalizowanym edytorze, który pozwala modyfikować sekwencję akcji.

 Alternatywnie, jeśli masz przypadek testowy, który został zarejestrowany w Microsoft Test Manager, można wygenerować kod z tego kodu. Aby uzyskać więcej informacji, zobacz [nagrywanie i odtwarzanie testów ręcznych](/azure/devops/test/mtm/record-play-back-manual-tests).

 Wyspecjalizowany Konstruktor i Edytor testów CUIT ułatwiają tworzenie i edytowanie kodowanych testów interfejsu użytkownika, nawet jeśli główne umiejętności są skoncentrowane na testowaniu zamiast kodowania. Ale jeśli jesteś deweloperem i chcesz przetworzyć test w bardziej zaawansowany sposób, kod jest strukturalny, dzięki czemu będzie on prosty do kopiowania i dostosowywania. Na przykład możesz zarejestrować test, aby kupić coś w witrynie sieci Web, a następnie edytować wygenerowany kod, aby dodać pętlę, która kupuje wiele elementów.

 **Wymagania**

- Visual Studio Enterprise

  Aby uzyskać więcej informacji o tym, które platformy i konfiguracje są obsługiwane przez kodowane testy interfejsu użytkownika, zobacz [obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

  **W tym temacie**

- [Tworzenie kodowanych testów interfejsu użytkownika](#VerifyingCodeUsingCUITCreate)

  - [Main — procedura](#VerifyingCodeUsingCUITCreate)

  - [Uruchamianie i zatrzymywanie aplikacji](#starting)

  - [Sprawdzanie poprawności właściwości formantów interfejsu użytkownika](#VerifyingCodeUsingCUITGenerateAssertions)

- [Dostosowywanie kodowanego testu interfejsu użytkownika](#VerifyingCodeCUITModify)

  - [Wygenerowany kod](#generatedCode)

  - [Kodowanie akcji i właściwości kontrolki interfejsu użytkownika](#actions)

  - [Debugowanie](#debugging)

- [Co dalej](#VerifyCodeUsingCUITWhatsNext)

## <a name="creating-coded-ui-tests"></a><a name="VerifyingCodeUsingCUITCreate"></a>Tworzenie kodowanych testów interfejsu użytkownika

1. **Utwórz projekt kodowanego testu interfejsu użytkownika.**

    Kodowane testy interfejsu użytkownika muszą być zawarte w projekcie kodowanego testu interfejsu użytkownika. Jeśli nie masz jeszcze projektu kodowanego testu interfejsu użytkownika, utwórz go. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt** , a następnie wybierz opcję **Visual Basic** lub **Visual C#**. Następnie wybierz kolejno pozycje **test**i **kodowany test interfejsu użytkownika**.

   - <em>Nie widzę szablonów projektu **kodowanego testu interfejsu użytkownika</em>* .*

      Być może używasz wersji programu Visual Studio, która nie obsługuje kodowanych testów interfejsu użytkownika. Aby utworzyć kodowane testy interfejsu użytkownika, należy użyć Visual Studio Enterprise.

2. **Dodaj kodowany plik testu interfejsu użytkownika.**

    Jeśli właśnie utworzono kodowany projekt interfejsu użytkownika, pierwszy plik CUIT jest dodawany automatycznie. Aby dodać inny plik testowy, otwórz menu skrótów dla projektu kodowanych testów interfejsu użytkownika, wskaż polecenie **Dodaj**, a następnie wybierz **kodowany test interfejsu użytkownika**.

    ![Tworzenie kodowanego testu interfejsu użytkownika](../test/media/codedui-create.png "CodedUI_Create")

    W oknie dialogowym **generowanie kodu dla kodowanego testu interfejsu użytkownika** wybierz pozycję **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia**.

    ![Wybieranie akcji rekordu](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")

    Zostanie wyświetlony Konstruktor kodowanego testu interfejsu użytkownika, a program Visual Studio jest zminimalizowany.

    ![Konstruktor kodowanego testu interfejsu użytkownika](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")

3. **Rejestruje sekwencję akcji**.

    **Aby rozpocząć nagrywanie**, wybierz ikonę **rekordu** . Wykonaj czynności, które chcesz przetestować w aplikacji, w tym uruchamianie aplikacji, jeśli jest to wymagane.

    Na przykład w przypadku testowania aplikacji sieci Web można uruchomić przeglądarkę, przejść do witryny sieci Web i zalogować się do aplikacji.

    **Aby wstrzymać nagrywanie**, na przykład w przypadku konieczności zajmowania się pocztą przychodzącą wybierz pozycję **Wstrzymaj**.

   > [!WARNING]
   > Wszystkie akcje wykonywane na pulpicie zostaną zarejestrowane. Wstrzymaj nagrywanie, jeśli wykonujesz akcje, które mogą prowadzić do zarejestrowania poufnych danych.

    **Aby usunąć akcje** , które zostały zarejestrowane przez pomyłkę, wybierz polecenie **Edytuj akcje**.

    **Aby wygenerować kod** , który będzie replikować akcje, wybierz ikonę **Generuj kod** i wpisz nazwę i opis dla KODOWANEJ metody testowania interfejsu użytkownika.

4. **Sprawdź wartości w polach interfejsu użytkownika, takich jak pola tekstowe**.

    Wybierz pozycję **Dodaj potwierdzenia** w konstruktorze kodowanego testu interfejsu użytkownika, a następnie wybierz KONTROLKĘ interfejs użytkownika w działającej aplikacji. Na liście właściwości, które pojawiają się, wybierz właściwość, na przykład **tekst** w polu tekstowym. W menu skrótów wybierz polecenie **Dodaj potwierdzenie**. W oknie dialogowym wybierz operator porównania, wartość porównania i komunikat o błędzie.

    Zamknij okno potwierdzenia i wybierz polecenie **Generuj kod**.

    ![Element docelowy kodowanego testu interfejsu użytkownika](../test/media/codedui-1.png "CodedUI_1")

   > [!TIP]
   > Alternatywa między akcjami rejestrowania i weryfikowaniem wartości. Generuj kod na końcu każdej sekwencji akcji lub weryfikacji. Jeśli chcesz, będzie można później wstawiać nowe akcje i weryfikacje.

    Aby uzyskać więcej informacji, zobacz [Walidacja właściwości kontrolek](#VerifyingCodeUsingCUITGenerateAssertions).

5. **Wyświetl wygenerowany kod testu**.

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

6. **Dodaj więcej akcji i potwierdzeń**.

    Umieść kursor w odpowiednim punkcie w metodzie testowej, a następnie w menu skrótów wybierz polecenie **Generuj kod dla kodowanego testu interfejsu użytkownika**. Nowy kod zostanie wstawiony w tym momencie.

7. **Edytuj szczegóły akcji testowych i potwierdzeń**.

    Otwórz UIMap. UITest. Ten plik zostanie otwarty w edytorze kodowanego testu interfejsu użytkownika, w którym można edytować dowolną sekwencję zarejestrowanych akcji, a także edytować potwierdzenia.

    ![Edytor kodowanego testu interfejsu użytkownika](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")

    Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. **Uruchom test**.

    Użyj Eksploratora testów lub Otwórz menu skrótów w metodzie testowej, a następnie wybierz polecenie **Uruchom testy**. Aby uzyskać więcej informacji na temat sposobu uruchamiania testów, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje uruchamiania KODOWANYCH testów interfejsu użytkownika* w sekcji [co dalej?](#VerifyCodeUsingCUITWhatsNext) na końcu tego tematu.

   Pozostałe sekcje w tym temacie zawierają więcej szczegółowych informacji na temat kroków opisanych w tej procedurze.

   Aby zapoznać się z bardziej szczegółowym przykładem, zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W tym przewodniku utworzysz prostą aplikację Windows Presentation Foundation (WPF), która pokazuje, jak tworzyć, edytować i obsługiwać kodowane testy interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.

### <a name="starting-and-stopping-the-application-under-test"></a><a name="starting"></a>Uruchamianie i zatrzymywanie testowanej aplikacji
 *Nie chcę osobno uruchamiać i zatrzymywać aplikacji, przeglądarki lub bazy danych dla każdego testu. Jak mogę tego uniknąć?*

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Jeśli nie chcesz rejestrować akcji do uruchamiania testowanej aplikacji, musisz uruchomić aplikację przed wybraniem ikony **rekordu** .

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Na końcu testu proces, w którym są kończone przebiegi testowe. Jeśli aplikacja została uruchomiona w teście, aplikacja zwykle zostanie zamknięta.  Jeśli nie chcesz, aby test zamykał aplikację po jej zakończeniu, musisz dodać plik. runsettings do rozwiązania i użyć `KeepExecutorAliveAfterLegacyRun` opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Można dodać metodę inicjowania testu, identyfikowaną przez atrybut [TestInitialize], który uruchamia kod na początku każdej metody testowej. Na przykład można uruchomić aplikację z metody TestInitialize.

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Można dodać metodę oczyszczania testu, identyfikowaną przez atrybut [TestCleanup], który uruchamia kod na końcu każdej metody testowej. Na przykład Metoda zamykania aplikacji może być wywołana z metody TestCleanup.

### <a name="validating-the-properties-of-ui-controls"></a><a name="VerifyingCodeUsingCUITGenerateAssertions"></a>Sprawdzanie poprawności właściwości formantów interfejsu użytkownika
 Możesz użyć **konstruktora kodowanego testu interfejsu** użytkownika, aby dodać formant interfejsu użytkownika do [UIMap](/previous-versions/dd580454(v=vs.140)) dla testu lub wygenerować kod dla metody walidacji, która używa potwierdzenia dla kontrolki interfejsu użytkownika.

 Aby wygenerować potwierdzenia dla formantów interfejsu użytkownika, wybierz narzędzie **Dodaj potwierdzenia** w konstruktorze kodowanego testu interfejsu użytkownika i przeciągnij je do kontrolki w testowanej aplikacji, która ma zostać zweryfikowana. Gdy pole zawiera opis kontrolki, zwolnij przycisk myszy. Kod klasy kontrolki jest natychmiast tworzony w `UIMap.Designer.cs` pliku.

 ![Element docelowy kodowanego testu interfejsu użytkownika](../test/media/codedui-1.png "CodedUI_1")

 Właściwości tej kontrolki są teraz wyświetlane w oknie dialogowym **Dodawanie potwierdzeń** .

 Innym sposobem przechodzenia do konkretnej kontrolki jest wybranie strzałki **(<<)** , aby rozwinąć widok **mapy formantów interfejsu użytkownika**. Aby znaleźć kontrolkę nadrzędną, równorzędną lub podrzędną, można kliknąć dowolne miejsce na mapie i użyć klawiszy strzałek do poruszania się po drzewie.

 ![Właściwości kodowanego testu interfejsu użytkownika](../test/media/codedui-2.png "CodedUI_2")

- *Nie widzę żadnych właściwości, gdy wybierzę kontrolkę w mojej aplikacji lub nie widzisz kontrolki na mapie formantów interfejsu użytkownika.*

   W kodzie aplikacji formant, który ma zostać zweryfikowany, musi mieć unikatowy identyfikator, taki jak atrybut identyfikatora HTML lub identyfikator UId WPF. Aby dodać te identyfikatory, może być konieczne zaktualizowanie kodu aplikacji.

  Następnie otwórz menu skrótów dla właściwości kontrolki interfejsu użytkownika, którą chcesz zweryfikować, a następnie wskaż polecenie **Dodaj potwierdzenie**. W oknie dialogowym **Dodaj potwierdzenie** wybierz **komparator** dla potwierdzenia, a na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>wpisz wartość potwierdzenia w polu **wartość porównania**.

  ![Zatwierdzeń kodowanego testu interfejsu użytkownika](../test/media/codedui-3.png "CodedUI_3")

  Po dodaniu wszystkich potwierdzeń dla testu wybierz **przycisk OK**.

  Aby wygenerować kod dla potwierdzeń i dodać formant do mapy interfejsu użytkownika, wybierz ikonę **Generuj kod** . Wpisz nazwę metody kodowanego testu interfejsu użytkownika i opis metody, która zostanie dodana jako komentarz dla metody. Wybierz pozycję **Dodaj i Generuj**. Następnie wybierz ikonę **Zamknij** , aby zamknąć **konstruktora KODOWANEGO testu interfejsu użytkownika**. Spowoduje to wygenerowanie kodu podobnego do poniższego kodu. Na przykład, Jeśli wprowadzona nazwa to `AssertForAddTwoNumbers`, kod będzie wyglądać podobnie do tego przykładu:

- Dodaje wywołanie metody Assert AssertForAddTwoNumbers do metody testowej w pliku kodowanego testu interfejsu użytkownika:

  ```
  [TestMethod]
  public void CodedUITestMethod1()
  {
      this.UIMap.AddTwoNumbers();
      this.UIMap.AssertForAddTwoNumbers();
  }
  ```

   Można edytować ten plik, aby zmienić kolejność kroków i potwierdzeń lub utworzyć nowe metody testowe. Aby dodać więcej kodu, umieść kursor w metodzie testowej, a następnie w menu skrótów wybierz polecenie **Generuj kod dla kodowanego testu interfejsu użytkownika**.

- Dodaje metodę o nazwie `AssertForAddTwoNumbers` do mapy interfejsu użytkownika (UIMap. UITest). Ten plik zostanie otwarty w edytorze kodowanego testu interfejsu użytkownika, w którym można edytować potwierdzenia.

   ![Edytuj potwierdzenie przy użyciu edytora kodowanego testu interfejsu użytkownika](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")

   Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

   Możesz również wyświetlić wygenerowany kod metody Assert w UIMap.Designer.cs. Nie należy jednak edytować tego pliku. Jeśli chcesz dostosować wersję kodu, skopiuj metody do innego pliku, takiego jak UIMap.cs, Zmień nazwę metod i zmodyfikuj je w tym miejscu.

  ```
  public void AssertForAddTwoNumbers()
  {
      ...
  }
  ```

  *Kontrolka, którą chcę zaznaczyć, traci fokus i znika, gdy próbuję wybrać narzędzie Dodaj potwierdzenia z konstruktora kodowanego testu interfejsu użytkownika. Jak mogę wybrać formant?* 
   **Wybieranie ukrytego formantu przy użyciu klawiatury**

  Czasami podczas [dodawania kontrolek i weryfikowania ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions)może być konieczne korzystanie z klawiatury. Na przykład podczas próby zarejestrowania kodowanego testu interfejsu użytkownika korzystającego z kontrolki menu kontekstowego lista elementów menu w formancie utraci fokus i znika przy próbie wybrania narzędzia Dodaj potwierdzenia z konstruktora kodowanego testu interfejsu użytkownika. Jest to zademonstrowane na poniższej ilustracji, gdzie menu kontekstowe w programie Internet Explorer utraci fokus i znika, jeśli spróbujesz wybrać je za pomocą narzędzia Dodaj potwierdzenia.

  ![Zestaw SDK CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

  Aby użyć klawiatury do wybrania kontrolki interfejsu użytkownika, umieść kursor nad kontrolką za pomocą myszy. Następnie trzymaj wciśnięty klawisz **Ctrl** i klawisz **i** w tym samym czasie. Zwolnij klawisze. Kontrolka jest rejestrowana przez kodowany Konstruktor testów międzytworzących.

> [!WARNING]
> Jeśli używasz programu Microsoft Lync, musisz zamknąć program Lync przed uruchomieniem konstruktora kodowanego testu interfejsu użytkownika. Program Microsoft Lync przeszkadza przy użyciu skrótu klawiaturowego **Ctrl + I** .

 *Nie mogę zarejestrować wskaźnika myszy na kontrolce. Czy istnieje sposób na to?*
 **Ręczne rejestrowanie przesuwania myszy**

 W pewnych okolicznościach konkretna kontrolka, która jest używana w kodowanym teście interfejsu użytkownika, może wymagać użycia klawiatury do ręcznego rejestrowania zdarzeń przesuwania myszy. Na przykład podczas testowania formularza systemu Windows lub aplikacji Windows Presentation Foundation (WPF) może istnieć kod niestandardowy. Można też mieć specjalne zachowanie zdefiniowane do przesuwania nad formantem, takie jak drzewo drzewa rozwijane po umieszczeniu na nim wskaźnika myszy. Aby przetestować takie okoliczności, trzeba ręcznie powiadomić konstruktora kodowanego testu interfejsu użytkownika, który jest przesuwany nad formantem, naciskając wstępnie zdefiniowane klawisze klawiatury.

 Po wykonaniu kodowanego testu interfejsu użytkownika Umieść wskaźnik myszy nad kontrolką. Naciśnij i przytrzymaj klawisz CTRL, a następnie naciśnij i przytrzymaj klawisze Shift i R na klawiaturze. Zwolnij klawisze. Zdarzenie dotyczące przesuwania myszy jest rejestrowane przez kodowany Konstruktor testów międzyelementowych.

 ![CodedUI&#95;aktywowania](../test/media/codedui-hover.png "CodedUI_Hover")

 Po wygenerowaniu metody testowej kod podobny do następującego przykładu zostanie dodany do pliku UIMap.Desinger.cs:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));

```

 *Przypisanie klucza do przechwytywania zdarzeń aktywowania myszy jest używane w innym miejscu w środowisku. Czy mogę zmienić domyślne przypisanie klucza?*
 **Konfigurowanie przypisań klawiatury do przesuwania myszy**

 W razie potrzeby domyślne przypisanie klawiatury Ctrl + Shift + R, które służy do stosowania zdarzeń przesuwania myszy w kodowanych testach interfejsu użytkownika, można skonfigurować tak, aby używały różnych kluczy.

> [!WARNING]
> Nie należy zmieniać przypisań klawiatury dla zdarzeń aktywowania myszy w normalnych warunkach. Należy zachować ostrożność podczas ponownego przypisywania przypisania klawiatury. Wybór może być już używany w innym miejscu w programie Visual Studio lub w testowanej aplikacji.

 Aby zmienić przypisania klawiatury, należy zmodyfikować następujący plik konfiguracji:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 W pliku konfiguracji Zmień wartości kluczy `HoverKeyModifier` i `HoverKey` , aby zmodyfikować przypisania klawiatury:

```
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>

```

 *Mam problemy z nagrywaniem myszy na stronie internetowej. Czy istnieje również poprawka?*
 **Ustawianie niejawnego przesuwania myszy dla przeglądarki sieci Web**

 W wielu witrynach sieci Web, gdy wskaźnik myszy znajduje się nad określoną kontrolką, rozszerza się, aby wyświetlić dodatkowe szczegóły. Ogólnie rzecz biorąc, wyglądają jak menu w aplikacjach komputerowych. Ponieważ jest to typowy wzorzec, kodowane testy interfejsu użytkownika umożliwiają niejawne przechodzenie do przeglądania w sieci Web. Na przykład, Jeśli rejestrujesz aktywowane w programie Internet Explorer, zdarzenie zostanie wyzwolone. Te zdarzenia mogą prowadzić do nagrania nadmiarowych kursorów. Z tego względu niejawne aktywowanie są `ContinueOnError` rejestrowane z `true` ustawionym na wartość w pliku konfiguracyjnym testu interfejsu użytkownika. Dzięki temu odtwarzanie będzie kontynuowane w przypadku niepowodzenia zdarzenia aktywowania.

 Aby włączyć rejestrowanie niejawnych kursorów w przeglądarce internetowej, Otwórz plik konfiguracji:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 Sprawdź, czy plik konfiguracji ma klucz `RecordImplicitiHovers` ustawiony na wartość, `true` tak jak pokazano w następującym przykładzie:

```
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>

```

## <a name="customizing-your-coded-ui-test"></a><a name="VerifyingCodeCUITModify"></a>Dostosowywanie kodowanego testu interfejsu użytkownika
 Po utworzeniu kodowanego testu interfejsu użytkownika można go edytować przy użyciu dowolnego z następujących narzędzi w programie Visual Studio:

- **Konstruktor kodowanego testu interfejsu użytkownika:** Użyj konstruktora kodowanego testu interfejsu użytkownika, aby dodać dodatkowe kontrolki i weryfikację do testów. Zobacz sekcję [Dodawanie kontrolek i sprawdzanie poprawności ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions) w tym temacie.

- **Edytor kodowanego testu interfejsu użytkownika:** Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować metody testowe. Możesz również edytować akcje interfejsu użytkownika i ich skojarzone kontrolki na mapie formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Edytor kodu:**

  - Ręcznie Dodaj kod dla kontrolek w teście, zgodnie z opisem w sekcji opis [akcji i właściwości kontrolki interfejsu użytkownika](#actions) w tym temacie.

  - Po utworzeniu kodowanego testu interfejsu użytkownika można go zmodyfikować w taki sposób, aby był oparty na danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kodowanego testu interfejsu użytkownika opartego na danych](../test/creating-a-data-driven-coded-ui-test.md).

  - W przypadku odtwarzania kodowanego testu interfejsu użytkownika można nakazać testowi zaczekać na wystąpienie niektórych zdarzeń, takich jak okno, które ma zostać wyświetlone, pasek postępu, który ma być znikany itd. Aby to zrobić, Dodaj odpowiednią metodę UITestControl. WaitForControlXXX (). Aby zapoznać się z pełną listą dostępnych metod, zobacz [Tworzenie kodowanych testów interfejsu użytkownika w przypadku określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Przykład kodowanego testu interfejsu użytkownika, który czeka na włączenie formantu przy użyciu metody metody WaitForControlEnabled, zawiera [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5 zawartych w programie Internet Explorer 9 i Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).

  - **Wskazówki dotyczące kodowania kodowanego testu interfejsu użytkownika:**

    - [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)

    - [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)

    - [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a><a name="generatedCode"></a>Wygenerowany kod
 Gdy wybierzesz opcję **Generuj kod**, tworzone są kilka fragmentów kodu:

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

   Możesz kliknąć prawym przyciskiem myszy tę metodę, aby dodać bardziej zarejestrowane akcje i weryfikacje. Możesz również ręcznie ją edytować, aby zwiększyć lub zmodyfikować kod. Na przykład można ująć część kodu w pętli.

   Możesz także dodać nowe metody testowe i dodać kod do nich w taki sam sposób. Każda metoda testowa musi mieć `[TestMethod]` atrybut.

- **Metoda w UIMap. UITest**

   Ta metoda zawiera szczegółowe informacje o zarejestrowanych akcjach lub zweryfikowanej wartości. Możesz edytować ten kod, otwierając UIMap. UITest. Zostanie otwarta w wyspecjalizowanym edytorze, w którym można usunąć lub refaktoryzację zarejestrowanych akcji.

   Youcan również wyświetlanie wygenerowanej metody w UIMap.Designer.cs. Ta metoda wykonuje działania zarejestrowane podczas wykonywania testu.

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

   Można dostosować wersje tych metod, kopiując je do UIMap.cs. Na przykład można utworzyć sparametryzowanej wersji, którą można wywołać z metody testowej:

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

- **Deklaracje w UIMap. UITest**

   Te deklaracje reprezentują kontrolki interfejsu użytkownika aplikacji, które są używane przez test. Są one używane przez wygenerowany kod do obsługi kontrolek i uzyskiwania dostępu do ich właściwości.

   Można ich również użyć w przypadku pisania własnego kodu. Na przykład możesz mieć metodę testową, aby wybrać hiperłącze w aplikacji sieci Web, wpisać wartość w polu tekstowym lub rozgałęzić i wykonać różne akcje testowania na podstawie wartości w polu.

   Można dodać wiele kodowanych testów interfejsu użytkownika i wiele obiektów i plików map interfejsu użytkownika w celu ułatwienia testowania dużej aplikacji. Aby uzyskać więcej informacji, zobacz [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md).

  Aby uzyskać więcej informacji na temat wygenerowanego kodu, zobacz [anatomię kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).

### <a name="coding-ui-control-actions-and-properties"></a><a name="actions"></a>Kodowanie akcji i właściwości kontrolki interfejsu użytkownika
 Podczas pracy z kontrolkami testu interfejsu użytkownika w kodowanych testach interfejsu użytkownika są one podzielone na dwie części: akcje i właściwości.

- Pierwsza część składa się z akcji, które można wykonać na kontrolkach testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika mogą symulować kliknięcia myszą w kontrolce testu interfejsu użytkownika lub symulować klucze wpisane na klawiaturze, aby mieć wpływ na kontrolę testu interfejsu użytkownika.

- Druga część obejmuje umożliwienie pobierania i ustawiania właściwości kontrolki testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika mogą pobrać liczbę elementów w `ListBox`lub ustawić `CheckBox` do wybranego stanu.

  **Uzyskiwanie dostępu do akcji kontroli testu interfejsu użytkownika**

  Aby wykonać akcje na kontrolkach testów interfejsu użytkownika, takich jak kliknięcia myszą lub akcje klawiatury, należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> metod <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> w klasach i:

- Aby wykonać akcję zorientowaną myszą, taką jak kliknięcie myszą, na kontrolce testu interfejsu użytkownika Użyj polecenia <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

   `Mouse.Click(buttonCancel);`

- Aby wykonać akcję zorientowaną na klawiaturę, taką jak wpisywanie do kontrolki edycji, <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>Użyj.

   `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

  **Uzyskiwanie dostępu do właściwości kontrolki testu interfejsu użytkownika**

  Aby uzyskać i ustawić wartości właściwości dla kontrolki interfejsu użytkownika, można bezpośrednio pobrać lub ustawić wartości właściwości kontrolki lub użyć metod <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> z nazwą konkretnej właściwości, którą chcesz pobrać lub ustawić.

  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>zwraca obiekt, który następnie może być rzutowany na odpowiedni <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>akceptuje obiekt dla wartości właściwości.

##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Aby uzyskać lub ustawić właściwości z kontrolek testu interfejsu użytkownika bezpośrednio

- Z kontrolkami, które pochodzą z T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, takich jak T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList lub T:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox, można uzyskać lub ustawić wartości właściwości bezpośrednio w następujący sposób:

    ```
    int i = myHtmlList.ItemCount;
    myWinCheckBox.Checked = true;
    ```

##### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z kontrolek testu interfejsu użytkownika

- Aby uzyskać wartość właściwości z kontrolki, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Aby określić właściwość kontrolki do pobrania, użyj odpowiedniego ciągu z `PropertyNames` klasy w każdej kontrolce jako parametru do. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>zwraca odpowiedni typ danych, ale ta wartość zwracana jest rzutowana jako <xref:System.Object>. Zwrot <xref:System.Object> musi być następnie rzutowany jako odpowiedni typ.

     Przykład:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

##### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości dla kontrolek testu interfejsu użytkownika

- Aby ustawić właściwość w kontrolce, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Aby określić właściwość kontrolki do ustawienia, użyj odpowiedniego ciągu z `PropertyNames` klasy jako pierwszy parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, z wartością właściwości jako drugi parametr.

     Przykład:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

### <a name="debugging"></a><a name="debugging"></a>Debugera
 Kodowane testy interfejsu użytkownika można analizować za pomocą dzienników kodowanego testu interfejsu użytkownika. Dzienniki kodowanych testów interfejsu użytkownika filtru i rejestrowania ważnych informacji o kodowanych przebiegach testów interfejsu użytkownika. Format dzienników pozwala szybko debugować problemy. Aby uzyskać więcej informacji, zobacz [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a><a name="VerifyCodeUsingCUITWhatsNext"></a>Co dalej?
 **Dodatkowe opcje uruchamiania kodowanych testów interfejsu użytkownika:** Kodowane testy interfejsu użytkownika można uruchomić bezpośrednio z programu Visual Studio, zgodnie z opisem we wcześniejszej części tego tematu. Dodatkowo można uruchamiać zautomatyzowane testy interfejsu użytkownika z [!INCLUDE[TCMext](../includes/tcmext-md.md)]programu, lub z [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]programu. Gdy kodowane testy interfejsu użytkownika są zautomatyzowane, muszą one współdziałać z pulpitem podczas jego uruchamiania, w przeciwieństwie do innych automatycznych testów.

- [Instrukcje: uruchamianie testów z Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

- [Uruchamianie testów automatycznych w Microsoft Test Manager](https://msdn.microsoft.com/0632f265-63fe-4859-a413-9bb934c66835)

- [Instrukcje: Konfigurowanie i uruchamianie zaplanowanych testów po skompilowaniu aplikacji](https://msdn.microsoft.com/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)

- [Uruchom testy w procesie kompilacji](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)

- [Uruchamianie testów automatycznych z wiersza polecenia](https://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)

- [Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem](/visualstudio/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop?view=vs-2015)

- [&#91;wycofane&#93; przy użyciu kodowanych testów interfejsu użytkownika w testach obciążenia](https://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)

  **Dodawanie obsługi niestandardowych formantów:**  Struktura testowania kodowanego interfejsu użytkownika nie obsługuje wszystkich możliwych interfejsów użytkownika i może nie obsługiwać interfejsu użytkownika, który ma zostać przetestowany. Na przykład nie można od razu utworzyć kodowanego testu interfejsu użytkownika dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]interfejsu użytkownika. Można jednak utworzyć rozszerzenie dla kodowanego środowiska testowania interfejsu użytkownika, które będzie obsługiwało kontrolkę niestandardową.

- [Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

  Kodowane testy interfejsu użytkownika są często używane do automatyzowania ręcznych testów. Aby uzyskać dodatkowe wskazówki, zobacz [testowanie ciągłego dostarczania przy użyciu programu Visual Studio 2012 — Rozdział 5: Automatyzowanie testów systemu](https://msdn.microsoft.com/library/jj159335.aspx). Aby uzyskać więcej informacji na temat testów ręcznych, zobacz [&#91;wycofane&#93; tworzenia ręcznych przypadków testowych przy użyciu Microsoft Test Manager](https://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Aby uzyskać więcej informacji na temat zautomatyzowanych testów systemowych, zobacz [Tworzenie testów automatycznych przy użyciu Microsoft Test Manager](https://msdn.microsoft.com/7b5075ee-ddfe-411d-b1d4-94283550a5d0).

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
- [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)

- [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 5: Automatyzowanie testów systemowych](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="faq"></a>Najczęściej zadawane pytania
- [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

- [Kodowane testy interfejsu użytkownika — często zadawane pytania — 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
- [Testowanie automatyzacji interfejsu użytkownika programu Visual Studio (w tym CodedUI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Zobacz także

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Podnoszenie jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
- [Przewodnik: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Edycja zakodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Aktualizowanie kodowanych testów interfejsu użytkownika z Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
- [Generowanie kodowanego testu interfejsu użytkownika z istniejącego rejestrowania akcji](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
