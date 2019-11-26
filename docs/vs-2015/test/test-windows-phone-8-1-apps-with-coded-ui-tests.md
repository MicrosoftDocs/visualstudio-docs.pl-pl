---
title: Testowanie aplikacji dla telefonów z systemem Windows platformy UWP i 8,1 przy użyciu kodowanych testów interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f2ac13b62dcc522626fde92b1b29cac9873edec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301840"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Testowanie aplikacji platformy UWP i 8.1 Phone systemu Windows za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik służy do tworzenia testów interfejsu użytkownika dla aplikacji platformy UWP, które działają na urządzeniach przenośnych lub emulatorach oraz aplikacjach telefonujących opartych na języku XAML 8,1.

## <a name="create-a-simple-windows-phone-app"></a>Tworzenie prostej aplikacji Windows Phone

1. Utwórz nowy projekt dla pustej aplikacji Windows Phone przy użyciu szablonu wizualizacji C# lub Visual Basic.

     ![Tworzenie nowej aplikacji Windows Phone](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")

2. W Eksplorator rozwiązań otwórz MainPage. XAML. Z przybornika przeciągnij kontrolkę Button i kontrolkę TextBox do powierzchni projektowej.

     ![Dodawanie kształty do MainPage. XAML](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")

3. W okno Właściwości Nadaj formantowi przycisk.

     ![Nazwij kontrolkę Button](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")

4. Nadaj nazwę formantowi TextBox.

     ![Nadaj nazwę formantowi TextBox](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")

5. Na powierzchni projektanta kliknij dwukrotnie formant Button i Dodaj następujący kod:

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

6. Naciśnij klawisz F5, aby uruchomić aplikację Windows Phone w emulatorze i sprawdź, czy działa.

     ![Uruchamianie aplikacji Windows Phone](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")

7. Zamknij emulator.

## <a name="deploy-the-windows-phone-app"></a>Wdrażanie aplikacji Windows Phone

1. Zanim kodowany test interfejsu użytkownika będzie mógł zmapować kontrolki aplikacji, należy wdrożyć aplikację.

     ![Wdrażanie aplikacji Windows Phone](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")

     Emulator rozpocznie działanie. Aplikacja jest teraz dostępna do testowania.

     ![Aplikacja wdrożona na emulatorze](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")

     Kontynuuj działanie emulatora podczas tworzenia kodowanego testu interfejsu użytkownika.

## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji Windows Phone

[Jak mogę utworzyć kodowane testy interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows (platformy UWP)?](#uwpapps)

1. Dodaj nowy kodowany projekt testu interfejsu użytkownika do rozwiązania za pomocą aplikacji Windows Phone.

    ![Utwórz nowy kodowany test interfejsu użytkownika dla Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")

2. Wybierz, aby edytować mapę interfejsu użytkownika za pomocą narzędzia krzyżyk.

    ![Generowanie kodowanego testu interfejsu użytkownika&#45;za pomocą narzędzia krzyżyk.](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")

3. Użyj narzędzia krzyżyka, aby wybrać aplikację, a następnie skopiuj wartość właściwości **AutomationId** aplikacji, która zostanie użyta później do uruchomienia aplikacji w teście.

    ![Skopiuj wartość AutomationId aplikacji](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")

4. W emulatorze Uruchom aplikację i użyj narzędzia krzyżyka, aby zaznaczyć formant przycisku. Następnie Dodaj kontrolkę Button do mapy formantów interfejsu użytkownika.

    ![&#45;Używanie narzędzia krzyżyk do mapowania formantów](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")

5. Aby dodać kontrolkę TextBox do mapy formantów interfejsu użytkownika, Powtórz poprzedni krok.

    ![Użyj narzędzia krzyżyk&#45;i Mapuj formant TextBox](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")

6. Generuj kod, aby utworzyć kod dla zmian mapy formantów interfejsu użytkownika.

    ![Generuj kod z konstruktora](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")

7. Użyj narzędzia krzyżyk, aby zaznaczyć formant TextBox, a następnie wybierz właściwość **Text** .

    ![Wybierz właściwość Text](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")

8. Dodaj potwierdzenie. Zostanie ona użyta w teście, aby sprawdzić, czy wartość jest poprawna.

    ![Dodaj potwierdzenie do testu](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")

9. Dodaj i Generuj kod dla metody Assert.

     ![Generuj kod dla potwierdzenia](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")

10. **Visual C#**

     W Eksplorator rozwiązań otwórz plik UIMap.Designer.cs, aby wyświetlić właśnie dodany kod dla metody Assert i kontrolek.

     **Visual Basic**

     W Eksplorator rozwiązań otwórz plik CodedUITest1. vb. W kodzie metody testowej okno CodedUITestMethod1 () kliknij prawym przyciskiem myszy wywołanie metody assertion, która została automatycznie dodana `Me.UIMap.AssertMethod1()` i wybierz **Przejdź do definicji**. Spowoduje to otwarcie pliku UIMap. Designer. vb w edytorze kodu, dzięki czemu można wyświetlić kod dodany dla metody Assert i kontrolek.

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

11. W Eksplorator rozwiązań otwórz plik CodedUITest1.cs lub CodedUITest1. vb. Teraz można dodać kod do metody CodedUTTestMethod1 dla akcji wymaganych do uruchomienia testu. Użyj kontrolek, które zostały dodane do UIMap w celu dodania kodu:

    1. Uruchom aplikację Windows Phone przy użyciu właściwości identyfikatora automatyzacji skopiowanej wcześniej do schowka:

       ```csharp
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

       ```vb
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

    2. Dodaj gest, aby nacisnąć kontrolkę Button:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)
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

## <a name="run-the-coded-ui-test"></a>Uruchamianie kodowanego testu interfejsu użytkownika

1. Skompiluj test, a następnie uruchom test za pomocą Eksploratora testów.

     ![Kompiluj i uruchamiaj test za pomocą Eksploratora testów](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")

     Zostanie uruchomiona aplikacja Windows Phone, Akcja do naciśnięcia przycisku zostanie zakończona, a właściwość tekstowa pola tekstowego jest wypełniana i sprawdzana przy użyciu metody Assert.

     ![Uruchamianie testu telefonu Winodws](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")

     Po zakończeniu testu Eksplorator testów potwierdza, że test zakończył się.

     ![Wyniki Eksploratora testów](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")

## <a name="TestingPhoneAppsCodedUI_DataDriven"></a>Korzystanie z kodowanych testów interfejsu użytkownika opartych na danych na Windows Phone aplikacjach
 Aby przetestować inne warunki, kodowany test interfejsu użytkownika może być uruchamiany wiele razy z różnymi zestawami danych.

 Kodowane testy interfejsu użytkownika oparte na danych dla Windows Phone są definiowane przy użyciu atrybutu DataRow dla metody testowej. W poniższym przykładzie x i y używają wartości 1 i 2 dla pierwszej iteracji i-1 i-2 dla drugiej iteracji testu.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>P: Czy muszę wdrożyć aplikację Windows Phone w emulatorze w celu zamapowania formantów interfejsu użytkownika?
 Odp **.: tak**, Konstruktor kodowanego testu interfejsu użytkownika wymaga uruchomienia emulatora i wdrożenia aplikacji. W przeciwnym razie zgłosi komunikat o błędzie informujący, że nie można odnaleźć działającego emulatora.

### <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a>P: czy testy można wykonać tylko na emulatorze, czy też użyć urządzenia fizycznego?
 Odp **.: Każda**opcja jest obsługiwana. Element docelowy do wykonania testu jest wybierany przez zmianę typu emulatora lub wybranie urządzenia na pasku narzędzi urządzenia. Jeśli urządzenie jest zaznaczone, urządzenie niebieskie musi być podłączone do jednego z portów USB maszyny.

 ![Wybierz wersję emulatora lub urządzenie physcial](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>P: Dlaczego nie widzę opcji rejestrowania kodowanego testu interfejsu użytkownika w oknie dialogowym generowanie kodu dla kodowanego testu interfejsu użytkownika?
 Odp **.: opcja**rejestrowania nie jest obsługiwana w przypadku aplikacji Windows Phone.

### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>P: Czy można utworzyć kodowany test interfejsu użytkownika dla aplikacji Windows Phone w oparciu o WinJS, Silverlight lub HTML5?
 Odp **.: nie**, obsługiwane są tylko aplikacje oparte na języku XAML.

### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>P: Czy można tworzyć kodowane testy interfejsu użytkownika dla aplikacji Windows Phone w systemie, który nie jest uruchomiony Windows 8.1 lub Windows 10?
 Odp **.:** nie, szablony projektów kodowanego testu interfejsu użytkownika są dostępne tylko w systemach Windows 8.1 i Windows 10. Aby utworzyć automatyzację dla aplikacji platforma uniwersalna systemu Windows (platformy UWP), musisz mieć system Windows 10.

<a name="uwpapps"></a>
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>P: Jak mogę utworzyć kodowane testy interfejsu użytkownika dla aplikacji platforma uniwersalna systemu Windows (platformy UWP)?
 Odp **.: w**zależności od platformy, w której testowasz aplikację platformy UWP, Utwórz projekt kodowanego testu interfejsu użytkownika w jeden z następujących sposobów:

- Aplikacja platformy UWP uruchomiona na komputerze lokalnym będzie działać jako aplikacja ze sklepu. Aby to przetestować, należy użyć szablonu **projektu kodowanego testu interfejsu użytkownika (Windows)** . Aby znaleźć ten szablon podczas tworzenia nowego projektu, **Przejdź do okna i** **uniwersalnego** węzła. Lub przejdź do okna **, systemu Windows** **8**, węzła **systemu Windows** .

- Aplikacja platformy UWP uruchomiona na urządzeniu przenośnym lub emulatorze będzie uruchamiana jako aplikacja dla telefonu. Aby to przetestować, należy użyć szablonu **projektu kodowanego testu interfejsu użytkownika (Windows Phone)** . Aby znaleźć ten szablon podczas tworzenia nowego projektu, **Przejdź do okna i** **uniwersalnego** węzła. Lub przejdź do węzła **Windows**, **Windows 8** **Windows Phone** .

  Po utworzeniu projektu tworzenie testu pozostaje tak samo jak poprzednio.

### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>P: Czy mogę wybrać kontrolki, które znajdują się poza emulatorem?
 Odp **.: nie**, Konstruktor nie będzie wykrywał.

### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>P: Czy można użyć konstruktora kodowanego testu interfejsu użytkownika do mapowania kontrolek za pomocą fizycznego urządzenia telefonicznego?
 Odp.: nie, Konstruktor może mapować tylko elementy interfejsu **użytkownika, jeśli**aplikacja została wdrożona do emulatora.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap. Designer?
 Odp **.: wszelkie**zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną nadpisywane przy każdym wygenerowaniu kodu za pomocą konstruktora kodowanego testu interfejsu użytkownika UIMap. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.

### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>P: Czy można uruchomić kodowany test interfejsu użytkownika w aplikacji Windows Phone z poziomu wiersza polecenia?
 Odp **.: tak**, użyj pliku runsettings, aby określić urządzenie docelowe dla wykonywania testów. Na przykład:

 **VSTest. Console. exe "pathToYourCodedUITestDll"/Settings: devicetarget. runsettings**

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

### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>P: Jakie są różnice między kodowanymi testami interfejsu użytkownika dla aplikacji ze sklepu Windows opartych na języku XAML i aplikacji Windows Phone?
 Odp **.: są to następujące**podstawowe różnice:

|Funkcja|Aplikacje Windows Store|Aplikacje Windows Phone|
|-------------|------------------------|------------------------|
|Cel dla uruchomionych testów|Komputer lokalny lub zdalny. Komputery zdalne można określić w przypadku używania zautomatyzowanego przypadku testowego do uruchamiania testów. Zobacz [Automatyzowanie przypadku testowego w Microsoft Test Manager](https://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Emulator lub urządzenie. Zobacz, [p: czy testy można wykonać tylko na emulatorze, czy też użyć urządzenia fizycznego?](#TestingPhoneAppsCodedUI_EmulatorDevice) w tym temacie.|
|Wykonywanie z wiersza polecenia|Plik ustawień nie jest wymagany do określenia celu.|Plik runsettings jest wymagany do określenia celu.|
|Wyspecjalizowane klasy dla formantów powłoki|[DirectUIControl](/previous-versions/dn248208(v=vs.140))|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|
|Kontrolka WebView w aplikacji XAML|Obsługiwane w przypadku używania specjalnych klas języka HTML * do współpracy z elementami HTML. Zobacz <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Nieobsługiwane.|
|Wykonaj testy automatyczne z MTM|Obsługiwał.|Nieobsługiwane.|
|Testy oparte na danych|Zobacz [testy oparte na danych](../test/creating-a-data-driven-coded-ui-test.md) , aby uzyskać informacje na temat używania zewnętrznych źródeł danych i używania atrybutu DataSource w metodzie testowej.|Dane są określane jako wbudowane, przy użyciu atrybutu DataRow dla metody testowej. Zobacz [Używanie kodowanych testów interfejsu użytkownika opartych na danych w aplikacjach Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) w tym temacie.|

## <a name="external-resources"></a>Zasoby zewnętrzne
 Blog dotyczący zarządzania cyklem życia aplikacji Microsoft Visual Studio: [Używanie kodowanego interfejsu użytkownika do testowania aplikacji Windows Phone opartych na języku XAML](https://devblogs.microsoft.com/devops/using-coded-ui-to-test-xaml-based-windows-phone-apps/#comments)

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
