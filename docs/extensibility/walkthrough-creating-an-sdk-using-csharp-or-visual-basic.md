---
title: 'Przewodnik: Tworzenie sdk przy użyciu języka C# lub Visual Basic | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697555"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Instruktaż: Tworzenie sdk przy użyciu języka C# lub Visual Basic
W tym instruktażu dowiesz się, jak utworzyć prosty pakiet SDK biblioteki matematycznej przy użyciu języka Visual C#, a następnie spakować zestawu SDK jako rozszerzenie programu Visual Studio (VSIX). Wykonasz następujące procedury:

- [Aby utworzyć składnik SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Aby utworzyć przykładową aplikację, która korzysta z biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Aby utworzyć składnik SimpleMath Windows Runtime

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście szablonów rozwiń węzeł **Visual C#** lub **Visual Basic**wybierz węzeł **Sklepu Windows,** a następnie wybierz szablon **składnika środowiska wykonawczego systemu Windows.**

3. W polu **Nazwa** określ **simplemath**, a następnie wybierz przycisk **OK.**

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla węzła projektu **SimpleMath,** a następnie wybierz polecenie **Właściwości**.

5. Zmień nazwę **Class1.cs,** aby **Arithmetic.cs** i zaktualizować go, aby dopasować go do następującego kodu:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **węzła Rozwiązanie "SimpleMath",** a następnie wybierz pozycję **Menedżer konfiguracji**.

    Zostanie otwarte okno dialogowe **Menedżer konfiguracji.**

7. Na liście **Konfiguracja aktywnego rozwiązania** wybierz pozycję **Zwolnij**.

8. W kolumnie **Konfiguracja** sprawdź, czy wiersz **SimpleMath** jest ustawiony na **Zwolnij**, a następnie wybierz przycisk **Zamknij,** aby zaakceptować zmianę.

   > [!IMPORTANT]
   > Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacją wydania lub aplikacje korzystające [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]z tego składnika nie przejdą certyfikacji dla pliku .

9. W **Eksploratorze rozwiązań**otwórz menu skrótów dla węzła projektu **SimpleMath,** a następnie wybierz polecenie **Buduj**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Aby utworzyć projekt rozszerzenia SimpleMathVSIX

1. W menu skrótów węzła **"SimpleMath" wybierz** pozycję **Dodaj** > **nowy projekt**.

2. Na liście szablonów rozwiń węzeł **Visual C#** lub **Visual Basic**wybierz węzeł **Rozszerzalność,** a następnie wybierz szablon **projektu VSIX.**

3. W polu **Nazwa** określ **simplemathvsix**, a następnie wybierz przycisk **OK.**

4. W **Eksploratorze rozwiązań**wybierz element **source.extension.vsixmanifest.**

5. Na pasku menu wybierz pozycję **Wyświetl** > **kod**.

6. Zastąp istniejący kod XML następującym kodem XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. W **Eksploratorze rozwiązań**wybierz projekt **SimpleMathVSIX.**

8. Na pasku menu wybierz pozycję **Project** > **Add New Item**.

9. Na liście **elementów wspólnych**rozwiń węzeł **Dane**, a następnie wybierz pozycję **Plik XML**.

10. W polu **Nazwa** `SDKManifest.xml`określ , a następnie wybierz przycisk **Dodaj.**

11. W **Eksploratorze rozwiązań**otwórz menu **skrótów**dla `SDKManifest.xml`, wybierz polecenie Właściwości , a następnie zmień wartość właściwości **Uwzględnij w VSIX** na **True**.

12. Zastąp zawartość pliku następującym plikiem XML:

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

13. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **SimpleMathVSIX,** wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Nowy folder**.

14. Zmień nazwę folderu na `references`.

15. Otwórz menu **skrótów** do folderu Odwołania, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Nowy folder**.

16. Zmień nazwę podfolderu na `commonconfiguration`, utwórz podfolder w `neutral`nim i nazwij podfolder .

17. Powtórz poprzednie cztery kroki, tym razem zmieniając `redist`nazwę pierwszego folderu na .

     Projekt zawiera teraz następującą strukturę folderów:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **SimpleMath,** a następnie wybierz pozycję **Otwórz folder w Eksploratorze plików**.

19. W **Eksploratorze plików**przejdź do folderu *bin\Release,* otwórz menu skrótów dla pliku **SimpleMath.winmd,** a następnie wybierz polecenie **Kopiuj**.

20. W **Eksploratorze rozwiązań**wklej plik do folderu *references\commonconfiguration\neutral* w projekcie **SimpleMathVSIX.**

21. Powtórz poprzedni krok, wklejając plik **SimpleMath.pri** do folderu *redist\commonconfiguration\neutral* w projekcie **SimpleMathVSIX.**

22. W **Eksploratorze rozwiązań**wybierz **simplemath.winmd**.

23. Na pasku menu wybierz pozycję **Wyświetl** > **właściwości** (klawiatura: Wybierz klawisz **F4).**

24. W oknie Właściwości zmień właściwość **Akcja kompilacji** na **Zawartość,** a następnie zmień właściwość **Properties** **Uwzględnij w vsix** na **True**.

25. W **Eksploratorze rozwiązań**powtórz ten proces dla **SimpleMath.pri**.

26. W **Eksploratorze rozwiązań**wybierz projekt **SimpleMathVSIX.**

27. Na pasku menu wybierz polecenie **Build** > **Build SimpleMathVSIX**.

28. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **SimpleMathVSIX,** a następnie wybierz pozycję **Otwórz folder w Eksploratorze plików**.

29. W **Eksploratorze plików**przejdź do *folderu \bin\Release,* a następnie uruchom *plik SimpleMathVSIX.vsix,* aby go zainstalować.

30. Wybierz przycisk **Zainstaluj,** poczekaj na zakończenie instalacji, a następnie uruchom ponownie program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Aby utworzyć przykładową aplikację, która korzysta z biblioteki klas

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście szablonów rozwiń węzeł **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **Sklepu Windows.**

3. Wybierz szablon **Pusta aplikacja,** nazwij projekt **ArithmeticUI,** a następnie wybierz przycisk **OK.**

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **ArithmeticUI,** a następnie wybierz pozycję **Dodaj** > **odwołanie**.

5. Na liście typów odwołań rozwiń węzeł **Windows**, a następnie wybierz pozycję **Rozszerzenia**.

6. W okienku szczegółów wybierz rozszerzenie **Biblioteka matematyczna WinRT.**

    Zostaną wyświetlona dodatkowe informacje o sdk. Łącze **Więcej informacji** do https://msdn.microsoft.com/otwarcia można wybrać, jak określono w pliku SDKManifest.xml wcześniej w tym instruktażu.

7. W oknie dialogowym **Menedżer odwołań** zaznacz pole wyboru **Biblioteka matematyczna WinRT,** a następnie wybierz przycisk **OK.**

8. Na pasku menu wybierz pozycję **Wyświetl** > **przeglądarkę obiektów**.

9. Na liście **Przeglądaj** wybierz pozycję **Prosta matematyka**.

     Teraz możesz zbadać, co znajduje się w sdk.

10. W **Eksploratorze rozwiązań**otwórz stronę **MainPage.xaml**i zastąp jego zawartość następującym kodem XAML:

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

11. Zaktualizuj **MainPage.xaml.cs,** aby dopasować go do następującego kodu:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Wybierz klawisz **F5,** aby uruchomić aplikację.

13. W aplikacji wprowadź dowolne dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.

     Pojawi się poprawny wynik.

    Pomyślnie utworzono i użyto SDK rozszerzenia.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: Tworzenie sdk przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Instruktaż: tworzenie sdk przy użyciu języka JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
