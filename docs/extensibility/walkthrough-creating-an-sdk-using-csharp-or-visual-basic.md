---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic | Microsoft Docs'
description: Dowiedz się, jak utworzyć prosty zestaw SDK biblioteki matematycznej za pomocą języka Visual C#, a następnie spakować zestaw SDK jako rozszerzenie programu Visual Studio, korzystając z tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b44566e4a8df323af6132128a8881b54c6f493f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217297"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic
W tym instruktażu dowiesz się, jak utworzyć prosty zestaw SDK biblioteki matematycznej za pomocą języka Visual C#, a następnie spakować zestaw SDK jako rozszerzenie programu Visual Studio (VSIX). Należy wykonać następujące procedury:

- [Aby utworzyć składnik środowisko wykonawcze systemu Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Aby utworzyć składnik środowisko wykonawcze systemu Windows SimpleMath

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście szablonów rozwiń pozycję **Visual C#** lub **Visual Basic**, wybierz węzeł **Sklep Windows** , a następnie wybierz szablon **składnika Środowisko wykonawcze systemu Windows** .

3. W polu **Nazwa** Określ **SimpleMath**, a następnie wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła projektu **SimpleMath** , a następnie wybierz polecenie **Właściwości**.

5. Zmień nazwę **Class1. cs** na wartość **arytmetyczną. cs** i zaktualizuj ją w celu dopasowania do następującego kodu:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła **rozwiązanie "SimpleMath"** , a następnie wybierz pozycję **Configuration Manager**.

    Zostanie otwarte okno dialogowe **Configuration Manager** .

7. Na liście **Konfiguracja rozwiązania aktywnego** wybierz pozycję **Zwolnij**.

8. W kolumnie **Konfiguracja** Sprawdź, czy wiersz **SimpleMath** jest ustawiony na wartość **Zwolnij**, a następnie wybierz przycisk **Zamknij** , aby zaakceptować zmianę.

   > [!IMPORTANT]
   > Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacją wydania lub aplikacje korzystające ze składnika nie przekazują certyfikacji dla [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła projektu **SimpleMath** , a następnie wybierz polecenie **Kompiluj**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia SimpleMathVSIX

1. W menu skrótów węzła **"SimpleMath" rozwiązania** wybierz pozycję **Dodaj**  >  **Nowy projekt**.

2. Na liście szablonów rozwiń pozycję **Visual C#** lub **Visual Basic**, wybierz węzeł **rozszerzalności** , a następnie wybierz szablon **projektu VSIX** .

3. W polu **Nazwa** Określ **SimpleMathVSIX**, a następnie wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań** wybierz element **source. Extension. vsixmanifest** .

5. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

6. Zastąp istniejący kod XML następującym kodem XML:

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. W **Eksplorator rozwiązań** wybierz projekt **SimpleMathVSIX** .

8. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

9. Na liście **elementów wspólnych** rozwiń pozycję **dane**, a następnie wybierz pozycję **plik XML**.

10. W polu **Nazwa** Określ `SDKManifest.xml` , a następnie wybierz przycisk **Dodaj** .

11. W **Eksplorator rozwiązań** Otwórz menu skrótów dla `SDKManifest.xml` , wybierz **Właściwości**, a następnie zmień wartość właściwości **Dołącz w VSIX** na **true**.

12. Zastąp zawartość pliku następującym kodem XML:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **SimpleMathVSIX** , wybierz **Dodaj**, a następnie wybierz **Nowy folder**.

14. Zmień nazwę folderu na `references` .

15. Otwórz menu skrótów dla folderu **References** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy folder**.

16. Zmień nazwę podfolderu na `commonconfiguration` , utwórz podfolder w nim i nazwij podfolder `neutral` .

17. Powtórz poprzednie cztery kroki, tym razem zmieniając nazwę pierwszego folderu na `redist` .

     Projekt zawiera teraz następującą strukturę folderów:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **SimpleMath** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

19. W **Eksploratorze plików** przejdź do folderu *bin\Release* , otwórz menu skrótów dla pliku **SimpleMath. winmd** , a następnie wybierz polecenie **Kopiuj**.

20. W **Eksplorator rozwiązań** wklej plik do folderu *References\commonconfiguration\neutral* w projekcie **SimpleMathVSIX** .

21. Powtórz poprzedni krok, wklejając plik **SimpleMath. pri** do folderu *Redist\commonconfiguration\neutral* w projekcie **SimpleMathVSIX** .

22. W **Eksplorator rozwiązań** wybierz **SimpleMath. winmd**.

23. Na pasku menu wybierz polecenie **Wyświetl**  >  **Właściwości** (klawiatura: wybierz klawisz **F4** ).

24. W oknie **Właściwości** Zmień właściwość **Akcja kompilacji** na **zawartość**, a następnie zmień wartość właściwości **Dołącz w VSIX** na **true**.

25. W **Eksplorator rozwiązań** Powtórz ten proces dla **SimpleMath. pri**.

26. W **Eksplorator rozwiązań** wybierz projekt **SimpleMathVSIX** .

27. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **kompilacje SimpleMathVSIX**.

28. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **SimpleMathVSIX** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

29. W **Eksploratorze plików** przejdź do folderu *\bin\Release* , a następnie uruchom plik *SimpleMathVSIX. vsix* , aby go zainstalować.

30. Wybierz przycisk **Zainstaluj** , poczekaj na zakończenie instalacji, a następnie ponownie uruchom program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście szablonów rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **Sklep Windows** .

3. Wybierz szablon **pustej aplikacji** , nazwij projekt **ArithmeticUI**, a następnie wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **ArithmeticUI** , a następnie wybierz **Dodaj**  >  **odwołanie**.

5. Na liście typów odwołań rozwiń węzeł **Windows**, a następnie wybierz pozycję **rozszerzenia**.

6. W okienku szczegółów wybierz rozszerzenie **biblioteki matematycznej WinRT** .

    Pojawią się dodatkowe informacje o zestawie SDK. Możesz wybrać link **więcej informacji** do otwarcia https://msdn.microsoft.com/ , jak określono w pliku SDKManifest.xml wcześniej w tym instruktażu.

7. W oknie dialogowym **Menedżer odwołań** zaznacz pole wyboru **Biblioteka wyrażeń matematycznych WinRT** , a następnie wybierz przycisk **OK** .

8. Na pasku menu wybierz polecenie **Wyświetl**  >  **Przeglądarka obiektów**.

9. Na liście **Przeglądaj** wybierz pozycję **proste matematyczne**.

     Teraz możesz dowiedzieć się, co znajduje się w zestawie SDK.

10. W **Eksplorator rozwiązań** Otwórz **MainPage. XAML** i Zastąp jego zawartość następującym XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Zaktualizuj **MainPage. XAML. cs** , aby pasował do następującego kodu:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. Wybierz klawisz **F5** , aby uruchomić aplikację.

13. W aplikacji wprowadź dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.

     Zostanie wyświetlony prawidłowy wynik.

    Pomyślnie utworzono i zastosowano zestaw SDK rozszerzenia.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
