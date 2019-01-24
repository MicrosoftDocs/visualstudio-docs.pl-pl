---
title: Testowanie Windows platformy UWP i 8.1 Store Apps za pomocą kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e8d7f1bf475dca7ed0e06e4b3ebb045b0513d5b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799300"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Testowanie Windows platformy UWP i 8.1 Store Apps za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj tego przewodnika dotyczący tworzenia testów interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows i aplikacji opartych na XAML 8.1 Store.
  
## <a name="create-a-simple-windows-store-app"></a>Utwórz prostą aplikację Windows Store  
  
1.  Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji opartych na XAML Windows Store, musisz najpierw [Ustawianie unikatowej właściwości automatyzacji, który identyfikował każdy formant](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Na **narzędzia** menu wskaż **opcje** , a następnie wybierz **edytora tekstów**, następnie **XAML**, a na koniec **różne** .  
  
     Zaznacz pole wyboru, aby automatycznie nadawać nazwy elementom interaktywnym podczas ich tworzenia.  
  
     ![XAML — różne opcje](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
2.  Utwórz nowy projekt dla pustego XAML opartych na aplikacji Windows Store przy użyciu szablonu programu Visual C# lub Visual Basic.  
  
     ![Tworzenie pustej aplikacji Windows Store &#40;XAML&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  W Eksploratorze rozwiązań Otwórz plik MainPage.xaml. Z przybornika przeciągnij formant przycisku i formant pola tekstowego na powierzchnię projektową.  
  
     ![Projektowanie aplikacji Windows Store](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Kliknij dwukrotnie formant przycisku i Dodaj następujący kod:  
  
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
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację Windows Store.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji Windows Store  

[Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy Windows (UWP)?](#uwpapps)
  
1. Utwórz nowy kodowane testy interfejsu użytkownika dla aplikacji Windows Store.  
  
    ![Nowy projekt kodowanego interfejsu użytkownika tet &#40;aplikacji Windows Store Apps&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")  
  
2. Wybrać opcję Edytuj mapę interfejsu użytkownika przy użyciu narzędzia krzyżyk.  
  
    ![Wybierz opcję Edytuj mapę interfejsu użytkownika lub Dodaj potwierdzenia](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3. Użyj narzędzia krzyżyk w Konstruktorze kodowanego testu interfejsu użytkownika wybierz Kafelek aplikacji, kliknij prawym przyciskiem myszy **AutomationId** i wybierz polecenie **wartość kopiowania do Schowka**. Wartość w Schowku będzie później używane podczas pisania akcji do uruchomienia aplikacji na potrzeby testowania.  
  
    ![Kopiuj AutomationId do Schowka](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4. W uruchomionej aplikacji Windows Store należy użyć narzędzia krzyżyka zaznacz formant przycisku i formant pola tekstowego. Po dodaniu każdego formantu wybierz **dodać formant do mapy formantów UI** przycisku na pasku narzędzi Konstruktor kodowanego testu interfejsu użytkownika.  
  
    ![Dodać formant do mapy interfejsu użytkownika](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5. Wybierz **Generuj kod** przycisk na pasku narzędzi Konstruktor kodowanego testu interfejsu użytkownika, a następnie wybierz **Generuj** utworzyć kod dla zmiany mapy formantów interfejsu użytkownika.  
  
    ![Generuj kod dla mapy interfejsu użytkownika](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")  
  
6. Wybierz przycisk, aby ustawić wartość w polu tekstowym.  
  
    ![Kliknij formant przycisku, aby ustawić wartość w polu tekstowym](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7. Użyj narzędzia krzyżyk aby zaznaczyć formant pola tekstowego, a następnie wybierz **tekstu** właściwości.  
  
    ![Wybierz właściwość Text](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8. Dodaj potwierdzenie. Będzie on używany w teście Aby sprawdzić, czy wartość jest poprawna.  
  
    ![Wybierz testbox za pomocą wielu&#45;włosów i Dodaj potwierdzenie](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Dodaj i wygeneruj kod dla potwierdzenia.  
  
     ![Generuj kod dla potwierdzenia textbox](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     W Eksploratorze rozwiązań Otwórz plik UIMap.Designer.cs, aby wyświetlić dodany kod dla metody assert i formantów.  
  
     **Visual Basic**  
  
     W Eksploratorze rozwiązań Otwórz plik CodedUITest1.vb, a następnie w metoda testowej codeduitestmethod1() kliknij prawym przyciskiem myszy wywołanie metody asercji, do której została dodana automatycznie `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. Spowoduje to otwarcie plik UIMap.Designer.vb w edytorze kodu, co pozwala na wyświetlanie widoku dodanego kodu dla metody assert i formantów.  
  
    > [!WARNING]
    >  Nie należy modyfikować pliku UIMap.designer.cs lub UIMap.Designer.vb bezpośrednio. Jeśli to zrobisz, zmiany w pliku zostaną zastąpione każdorazowo, gdy test jest generowany.  
  
     **Assert — metoda**  
  
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
  
     **Kontrolki**  
  
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
  
11. W Eksploratorze rozwiązań Otwórz plik CodedUITest1.cs lub CodedUITest1.vb. Teraz można dodać kod do metody codeduttestmethod1 gdyż działania muszą uruchomić test za pomocą formantów dodanych do UIMap:  
  
    1. Uruchom aplikację Windows Store za pomocą właściwości automatyzacji Identyfikatora poprzednio skopiowane do Schowka:  
  
       ```csharp  
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
       ```  
  
       ```vb  
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
       ```  
  
    2. Dodaj gest, aby dotknąć przycisku sterowania:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
       ```  
  
    3. Sprawdź, czy wywołanie metody assert, które zostało wygenerowane automatycznie przychodzi po uruchomieniu aplikacji, a następnie wybierz gest na przycisku:  
  
       ```csharp  
       this.UIMap.AssertMethod1();  
       ```  
  
       ```vb  
       Me.UIMap.AssertMethod1()  
       ```  
  
       Po dodaniu kodu metoda testu CodedUITestMethod1 powinna wyglądać następująco:  
  
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
  
12. Skompiluj test, a następnie uruchom test za pomocą narzędzia Eksplorator testów.  
  
     ![Uruchamianie kodowanego testu interfejsu użytkownika z Eksploratora testów](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Uruchamia aplikację Windows Store, akcji naciśnięcie przycisku jest zakończona i tekst w polu tekstowym właściwości jest wypełniana i sprawdzana za pomocą metody assert.  
  
     ![Uruchamianie kodowanego testu interfejsu użytkownika](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")  
  
     Po zakończeniu testu Eksplorator testów Wyświetla, że test jest zaliczony.  
  
     ![Przekazano Wyświetla test w Eksploratorze testów](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
-   **PYT.: Dlaczego nie widzę opcji zapisu mojego kodowanego testu interfejsu użytkownika w Generuj kod dla kodowanego testu interfejsu użytkownika okna dialogowego**  
  
     **A**: Opcja zapisu nie jest obsługiwana dla aplikacji Windows Store.  
  
-   **PYT.: Można utworzyć kodowany test interfejsu użytkownika dla Moje aplikacje Windows Store, w oparciu o WinJS?**  
  
     **A**: Nie, obsługiwane są tylko aplikacje na podstawie XAML.  
  
-   **PYT.: Czy mogę utworzyć kodowane testy interfejsu użytkownika dla mojej aplikacji Windows Store w systemie, który nie jest uruchomiony, Windows 8.1 lub Windows 10?**  
  
     **A**: Nie, szablony projekt kodowanego testu interfejsu użytkownika są dostępne tylko w Windows 8.1 i Windows 10. Aby utworzyć automatyzacji dla aplikacji uniwersalnych platformy Windows (UWP), należy systemu Windows 10.  

<a name="uwpapps"></a>
- **PYT.: Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy Windows (UWP)?**  
  
   **A**: W zależności od platformy, na którym testujesz aplikację platformy uniwersalnej systemu Windows należy utworzyć kodowane testy interfejsu użytkownika w jednym z następujących sposobów:  
  
  - Aplikacja platformy uniwersalnej systemu Windows, uruchomiony na komputerze lokalnym zostanie uruchomiony jako Store app. Aby to przetestować, należy użyć **projekt kodowanego interfejsu użytkownika testu (Windows)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **Universal** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows** węzła.  
  
  - Uruchamianie na urządzeniu przenośnym lub w emulatorze aplikacji platformy UWP działa jako aplikację na telefon. Aby to przetestować, należy użyć **projekt kodowanego interfejsu użytkownika testu (Windows Phone)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **Universal** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows Phone** węzła.  
  
    Po utworzeniu projektu, tworzenia testu pozostaje taka sama jak przed.  
  
- **PYT.: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?**  
  
   **A**: Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Ustawianie unikatowej właściwości automatyzacji dla kontrolek Sklepu Windows przeznaczonych do testowania](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
