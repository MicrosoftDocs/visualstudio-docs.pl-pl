---
title: Dodawanie kontrolki użytkownika do strony startowej | Microsoft Docs
description: Dowiedz się, jak dodać kontrolkę użytkownika Windows Presentation Foundation (WPF) do strony Start w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 735e77868b85bdd8f85fb27957602d6759b5b097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879179"
---
# <a name="add-user-control-to-the-start-page"></a>Dodawanie kontrolki użytkownika do strony początkowej

W tym instruktażu pokazano, jak dodać odwołanie do biblioteki DLL do niestandardowej strony początkowej. Przykład dodaje kontrolkę użytkownika do rozwiązania, kompiluje kontrolkę użytkownika, a następnie odwołuje się do skompilowanego zestawu z pliku Start Page *. XAML* . Nowa karta obsługuje kontrolkę użytkownika, która działa jako podstawowa przeglądarka sieci Web.

Można użyć tego samego procesu, aby dodać każdy zestaw, który może być wywoływany z pliku *. XAML* .

## <a name="add-a-wpf-user-control-to-the-solution"></a>Dodawanie kontrolki użytkownika WPF do rozwiązania

Najpierw Dodaj kontrolkę użytkownika Windows Presentation Foundation (WPF) do rozwiązania strony początkowej.

1. Utwórz stronę początkową przy użyciu utworzonej w obszarze [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

3. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** , a następnie kliknij pozycję **Windows**. W środkowym okienku wybierz pozycję **Biblioteka formantów użytkownika WPF**.

4. Nadaj formantowi nazwę `WebUserControl` , a następnie kliknij przycisk **OK**.

## <a name="implement-the-user-control"></a>Implementowanie kontrolki użytkownika

Aby zaimplementować kontrolkę użytkownika WPF, skompiluj interfejs użytkownika w języku XAML, a następnie napisz zdarzenia związane z kodem w języku C# lub innym języku .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Aby napisać kod XAML dla kontrolki użytkownika

1. Otwórz plik XAML dla kontrolki użytkownika. W `<Grid>` elemencie Dodaj następujące definicje wierszy do kontrolki.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. W elemencie głównym `<Grid>` Dodaj następujący nowy `<Grid>` element, który zawiera pole tekstowe służące do wpisywania adresów sieci Web i przycisk służący do ustawiania nowego adresu.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Dodaj następującą ramkę do elementu najwyższego poziomu `<Grid>` tuż po `<Grid>` elemencie zawierającym przycisk i pole tekstowe.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Poniższy przykład pokazuje ukończony kod XAML dla kontrolki użytkownika.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Aby napisać zdarzenia związane z kodem dla kontrolki użytkownika

1. W projektancie XAML kliknij dwukrotnie przycisk **Ustaw adres** , który został dodany do kontrolki.

    Plik *UserControl1.cs* zostanie otwarty w edytorze kodu.

2. Wypełnij SetButton_Click obsługi zdarzeń w następujący sposób.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Ten kod ustawia adres sieci Web, który jest wpisywany w polu tekstowym jako element docelowy przeglądarki sieci Web. Jeśli adres jest nieprawidłowy, kod zgłosi błąd.

3. Musisz również obsłużyć WebFrame_Navigated zdarzenie:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Skompiluj rozwiązanie.

## <a name="add-the-user-control-to-the-start-page"></a>Dodawanie kontrolki użytkownika do strony początkowej

Aby udostępnić tę kontrolkę projektowi strony początkowej, w pliku projektu strony początkowej Dodaj odwołanie do nowej biblioteki formantów. Następnie można dodać formant do znacznika XAML strony początkowej.

1. W **Eksplorator rozwiązań** w projekcie strony początkowej kliknij prawym przyciskiem myszy pozycję **odwołania** , a następnie kliknij pozycję **Dodaj odwołanie**.

2. Na karcie **projekty** wybierz pozycję **WebUserControl** , a następnie kliknij przycisk **OK**.

3. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

    Kompilowanie rozwiązania sprawia, że formant użytkownika jest dostępny dla funkcji IntelliSense dla innych plików w rozwiązaniu.

    Aby dodać formant do znacznika XAML strony początkowej, Dodaj odwołanie do przestrzeni nazw do zestawu, a następnie umieść formant na stronie.

### <a name="to-add-the-control-to-the-markup"></a>Aby dodać kontrolkę do znacznika

1. W **Eksplorator rozwiązań** Otwórz plik Start Page *. XAML* .

2. W okienku **XAML** Dodaj następującą deklarację przestrzeni nazw do elementu najwyższego poziomu <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. W okienku **XAML** przewiń do \<Grid> sekcji.

    Sekcja zawiera <xref:System.Windows.Controls.TabControl> element w <xref:System.Windows.Controls.Grid> elemencie.

4. Dodaj \<TabControl> element zawierający \<TabItem> odwołanie do kontrolki użytkownika.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Teraz można testować formant.

## <a name="test-a-manually-created-custom-start-page"></a>Przetestuj ręcznie utworzoną niestandardową stronę początkową

1. Skopiuj plik XAML i wszystkie pomocnicze pliki tekstowe lub pliki znaczników do folderu *%USERPROFILE%\My Documents\Visual Studio 2015 \ startpages \\* .

2. Jeśli strona początkowa odwołuje się do dowolnych kontrolek lub typów w zestawach, które nie są zainstalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w _folderze instalacyjnym programu Visual Studio_**\Common7\IDE\PrivateAssemblies \\**.

3. W wierszu polecenia programu Visual Studio wpisz **devenv/rootsuffix Exp** , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

4. W eksperymentalnym wystąpieniu przejdź do   >    >    >  strony **startowej** Opcje narzędzia, a następnie wybierz plik XAML na liście rozwijanej **Dostosuj stronę początkową** .

5. W menu **Widok** kliknij pozycję **Strona początkowa**.

    Powinna zostać wyświetlona niestandardowa strona startowa. Jeśli chcesz zmienić dowolne pliki, musisz zamknąć wystąpienie eksperymentalne, wprowadzić zmiany, skopiować i wkleić zmienione pliki, a następnie ponownie otworzyć doświadczalne wystąpienie, aby wyświetlić zmiany.

## <a name="see-also"></a>Zobacz też

- [Formanty kontenera WPF](/previous-versions/bb675291(v=vs.110))
- [Przewodnik: Dodawanie niestandardowego kodu XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)