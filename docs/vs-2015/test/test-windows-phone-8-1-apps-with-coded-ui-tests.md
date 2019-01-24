---
title: Testowanie za pomocą kodowanych testów interfejsu użytkownika Windows platformy UWP i 8.1 Phone | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74d86998657a380e4cef1f3ee6ca0d87bccb3507
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765102"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Testowanie aplikacji platformy UWP i 8.1 Phone systemu Windows za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj tego przewodnika dotyczący tworzenia testów interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows, uruchamianych na urządzeniu przenośnym lub emulatorów i aplikacji opartych na XAML Phone 8.1.   
  
## <a name="create-a-simple-windows-phone-app"></a>Utwórz prostą aplikację Windows Phone  
  
1.  Utwórz nowy projekt dla pustej aplikacji Windows Phone przy użyciu szablonu programu Visual C# lub Visual Basic.  
  
     ![Utwórz nową aplikację Windows Phone](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")  
  
2.  W Eksploratorze rozwiązań Otwórz plik MainPage.xaml. Z przybornika przeciągnij formant przycisku i formant pola tekstowego na powierzchnię projektową.  
  
     ![Dodawanie i kształty do pliku MainPage.xaml](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")  
  
3.  W oknie dialogowym właściwości nazwę kontrolki przycisku.  
  
     ![Nazwij kontrolkę przycisku](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")  
  
4.  Nazwij formant pola tekstowego.  
  
     ![Nazwij formant pola tekstowego](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")  
  
5.  Na powierzchni projektowej kliknij dwukrotnie formant przycisku, a następnie dodaj następujący kod:  
  
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
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację Windows Phone w emulatorze i sprawdź, czy działa.  
  
     ![Uruchom Windows Phone app](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")  
  
7.  Zamknij emulatora.  
  
## <a name="deploy-the-windows-phone-app"></a>Windows Phone wdrażanie aplikacji  
  
1.  Przed kodowanego testu interfejsu użytkownika można mapować kontrolki aplikacji, musisz wdrożyć tę aplikację.  
  
     ![Wdrażanie Windows Phone app](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")  
  
     Zostanie uruchomiony emulator. Aplikacja jest teraz dostępna do testowania.  
  
     ![Aplikacja wdrożona w emulatorze](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")  
  
     Zachowaj emulator uruchomiony podczas tworzenie kodowanego testu interfejsu użytkownika.  
  
## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji Windows Phone  

[Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy Windows (UWP)?](#uwpapps)
  
1. Dodaj nowy projekt kodowanego testu interfejsu użytkownika do rozwiązania przy użyciu aplikacji Windows Phone.  
  
    ![Utwórz nowy kodowany test interfejsu użytkownika dla Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")  
  
2. Wybrać opcję Edytuj mapę interfejsu użytkownika przy użyciu narzędzia krzyżyk.  
  
    ![Generowanie kodowanego interfejsu użytkownika testu za pomocą wielu&#45;narzędzie włosów. ](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")  
  
3. Użyj narzędzia krzyżyk, aby wybrać aplikację, a następnie skopiuj wartość w aplikacji **AutomationId** właściwość, która będzie później używany do uruchomienia aplikacji w teście.  
  
    ![Skopiuj wartość AutomationId aplikacji](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")  
  
4. W emulatorze należy uruchomić aplikację i użyj narzędzia krzyżyk, aby wybrać formant przycisku. Następnie można dodać kontrolkę przycisku do mapy formantów interfejsu użytkownika.  
  
    ![Użyj krzyżowego&#45;narzędzie włosów do kontrolki mapy](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")  
  
5. Aby dodać formant pola tekstowego do mapy formantów interfejsu użytkownika, powtórz poprzedni krok.  
  
    ![Użyj krzyżowego&#45;włosów Mapa i narzędzia do kontrolki textbox](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")  
  
6. Generuj kod, aby utworzyć kod dla zmiany mapy formantów interfejsu użytkownika.  
  
    ![Generowanie kodu na podstawie konstruktora](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")  
  
7. Użyj narzędzia krzyżyk aby zaznaczyć formant pola tekstowego, a następnie wybierz **tekstu** właściwości.  
  
    ![Wybierz właściwość Text](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")  
  
8. Dodaj potwierdzenie. Będzie on używany w teście Aby sprawdzić, czy wartość jest poprawna.  
  
    ![Dodaj potwierdzenie do testu](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")  
  
9. Dodaj i wygeneruj kod dla metody assert.  
  
     ![Generuj kod dla potwierdzenia](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")  
  
10. **Visual C#**  
  
     W Eksploratorze rozwiązań Otwórz plik UIMap.Designer.cs, aby wyświetlić kod, który właśnie został dodany dla metody assert i formantów.  
  
     **Visual Basic**  
  
     W Eksploratorze rozwiązań Otwórz plik CodedUITest1.vb. W CodedUITestMethod1() przetestować kod metody, kliknij prawym przyciskiem myszy wywołanie metody asercji, do której została dodana automatycznie `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. Spowoduje to otwarcie plik UIMap.Designer.vb w edytorze kodu, aby można było wyświetlić kod, który został dodany dla metody assert i formantów.  
  
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
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Kontrolki**  
  
    ```csharp  
    #region Properties  
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues  
    {  
        get  
        {  
            if ((this.mAssertMethod1ExpectedValues == null))  
            {  
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();  
            }  
            return this.mAssertMethod1ExpectedValues;  
        }  
    }  
  
    public UIApp1Window UIApp1Window  
    {  
        get  
        {  
            if ((this.mUIApp1Window == null))  
            {  
                this.mUIApp1Window = new UIApp1Window();  
            }  
            return this.mUIApp1Window;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;  
  
    private UIApp1Window mUIApp1Window;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
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
  
11. W Eksploratorze rozwiązań Otwórz plik CodedUITest1.cs lub CodedUITest1.vb. Teraz można dodać kod do metody codeduttestmethod1 gdyż działania wymagane do uruchomienia testu. Za pomocą formantów dodanych do UIMap, aby dodać kod:  
  
    1. Uruchom aplikację Windows Phone za pomocą właściwości automatyzacji Identyfikatora poprzednio skopiowane do Schowka:  
  
       ```csharp  
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
       ```vb  
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
    2. Dodaj gest, aby dotknąć przycisku sterowania:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
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
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
            ' Launch the app.  
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
## <a name="run-the-coded-ui-test"></a>Uruchom kodowany test interfejsu użytkownika  
  
1.  Skompiluj test, a następnie uruchom test za pomocą narzędzia Eksplorator testów.  
  
     ![Skompiluj i uruchom test za pomocą Eksploratora testów](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")  
  
     Uruchamia aplikację Windows Phone, działanie naciśnięcie przycisku jest zakończona, a tekst w polu tekstowym właściwości jest wypełniana i sprawdzana za pomocą metody assert.  
  
     ![Uruchamianie testu systemu Windows Phone](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")  
  
     Po zakończeniu testu Eksplorator testów potwierdza, że test jest zaliczony.  
  
     ![Wyniki w Eksploratorze testów](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")  
  
##  <a name="TestingPhoneAppsCodedUI_DataDriven"></a> Opartych na danych kodowanych testów interfejsu użytkownika dla aplikacji Windows Phone  
 Na potrzeby testowania różnych warunków, kodowany test interfejsu użytkownika można uruchamiać wiele razy z różnymi zestawami danych.  
  
 Oparte na danych kodowanych testów interfejsu użytkownika dla Windows Phone są definiowane dla metody testowej przy użyciu atrybutu wiersza danych. W poniższym przykładzie, x i y Użyj wartości 1 i 2 dla pierwszej iteracji i -1 -2 dla drugiego iteracji testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>PYT.: Trzeba wdrożyć aplikację Windows Phone w emulatorze do mapy formantów interfejsu użytkownika?  
 **A**: Tak, kodowanego testu interfejsu użytkownika wymaga, aby być uruchomiony emulator, a aplikacji można wdrożyć do niego. W przeciwnym razie zgłosi komunikat o błędzie informujący o tym, nie uruchomionego emulatora został odnaleziony.  
  
###  <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> Q: Testy można wykonać na tylko emulator, czy też korzystać urządzenia fizycznego?  
 **A**: Jedną z opcji jest obsługiwane. Element docelowy dla wykonywania testów jest zaznaczone, zmieniając typ emulatora lub wybierając urządzenie, na pasku narzędzi urządzenia. Jeśli urządzenie jest wybrane, niebieski Phone urządzenie musi być podłączone do jednego z portów USB komputera.  
  
 ![Wybierz dla wersji emulatora lub urządzenia fizyczne](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")  
  
### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>PYT.: Dlaczego nie widzę opcji zapisu mojego kodowanego testu interfejsu użytkownika w Generuj kod dla kodowanego testu interfejsu użytkownika okna dialogowego  
 **A**: Opcja zapisu nie jest obsługiwana dla aplikacji Windows Phone.  
  
### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>PYT.: Czy można utworzyć kodowany test interfejsu użytkownika, dla mojej aplikacji Windows Phone, na podstawie WinJS, Silverlight lub HTML5?  
 **A**: Nie, obsługiwane są tylko aplikacje na podstawie XAML.  
  
### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>PYT.: Czy mogę utworzyć kodowane testy interfejsu użytkownika dla mojej aplikacji Windows Phone w systemie, który nie jest uruchomiony, Windows 8.1 lub Windows 10?  
 **A**: Nie, szablony projekt kodowanego testu interfejsu użytkownika są dostępne tylko w Windows 8.1 i Windows 10. Aby utworzyć automatyzacji dla aplikacji uniwersalnych platformy Windows (UWP), należy systemu Windows 10.  

<a name="uwpapps"></a>  
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>PYT.: Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy Windows (UWP)?  
 **A**: W zależności od platformy, na którym testujesz aplikację platformy uniwersalnej systemu Windows należy utworzyć kodowane testy interfejsu użytkownika w jednym z następujących sposobów:  
  
- Aplikacja platformy uniwersalnej systemu Windows, uruchomiony na komputerze lokalnym zostanie uruchomiony jako Store app. Aby to przetestować, należy użyć **projekt kodowanego interfejsu użytkownika testu (Windows)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **Universal** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows** węzła.  
  
- Uruchamianie na urządzeniu przenośnym lub w emulatorze aplikacji platformy UWP działa jako aplikację na telefon. Aby to przetestować, należy użyć **projekt kodowanego interfejsu użytkownika testu (Windows Phone)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **Universal** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows Phone** węzła.  
  
  Po utworzeniu projektu, tworzenia testu pozostaje taka sama jak przed.  
  
### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>PYT.: Czy mogę wybrać formanty, które wykraczają poza emulator  
 **A**: Nie, Konstruktor nie wykryje je.  
  
### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>PYT.: Do kontrolki za pomocą urządzenia fizycznego telefonu mapy może używać konstruktora kodowanego testu interfejsu użytkownika?  
 **A**: Nie, Konstruktor tylko można mapować elementy interfejsu użytkownika, jeśli aplikacja została wdrożona w emulatorze.  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>PYT.: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?  
 **A**: Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>PYT.: Można uruchomić kodowany test interfejsu użytkownika w mojej aplikacji Windows Phone z wiersza polecenia?  
 **A**: Tak, użyj pliku runsettings określić urządzenie docelowe dla wykonywania testów. Na przykład:  
  
 **/settings:devicetarget.runsettings "pathToYourCodedUITestDll" vstest.Console.exe**  
  
 Przykładowy plik runsettings:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
<MSPhoneTest>  
<!--to specify test execution on device, use a TargetDevice option as follows-->  
<TargetDevice>Device</TargetDevice>  
<!--to specify an emulator instead, use a TargetDevice option like below-->  
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->  
</MSPhoneTest>  
</RunSettings>  
```  
  
### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>PYT.: Jakie są różnice między aplikacjami Windows Phone i kodowane testy interfejsu użytkownika dla aplikacji opartych na XAML Windows Store?  
 **A**: Poniżej przedstawiono niektóre podstawowe różnice:  
  
|Funkcja|Aplikacje Windows Store|Aplikacje Windows Phone|  
|-------------|------------------------|------------------------|  
|Element docelowy dla wykonywania testów|Komputerze lokalnym lub zdalnym. Komputer zdalny można określić, gdy automatyczny przypadek testowy można używać do uruchamiania testów. Zobacz [zautomatyzować przypadek testowy w programie Microsoft Test Manager](http://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Urządzenie lub emulator. Zobacz, [Pyt.: Testy można wykonać na tylko emulator, czy też korzystać urządzenia fizycznego? ](#TestingPhoneAppsCodedUI_EmulatorDevice) w tym temacie.|  
|Wykonywanie z wiersza polecenia|Plik ustawień nie są wymagane do określenia docelowej.|Wymagany do określenia docelowej pliku Runsettings.|  
|Wyspecjalizowane klasy formantów powłoki|<xref:Microsoft.VisualStudio.TestTools.UITesting.DirectUIControls.DirectUIControl>|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|  
|Kontrolki WebView w aplikacji w języku XAML|Obsługiwane, jeśli używasz Html * wyspecjalizowane klasy do interakcji z elementów HTML. Zobacz <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Nieobsługiwane.|  
|Wykonywanie zautomatyzowanych testów z MTM|Obsługiwane.|Nieobsługiwane.|  
|Testy oparte na danych|Zobacz [testów opartych na danych](../test/creating-a-data-driven-coded-ui-test.md) informacje za pomocą zewnętrznych źródeł danych i przy użyciu źródła danych i atrybutu dla metody testowej.|Dane są określone w jednej linii, za pomocą atrybutu wiersza danych dla metody testowej. Zobacz [opartych na danych użyj kodowanych testów interfejsu użytkownika dla aplikacji Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) w tym temacie.|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Blog programu Microsoft Visual Studio Application Lifecycle Management: [Za pomocą kodowanego interfejsu użytkownika do testowania aplikacji Windows Phone opartych na XAML](http://blogs.msdn.com/b/visualstudioalm/archive/2014/04/05/using-coded-ui-to-test-xaml-based-windows-phone-apps.aspx?PageIndex=2#comments)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
