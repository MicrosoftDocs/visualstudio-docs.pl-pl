---
title: 'Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 6bb9ae53dfb2e849c35c05fe5187cddcf301622c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312644"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic
W tym przewodniku dowiesz się, jak utworzyć prosty zestaw SDK biblioteki matematyczne przy użyciu języka Visual C# i następnie pakietu SDK jako programu Visual Studio rozszerzenia (VSIX). Wykonasz następujące procedury:

- [Aby utworzyć składnika środowiska wykonawczego Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="createClassLibrary"></a> Aby utworzyć składnika środowiska wykonawczego Windows SimpleMath

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, wybierz **Windows Store** węzła, a następnie wybierz **składnika środowiska wykonawczego Windows** szablonu.

3. W **nazwa** określ **SimpleMath**, a następnie wybierz **OK** przycisku.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** węzła projektu, a następnie wybierz **właściwości**.

5. Zmień nazwę **Class1.cs** do **Arithmetic.cs** i zaktualizować je, aby dopasować następujący kod:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "SimpleMath"** węzła, a następnie wybierz **programu Configuration Manager**.

    **Programu Configuration Manager** zostanie otwarte okno dialogowe.

7. W **Konfiguracja rozwiązania aktywnego** wybierz **wersji**.

8. W **konfiguracji** kolumny, upewnij się, że **SimpleMath** wiersza jest ustawiona na **wersji**, a następnie wybierz **Zamknij** przycisk, aby zaakceptować Zmiana.

   > [!IMPORTANT]
   > Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacji wydania lub aplikacje, które używają składnika nie przekaże certyfikacji [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].

9. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** węzła projektu, a następnie wybierz **kompilacji**.

## <a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia SimpleMathVSIX

1. W menu skrótów dla **rozwiązania "SimpleMath"** węzła, wybierz **Dodaj** > **nowy projekt**.

2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, wybierz **rozszerzalności** węzła, a następnie wybierz **projekt VSIX** szablon.

3. W **nazwa** określ **SimpleMathVSIX**, a następnie wybierz **OK** przycisku.

4. W **Eksploratora rozwiązań**, wybierz **source.extension.vsixmanifest** elementu.

5. Na pasku menu wybierz **widoku** > **kodu**.

6. Zastąp istniejący kod XML następujący kod XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.

8. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

9. Na liście **wspólne elementy**, rozwiń węzeł **danych**, a następnie wybierz **pliku XML**.

10. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz **Dodaj** przycisku.

11. W **Eksploratora rozwiązań**, otwórz menu skrótów dla `SDKManifest.xml`, wybierz **właściwości**, a następnie zmień wartość **Include w VSIX** właściwość **True**.

12. Zastąp zawartość pliku następujący kod XML:

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

13. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMathVSIX** projektu, wybierz **Dodaj**, a następnie wybierz **nowy Folder**.

14. Zmień nazwę folderu do `references`.

15. Otwórz menu skrótów dla **odwołania** folderu, wybierz **Dodaj**, a następnie wybierz **nowy Folder**.

16. Zmień nazwę podfolderu, aby `commonconfiguration`, utwórz podfolder w niej i nazwa podfolderu `neutral`.

17. Powtórz poprzednie cztery kroki tej chwili, zmiana nazwy pierwszego folderu do `redist`.

     Projekt obecnie zawiera następującą strukturę folderów:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.

19. W **Eksploratora plików**, przejdź do *bin\Release* folder, otwórz menu skrótów dla **SimpleMath.winmd** , a następnie wybierz **Skopiuj**.

20. W **Eksploratora rozwiązań**, wklej go do *references\commonconfiguration\neutral* folderu w **SimpleMathVSIX** projektu.

21. Powtórz poprzedni krok, wklejając **SimpleMath.pri** mezzanine do *redist\commonconfiguration\neutral* folderu w **SimpleMathVSIX** projektu.

22. W **Eksploratora rozwiązań**, wybierz **SimpleMath.winmd**.

23. Na pasku menu wybierz **widoku** > **właściwości** (klawiatury: Wybierz **F4** klucza).

24. W **właściwości** oknie zmiany **Build Action** właściwości **zawartości**, a następnie zmień **Include w VSIX** właściwości  **Wartość true,** .

25. W **Eksploratora rozwiązań**, powtórz ten proces dla **SimpleMath.pri**.

26. W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.

27. Na pasku menu wybierz **kompilacji** > **kompilacji SimpleMathVSIX**.

28. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMathVSIX** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.

29. W **Eksploratora plików**, przejdź do *\bin\Release* folder, a następnie uruchom *SimpleMathVSIX.vsix* go zainstalować.

30. Wybierz **zainstalować** przycisk, poczekaj na zakończenie instalacji i ponownie uruchom program Visual Studio.

## <a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz **Windows Store** węzła.

3. Wybierz **pusta aplikacja** szablonu, nazwę projektu **ArithmeticUI**, a następnie wybierz **OK** przycisku.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ArithmeticUI** projektu, a następnie wybierz **Dodaj** > **odwołania**.

5. Na liście typów referencyjnych rozwiń **Windows**, a następnie wybierz **rozszerzenia**.

6. W okienku szczegółów wybierz **biblioteka funkcji matematycznych WinRT** rozszerzenia.

    Pojawi się dodatkowe informacje na temat zestawu SDK. Możesz wybrać **więcej informacji o** link umożliwiający otworzenie https://msdn.microsoft.com/, jak określono w pliku SDKManifest.xml we wcześniejszej części tego przewodnika.

7. W **Menadżer odwołań** okno dialogowe, wybierz opcję **biblioteka funkcji matematycznych WinRT** pole wyboru, a następnie wybierz **OK** przycisku.

8. Na pasku menu wybierz **widoku** > **przeglądarki obiektów**.

9. W **Przeglądaj** wybierz **proste matematyczne**.

     Można teraz zbadać, co nowego w zestawie SDK.

10. W **Eksploratora rozwiązań**, otwórz **MainPage.xaml**i zastąp jego zawartość następujących XAML:

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

11. Aktualizacja **MainPage.xaml.cs** aby dopasować następujący kod:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Wybierz **F5** klawisz, aby uruchomić aplikację.

13. W aplikacji, wprowadź dowolne dwie liczby, wybierz operację, a następnie wybierz **=** przycisku.

     Zostanie wyświetlony odpowiedni wynik.

    Pomyślnie tworzone i używane rozszerzenie SDK.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md)
