---
title: Testowanie aplikacji platformy UWP przy użyciu kodowanego testu interfejsu użytkownika
description: Dowiedz się, jak utworzyć kodowany test interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows, tworząc aplikację platformy UWP do testowania i tworzenia kodowanego testu interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 0fb60de87fa98e4715d872512c120a408ec8339e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911518"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Tworzenie kodowanego testu interfejsu użytkownika w celu przetestowania aplikacji platformy UWP

W tym artykule wyjaśniono, jak utworzyć kodowany test interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows (platformy UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Tworzenie aplikacji platformy UWP do przetestowania

Pierwszym krokiem jest utworzenie prostej aplikacji platformy UWP do uruchomienia testu.

1. W programie Visual Studio Utwórz nowy projekt za pomocą szablonu **pusta aplikacja (uniwersalna systemu Windows)** dla programu Visual C# lub Visual Basic.

   ::: moniker range="vs-2017"

   ![Pusty szablon uniwersalnego systemu Windows aplikacji](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. W oknie dialogowym **Nowy projekt platforma uniwersalna systemu Windows** wybierz pozycję **OK** , aby zaakceptować domyślne wersje platformy.

1. W obszarze **Eksplorator rozwiązań** Otwórz *MainPage. XAML*.

   Plik zostanie otwarty w **Projektant XAML**.

1. Przeciągnij kontrolkę Button i kontrolkę TextBox z **przybornika** do powierzchni projektowej.

     ![Projektowanie aplikacji platformy UWP](../test/media/toolbox-controls.png)

1. Nadaj nazwę kontrolkom. Zaznacz kontrolkę TextBox, a następnie w oknie **Właściwości** wprowadź pole **tekstowe** w polu **Nazwa** . Zaznacz kontrolkę przycisk, a następnie w oknie **Właściwości** wprowadź **przycisk** w polu **Nazwa** .

1. Kliknij dwukrotnie formant Button i Dodaj następujący kod do treści `Button_Click` metody. Ten kod po prostu ustawia tekst w polu tekstowym na nazwę kontrolki Button, po prostu, aby przekazać nam coś do weryfikacji przy użyciu kodowanego testu interfejsu użytkownika, który zostanie utworzony w przyszłości.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Naciśnij klawisz **Ctrl** + **F5** , aby uruchomić aplikację. Powinna zostać wyświetlona zawartość podobna do tej:

   ![Aplikacja platformy UWP za pomocą przycisku i pola tekstowego](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika

1. Aby dodać projekt testowy do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

1. Wyszukaj i wybierz szablon **projekt kodowanego testu interfejsu użytkownika (Uniwersalna aplikacja systemu Windows)** .

   ::: moniker range="vs-2017"

   ![Nowy projekt kodowanego testu interfejsu użytkownika](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli nie widzisz szablonu **projektu kodowanych testów interfejsu użytkownika (uniwersalny system Windows)** , musisz [zainstalować składnik KODOWANEGO testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. W oknie dialogowym **generowanie kodu dla kodowanego testu interfejsu użytkownika** wybierz pozycję **ręcznie Edytuj test**.

   ![Generowanie kodu dla okna dialogowego kodowanego testu interfejsu użytkownika](../test/media/manually-edit-the-test.png)

1. Jeśli aplikacja platformy UWP nie jest już uruchomiona, należy ją uruchomić, naciskając klawisz **Ctrl** + **F5**.

1. Otwórz okno dialogowe **Konstruktor kodowanego testu interfejsu użytkownika** , umieszczając kursor w `CodedUITestMethod1` metodzie, a następnie wybierając pozycję **Testuj**  >  **generowanie kodu dla kodowanego testu interfejsu** użytkownika przy  >  **użyciu konstruktora kodowanego testu interfejsu użytkownika**.

1. Dodaj formanty do mapy formantów interfejsu użytkownika. Użyj narzędzia Cross-krzyżyk **konstruktora kodowanego testu interfejsu użytkownika** , aby wybrać kontrolkę przycisk w aplikacji platformy UWP. W oknie dialogowym **Dodawanie potwierdzeń** rozwiń okienko **mapy kontrolek interfejsu użytkownika** w razie potrzeby, a następnie wybierz pozycję **Dodaj formant do mapy formantów interfejsu użytkownika**.

     ![Dodawanie kontrolki do mapy interfejsu użytkownika](../test/media/add-control-to-ui-control-map.png)

1. Powtórz poprzedni krok, aby dodać kontrolkę TextBox do mapy formantów interfejsu użytkownika.

1. W oknie dialogowym **Konstruktor kodowanego testu interfejsu użytkownika** wybierz pozycję **Generuj kod** lub naciśnij klawisz **Ctrl** + **G**. Następnie wybierz pozycję **Generuj** , aby utworzyć kod dla zmian mapy formantów interfejsu użytkownika.

     ![Generuj kod dla mapy interfejsu użytkownika](../test/media/generate-code-dialog.png)

1. Aby sprawdzić, czy tekst w polu tekstowym zmieni się na **przycisk** po kliknięciu przycisku, kliknij przycisk.

     ![Kliknij formant przycisku, aby ustawić wartość TextBox](../test/media/uwp-app-button-textbox.png)

1. Dodaj potwierdzenie, aby zweryfikować tekst w kontrolce TextBox. Użyj narzędzia krzyżyk, aby zaznaczyć formant TextBox, a następnie wybierz właściwość **Text** w oknie dialogowym **Dodawanie potwierdzeń** . Następnie wybierz pozycję **Dodaj potwierdzenie** lub naciśnij klawisz **Alt** + **A**. W oknie **komunikat w przypadku niepowodzenia potwierdzenia** wprowadź **wartość pola tekstowego.** a następnie wybierz przycisk **OK**.

     ![Wybierz pole tekstowe z krzyżykiem i Dodaj potwierdzenie](../test/media/add-assertion-for-text.png)

1. Generuj kod testu dla potwierdzenia. W oknie dialogowym **Konstruktor kodowanego testu interfejsu użytkownika** wybierz polecenie **Generuj kod**. W oknie dialogowym **generowanie kodu** wybierz pozycję **Dodaj i Generuj**.

     ![Generuj kod dla potwierdzenia TextBox](../test/media/add-and-generate-assert-method.png)

   W **Eksplorator rozwiązań** Otwórz *UIMap.Designer.cs* , aby wyświetlić dodany kod dla metody Assert i kontrolek.

   > [!TIP]
   > Jeśli używasz Visual Basic, Otwórz *CodedUITest1. vb*. Następnie w `CodedUITestMethod1()` kodzie metody testowej kliknij prawym przyciskiem myszy wywołanie metody Assert `Me.UIMap.AssertMethod1()` i wybierz polecenie **Przejdź do definicji**. *UIMap. Designer. vb* otwiera się w edytorze kodu i można wyświetlić dodany kod dla metody Assert i kontrolek.

    > [!WARNING]
    > Nie należy modyfikować plików *UIMap.Designer.cs* ani *UIMap. Designer. vb* bezpośrednio. Jeśli to zrobisz, zmiany zostaną nadpisywane podczas generowania testu.

    Metoda Assert wygląda następująco:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Następnie musimy uzyskać **AutomationId** [aplikacji](#create-a-uwp-app-to-test) platformy UWP, która ma zostać przetestowana. Otwórz menu **Start** systemu Windows, aby wyświetlić kafelek aplikacji. Następnie przeciągnij ![ ikonę docelową narzędzia krzyżyka ](media/target-icon.png) z okna dialogowego **Konstruktor KODOWANEGO testu interfejsu użytkownika** do kafelka aplikacji. Gdy niebieskie pole otacza kafelka, zwolnij przycisk myszy.

   ![Narzędzie krzyżykowe](media/cross-hair-tool.png)

   Zostanie otwarte okno dialogowe **Dodawanie potwierdzeń** i zostanie wyświetlona **AutomationId** dla aplikacji. Kliknij prawym przyciskiem myszy pozycję **AutomationId** i wybierz polecenie **Kopiuj wartość do schowka**.

   ![AutomationID w oknie dialogowym Dodawanie potwierdzenia](../test/media/automation-id.png)

1. Dodaj kod do metody testowej, aby uruchomić aplikację platformy UWP. W **Eksplorator rozwiązań** Otwórz *CodedUITest1.cs* lub *CodedUITest1. vb*. Powyżej wywołania do `AssertMethod1` , Dodaj kod, aby uruchomić aplikację platformy UWP:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Zastąp identyfikator automatyzacji w przykładowym kodzie wartością skopiowaną do Schowka w poprzednim kroku.

   > [!IMPORTANT]
   > Przytnij początek identyfikatora automatyzacji, aby usunąć znaki, takie jak **P ~**. Jeśli te znaki nie są przycinane, test zgłosi wyjątek `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` podczas próby uruchomienia aplikacji.

1. Następnie Dodaj kod do metody testowej, aby kliknąć przycisk. W wierszu po `XamlWindow.Launch` Dodaj gest, aby nacisnąć kontrolkę Button:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po dodaniu kodu, kompletna `CodedUITestMethod1` Metoda testowa powinna wyglądać następująco:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Skompiluj projekt testowy, a następnie otwórz **Eksploratora testów** , wybierając **test**  >    >  **Eksplorator testów** systemu Windows.

1. Wybierz opcję **Uruchom wszystkie** , aby uruchomić test.

   Aplikacja zostanie otwarta, przycisk jest wybierany, a właściwość **Text tekstu** jest wypełniana. Metoda Assert sprawdza poprawność właściwości **Text** pola tekstowego.

   Po zakończeniu testu w **Eksploratorze testów** zostanie wyświetlony komunikat zakończony testem.

   ![Testy zakończone w Eksploratorze testów](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>P: Dlaczego nie widzę opcji rejestrowania kodowanego testu interfejsu użytkownika w oknie dialogowym generowanie kodu dla kodowanego testu interfejsu użytkownika?

Odp **.: opcja** rejestrowania nie jest obsługiwana w przypadku aplikacji platformy UWP.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>P: Czy można utworzyć kodowany test interfejsu użytkownika dla aplikacji platformy UWP w oparciu o WinJS?

Odp **.: nie**, obsługiwane są tylko aplikacje oparte na języku XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap. Designer?

Odp **.: wszelkie** zmiany kodu wprowadzane w pliku *UIMapDesigner.cs* są zastępowane przy każdym wygenerowaniu kodu przy użyciu **konstruktora kodowanego testu interfejsu użytkownika**. Jeśli trzeba zmodyfikować nagraną metodę, skopiuj ją do pliku *UIMap.cs* i zmień jej nazwę. Plik *UIMap.cs* może służyć do przesłonięcia metod i właściwości w pliku *UIMapDesigner.cs* . Usuń odwołanie do oryginalnej metody w pliku *CodedUITest.cs* i zastąp je nazwą metody o zmienionej nazwie.

## <a name="see-also"></a>Zobacz też

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Ustawianie unikatowych właściwości automatyzacji dla kontrolek platformy UWP](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
