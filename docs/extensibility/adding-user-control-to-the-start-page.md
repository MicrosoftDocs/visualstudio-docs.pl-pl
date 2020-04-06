---
title: Dodawanie kontrolki użytkownika do strony początkowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740128"
---
# <a name="add-user-control-to-the-start-page"></a>Dodawanie kontrolki użytkownika do strony początkowej

W tym przewodniku pokazano, jak dodać odwołanie dll do niestandardowej strony początkowej. W przykładzie dodaje formant użytkownika do rozwiązania, tworzy formant użytkownika, a następnie odwołuje się do zestawu wbudowanego z pliku *xaml strony początkowej.* Nowa karta obsługuje kontrolkę użytkownika, która działa jako podstawowa przeglądarka sieci Web.

Tego samego procesu można użyć, aby dodać dowolny zestaw, który może być wywoływany z pliku *xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Dodawanie formantu użytkownika WPF do rozwiązania

Najpierw dodaj kontrolkę użytkownika programu Windows Presentation Foundation (WPF) do rozwiązania Strony początkowej.

1. Utwórz stronę początkową za pomocą utworzonej w [polu Utwórz niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md).

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Nowy projekt**.

3. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** i kliknij pozycję **Windows**. W środkowym okienku wybierz pozycję **Biblioteka sterowania użytkownikami WPF**.

4. Nadaj `WebUserControl` formancie nazwę, a następnie kliknij przycisk **OK**.

## <a name="implement-the-user-control"></a>Implementowanie formantu użytkownika

Aby zaimplementować formant użytkownika WPF, skompiluj interfejs użytkownika (UI) w języku XAML, a następnie zapisz zdarzenia związane z kodem w języku C# lub innym języku .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Aby zapisać kod XAML dla formantu użytkownika

1. Otwórz plik XAML dla formantu użytkownika. W `<Grid>` elemencie dodaj następujące definicje wierszy do formantu.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. W elemencie głównym `<Grid>` `<Grid>` dodaj następujący nowy element, który zawiera pole tekstowe służące do wpisywania adresów sieci Web i przycisk do ustawiania nowego adresu.

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

3. Dodaj następującą ramkę do `<Grid>` elementu najwyższego poziomu tuż po elemencie `<Grid>` zawierającym przycisk i pole tekstowe.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. W poniższym przykładzie przedstawiono ukończony kod XAML dla formantu użytkownika.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Aby napisać zdarzenia związane z kodem dla formantu użytkownika

1. W projektancie XAML kliknij dwukrotnie przycisk **Ustaw adres** dodany do formantu.

    Plik *UserControl1.cs* zostanie otwarty w edytorze kodu.

2. Wypełnij SetButton_Click obsługi zdarzeń w następujący sposób.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    Ten kod ustawia adres sieci Web wpisany w polu tekstowym jako miejsce docelowe przeglądarki sieci Web. Jeśli adres jest nieprawidłowy, kod zgłasza błąd.

3. Należy również obsługiwać zdarzenie WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Skompiluj rozwiązanie.

## <a name="add-the-user-control-to-the-start-page"></a>Dodawanie formantu użytkownika do strony początkowej

Aby udostępnić ten formant projektowi Strona początkowa, w pliku projektu Strona początkowa dodaj odwołanie do nowej biblioteki formantów. Następnie można dodać formant do znaczników XAML strony początkowej.

1. W **Eksploratorze rozwiązań**w projekcie Strona początkowa kliknij prawym przyciskiem myszy **pozycję Odwołania,** a następnie kliknij polecenie **Dodaj odwołanie**.

2. Na karcie **Projekty** wybierz pozycję **WebUserControl,** a następnie kliknij przycisk **OK**.

3. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

    Tworzenie rozwiązania udostępnia formant użytkownika intellisense dla innych plików w rozwiązaniu.

    Aby dodać formant do znaczników XAML strony początkowej, dodaj odwołanie do obszaru nazw do zestawu, a następnie umieść formant na stronie.

### <a name="to-add-the-control-to-the-markup"></a>Aby dodać formant do znaczników

1. W **Eksploratorze rozwiązań**otwórz plik *xaml* strony początkowej.

2. W okienku **XAML** dodaj następującą deklarację obszaru <xref:System.Windows.Controls.Grid> nazw do elementu najwyższego poziomu.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. W okienku **XAML** przewiń do sekcji \<> siatki.

    Sekcja zawiera <xref:System.Windows.Controls.TabControl> element w <xref:System.Windows.Controls.Grid> elemencie.

4. Dodaj \<Element> TabControl zawierający \<> TabItem, który zawiera odwołanie do formantu użytkownika.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Teraz możesz przetestować formant.

## <a name="test-a-manually-created-custom-start-page"></a>Testowanie ręcznie utworzonej niestandardowej strony startowej

1. Skopiuj plik XAML i wszystkie pomocnicze pliki tekstowe lub pliki znaczników do folderu *%USERPROFILE%\Moje dokumenty\Visual Studio 2015\StartPages.\\ *

2. Jeśli strona początkowa odwołuje się do wszystkich formantów lub typów w zestawach, które nie są zainstalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w _folderze instalacyjnym programu Visual Studio_**\Common7\IDE\PrivateAssemblies\\**.

3. W wierszu polecenia programu Visual Studio wpisz **devenv /rootsuffix Exp,** aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

4. W przypadku wystąpienia eksperymentalnego przejdź do strony**Uruchamianie** **środowiska** > **opcje** >  **narzędzi** > i wybierz plik XAML z listy rozwijanej **Dostosowywanie strony początkowej.**

5. W menu **Widok** kliknij polecenie **Strona początkowa**.

    Powinna zostać wyświetlona niestandardowa strona początkowa. Jeśli chcesz zmienić wszystkie pliki, musisz zamknąć wystąpienie eksperymentalne, wprowadzić zmiany, skopiować i wkleić zmienione pliki, a następnie ponownie otworzyć wystąpienie eksperymentalne, aby wyświetlić zmiany.

## <a name="see-also"></a>Zobacz też

- [Kontrolki kontenera WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Instruktaż: Dodawanie niestandardowego kodu XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
