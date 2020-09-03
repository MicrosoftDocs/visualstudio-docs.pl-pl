---
title: Testowanie aplikacji ze sklepu Windows platformy UWP i 8,1 przy użyciu kodowanych testów interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce4c6ceec9489abcd3573c126aefe98a268187c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660443"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Testowanie aplikacji platformy UWP i 8.1 Store systemu Windows za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik służy do tworzenia testów interfejsu użytkownika dla aplikacji platformy UWP i aplikacji ze sklepu w języku XAML 8,1.

## <a name="create-a-simple-windows-store-app"></a>Tworzenie prostej aplikacji ze sklepu Windows

1. Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji ze sklepu Windows opartej na języku XAML, musisz [ustawić unikatową Właściwość automatyzacji, która identyfikuje każdy formant](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).

     W menu **Narzędzia** wskaż polecenie **Opcje** , a następnie wybierz **Edytor tekstu**, **XAML**i **inne**.

     Zaznacz pole wyboru, aby automatycznie nazwać elementy interaktywne podczas tworzenia.

     ![Opcje różne XAML](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

2. Utwórz nowy projekt dla pustej aplikacji ze sklepu Windows w języku XAML przy użyciu szablonu Visual C# lub Visual Basic.

     ![Tworzenie pustej aplikacji do sklepu Windows &#40;XAML&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")

3. W Eksplorator rozwiązań otwórz MainPage. XAML. Z przybornika przeciągnij kontrolkę Button i kontrolkę TextBox do powierzchni projektowej.

     ![Projektowanie aplikacji ze sklepu Windows](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")

4. Kliknij dwukrotnie formant przycisku i Dodaj następujący kod:

    ```csharp
    private void button_Click_1(object sender, RoutedEventArgs e)
    {
        this.textBox.Text = this.button.Name;
    }

    ```

    ```vb
    Public NotInheritable Class MainPage
        Inherits Page

        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click
            Me.textBox.Text = Me.button.Name
        End Sub
    End Class
    ```

5. Naciśnij klawisz F5, aby uruchomić aplikację ze sklepu Windows.

## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji ze sklepu Windows

[Jak mogę utworzyć kodowane testy interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows (platformy UWP)?](#uwpapps)

1. Utwórz nowy projekt kodowanego testu interfejsu użytkownika dla aplikacji ze sklepu Windows.

    ![Nowy zakodowany interfejs użytkownika TET projekt &#40;aplikacji ze sklepu Windows&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")

2. Wybierz, aby edytować mapę interfejsu użytkownika za pomocą narzędzia krzyżyk.

    ![Wybierz pozycję Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")

3. Użyj narzędzia krzyżyka w konstruktorze kodowanego testu interfejsu użytkownika, aby wybrać kafelek aplikacji, kliknij prawym przyciskiem myszy pozycję **AutomationId** i wybierz polecenie **Kopiuj wartość do schowka**. Wartość w schowku zostanie później użyta do pisania akcji w celu uruchomienia aplikacji do testowania.

    ![Kopiuj AutomationId do schowka](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")

4. W uruchomionej aplikacji ze sklepu Windows użyj narzędzia krzyżyka, aby wybrać kontrolkę przycisk i kontrolkę TextBox. Po dodaniu każdej kontrolki wybierz przycisk **Dodaj formant do mapy kontrolek interfejsu użytkownika** na pasku narzędzi Konstruktor kodowanego testu interfejsu użytkownika.

    ![Dodawanie kontrolki do mapy interfejsu użytkownika](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")

5. Wybierz przycisk **Generuj kod** na pasku narzędzi Konstruktor kodowanego testu interfejsu użytkownika, a następnie wybierz polecenie **Generuj** , aby utworzyć kod dla zmian mapy formantów interfejsu użytkownika.

    ![Generuj kod dla mapy interfejsu użytkownika](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")

6. Wybierz przycisk, aby ustawić wartość w polu tekstowym.

    ![Kliknij formant przycisku, aby ustawić wartość TextBox](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")

7. Użyj narzędzia krzyżyk, aby zaznaczyć formant TextBox, a następnie wybierz właściwość **Text** .

    ![Wybierz właściwość Text](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")

8. Dodaj potwierdzenie. Zostanie ona użyta w teście, aby sprawdzić, czy wartość jest poprawna.

    ![Wybieranie testbox z krzyżykiem i dodawaniem&#45;](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")

9. Dodaj i Wygeneruj kod dla potwierdzenia.

     ![Generuj kod dla potwierdzenia TextBox](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")

10. **Visual C #**

     W Eksplorator rozwiązań otwórz plik UIMap.Designer.cs, aby wyświetlić dodany kod dla metody Assert i kontrolek.

     **Visual Basic**

     W Eksplorator rozwiązań otwórz plik CodedUITest1. vb, a następnie w kodzie metody testowej okno CodedUITestMethod1 () kliknij prawym przyciskiem myszy wywołanie metody assertion, która została automatycznie dodana, `Me.UIMap.AssertMethod1()` i wybierz polecenie **Przejdź do definicji**. Spowoduje to otwarcie pliku UIMap. Designer. vb w edytorze kodu, dzięki czemu można wyświetlić widok dodany kod dla metody Assert i kontrolek.

    > [!WARNING]
    > Nie należy modyfikować pliku UIMap.designer.cs ani UIMap. Designer. vb bezpośrednio. W takim przypadku zmiany wprowadzone w pliku zostaną nadpisywane przy każdym wygenerowaniu testu.

     **Assert — Metoda**

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Formanty**

    ```csharp
    #region Properties
    public XamlButton UIButtonButton
    {
        get
        {
            if ((this.mUIButtonButton == null))
            {
                this.mUIButtonButton = new XamlButton(this);
                #region Search Criteria
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";
                this.mUIButtonButton.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUIButtonButton;
        }
    }

    public XamlEdit UITextBoxEdit
    {
        get
        {
            if ((this.mUITextBoxEdit == null))
            {
                this.mUITextBoxEdit = new XamlEdit(this);
                #region Search Criteria
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";
                this.mUITextBoxEdit.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUITextBoxEdit;
        }
    }
    #endregion

    #region Fields
    private XamlButton mUIButtonButton;

    private XamlEdit mUITextBoxEdit;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
                Me.mUIButtonButton.WindowTitles.Add("App2")
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
                Me.mUITextBoxEdit.WindowTitles.Add("App2")
            End If
            Return Me.mUITextBoxEdit
        End Get
    End Property
    #End Region

    #Region "Fields"
    Private mUIButtonButton As XamlButton

    Private mUITextBoxEdit As XamlEdit
    #End Region
    ```

11. W Eksplorator rozwiązań otwórz plik CodedUITest1.cs lub CodedUITest1. vb. Teraz można dodać kod do metody CodedUTTestMethod1, aby akcje były wymagane do uruchomienia testu przy użyciu kontrolek dodanych do UIMap:

    1. Uruchom aplikację ze sklepu Windows, używając właściwości identyfikatora automatyzacji, która została wcześniej skopiowana do schowka:

       ```csharp
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")
       ```

       ```vb
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");
       ```

    2. Dodaj gest, aby nacisnąć kontrolkę Button:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)
       ```

    3. Upewnij się, że wywołanie metody Assert, która została wygenerowana automatycznie, nastąpi po uruchomieniu aplikacji, a następnie naciśnij pozycję gest na przycisku:

       ```csharp
       this.UIMap.AssertMethod1();
       ```

       ```vb
       Me.UIMap.AssertMethod1()
       ```

       Po dodaniu kodu metoda testowa okno CodedUITestMethod1 powinna wyglądać następująco:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.

        // Launch the app.
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest(CodedUITestType.WindowsStore)>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '

            ' Launch the app.
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

12. Skompiluj test, a następnie uruchom test za pomocą Eksploratora testów.

     ![Uruchamianie kodowanego testu interfejsu użytkownika z Eksploratora testów](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")

     Aplikacja ze sklepu Windows uruchamia się, Akcja do naciśnięcia przycisku jest zakończona, a właściwość tekstowa pola tekstowego jest wypełniana i sprawdzana przy użyciu metody Assert.

     ![Uruchamianie kodowanego testu interfejsu użytkownika](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")

     Po zakończeniu testu Eksplorator testów pokazuje, że test zakończył się.

     ![Testy zakończone w Eksploratorze testów](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")

## <a name="q--a"></a>Pytania i odpowiedzi

- **P: Dlaczego nie widzę opcji rejestrowania kodowanego testu interfejsu użytkownika w oknie dialogowym generowanie kodu dla kodowanego testu interfejsu użytkownika?**

     Odp **.: opcja**rejestrowania nie jest obsługiwana w przypadku aplikacji ze sklepu Windows.

- **P: Czy można utworzyć kodowany test interfejsu użytkownika dla aplikacji ze sklepu Windows w oparciu o WinJS?**

     Odp **.: nie**, obsługiwane są tylko aplikacje oparte na języku XAML.

- **P: Czy można utworzyć kodowane testy interfejsu użytkownika dla aplikacji ze sklepu Windows w systemie, który nie jest uruchomiony Windows 8.1 lub Windows 10?**

     Odp **.:** nie, szablony projektów kodowanego testu interfejsu użytkownika są dostępne tylko w systemach Windows 8.1 i Windows 10. Aby utworzyć automatyzację dla aplikacji platforma uniwersalna systemu Windows (platformy UWP), musisz mieć system Windows 10.

<a name="uwpapps"></a>
- **P: Jak mogę utworzyć kodowane testy interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows (platformy UWP)?**

   Odp **.: w**zależności od platformy, w której testowasz aplikację platformy UWP, Utwórz projekt kodowanego testu interfejsu użytkownika w jeden z następujących sposobów:

  - Aplikacja platformy UWP uruchomiona na komputerze lokalnym będzie działać jako aplikacja ze sklepu. Aby to przetestować, należy użyć szablonu **projektu kodowanego testu interfejsu użytkownika (Windows)** . Aby znaleźć ten szablon podczas tworzenia nowego projektu, **Przejdź do okna i** **uniwersalnego** węzła. Lub przejdź do okna **, systemu Windows** **8**, węzła **systemu Windows** .

  - Aplikacja platformy UWP uruchomiona na urządzeniu przenośnym lub emulatorze będzie uruchamiana jako aplikacja dla telefonu. Aby to przetestować, należy użyć szablonu **projektu kodowanego testu interfejsu użytkownika (Windows Phone)** . Aby znaleźć ten szablon podczas tworzenia nowego projektu, **Przejdź do okna i** **uniwersalnego** węzła. Lub przejdź do węzła **Windows**, **Windows 8** **Windows Phone** .

    Po utworzeniu projektu tworzenie testu pozostaje tak samo jak poprzednio.

- **P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap. Designer?**

   Odp **.: wszelkie**zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną nadpisywane przy każdym wygenerowaniu kodu za pomocą konstruktora kodowanego testu interfejsu użytkownika UIMap. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [Ustawianie unikatowej właściwości automatyzacji dla kontrolek sklepu Windows na potrzeby testowania](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
