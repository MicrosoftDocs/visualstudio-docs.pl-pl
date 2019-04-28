---
title: Dodawanie kontrolki użytkownika do strony początkowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5a5e8d752122432e27d7b6845f6d144856746387
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891818"
---
# <a name="add-user-control-to-the-start-page"></a>Dodaj kontrolkę użytkownika do strony początkowej

W tym instruktażu przedstawiono sposób dodawania odwołania biblioteki DLL do niestandardowej strony początkowej. Przykład dodaje formant użytkownika do rozwiązania, tworzy kontrolkę użytkownika i następnie odwołuje się skompilowany zestaw z poziomu strony startowej *.xaml* pliku. Nowa karta obsługuje formant użytkownika, który działa jako podstawowa przeglądarka sieci Web.

Można użyć tego samego procesu można dodać zestawu, który może zostać wywołana z *.xaml* pliku.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Dodaj kontrolkę użytkownika WPF do rozwiązania

Najpierw dodaj formant użytkownika Windows Presentation Foundation (WPF) z rozwiązaniem strony początkowej.

1. Tworzenie strony początkowej, przy użyciu utworzonego w [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.

3. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** węzeł, a następnie kliknij przycisk **Windows**. W środkowym okienku wybierz **Biblioteka kontrolek użytkownika WPF**.

4. Nazwij kontrolkę `WebUserControl` a następnie kliknij przycisk **OK**.

## <a name="implement-the-user-control"></a>Implementowanie formantu użytkownika

Do zaimplementowania formanty użytkownika WPF, tworzenia interfejsu użytkownika (UI) w XAML, a następnie wpisz zdarzenia związanego z kodem w języku C# lub innym języku .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Do pisania XAML, kontrolki użytkownika

1. Otwórz plik XAML, kontrolki użytkownika. W `<Grid>` elementu, Dodaj następujące definicje wiersza do formantu.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. W oknie głównym `<Grid>` elementu, Dodaj następujące nowe `<Grid>` element, który zawiera pole tekstowe służące do wpisywania adresy sieci Web i przycisk służący do ustawiania nowego adresu.

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

3. Dodaj następujące ramki do najwyższego poziomu `<Grid>` elementu tuż za `<Grid>` element, który zawiera przycisk i pole tekstowe.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Poniższy przykład pokazuje ukończone XAML, kontrolki użytkownika.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Aby zapisać zdarzenia związanego z kodem dla formantu użytkownika

1. W Projektancie XAML, kliknij dwukrotnie **Ustaw adres** dodanie do formantu przycisku.

    *UserControl1.cs* plik zostanie otwarty w edytorze kodu.

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

    Ten kod ustawia adres sieci Web wprowadzonego w polu tekstowym jako cel przeglądarki sieci Web. Jeśli adres nie jest prawidłowy, kod zgłasza błąd.

3. Muszą również obsługiwać zdarzenia WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Skompiluj rozwiązanie.

## <a name="add-the-user-control-to-the-start-page"></a>Dodaj kontrolkę użytkownika do strony początkowej

Aby udostępnić ten formant do projektu strony początkowej w pliku projektu strony początkowej, należy dodać odwołanie do Nowa biblioteka kontrolki. Następnie można dodać kontrolki do znaczników Start strony XAML.

1. W **Eksploratora rozwiązań**, w projekcie strony początkowej, kliknij prawym przyciskiem myszy **odwołania** a następnie kliknij przycisk **Dodaj odwołanie**.

2. Na **projektów** zaznacz **WebUserControl** a następnie kliknij przycisk **OK**.

3. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

    Skompilować rozwiązanie udostępnia kontrolkę użytkownika do funkcji IntelliSense dla innych plików w rozwiązaniu.

    Aby dodać formant do znaczników Start strony XAML, Dodaj odwołanie do zestawu przestrzeni nazw, a następnie umieszczanie kontrolki na stronie.

### <a name="to-add-the-control-to-the-markup"></a>Aby dodać kontrolkę znaczników

1. W **Eksploratora rozwiązań**, otwórz stronę początkową *.xaml* pliku.

2. W **XAML** okienko, dodaj następującą deklarację przestrzeni nazw do najwyższego poziomu <xref:System.Windows.Controls.Grid> elementu.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. W **XAML** okienko, przewiń do \<siatki > sekcji.

    Sekcja zawiera <xref:System.Windows.Controls.TabControl> element <xref:System.Windows.Controls.Grid> elementu.

4. Dodaj \<TabControl > zawierający element \<TabItem > zawiera odwołanie do kontrolki użytkownika.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Teraz można przetestować formant.

## <a name="test-a-manually-created-custom-start-page"></a>Testowanie ręczne tworzenie niestandardowej strony początkowej

1. Skopiuj plik XAML i pomocnicze pliki tekstowe lub znaczników pliki do *%USERPROFILE%\My 2015\StartPages Documents\Visual Studio\\*  folderu.

2. Jeśli swoją stronę początkową odwołuje się do żadnych formantów lub typów w zestawach, które nie są instalowane przez program Visual Studio, skopiować te zestawy, a następnie wklej je w _folder instalacji programu Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.

3. Wpisz w wierszu polecenia programu Visual Studio **devenv /rootsuffix Exp** otworzyć doświadczalne wystąpienie programu Visual Studio.

4. W doświadczalnym wystąpieniu, przejdź do **narzędzia** > **opcje** > **środowiska** > **uruchamiania** strony i wybierz plik XAML z **Dostosuj stronę początkową** listy rozwijanej.

5. Na **widoku** menu, kliknij przycisk **strona startowa**.

    Powinien być wyświetlany z niestandardową stronę początkową. Jeśli chcesz zmienić wszystkie pliki, możesz musi Zamknij wystąpienie doświadczalne, wprowadzić zmiany, skopiuj Wklej zmienionych plików i następnie ponownie otwórz wystąpienie doświadczalne, aby wyświetlić zmiany.

## <a name="see-also"></a>Zobacz także

- [Kontrole kontenerów WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Przewodnik: Dodaj niestandardowe XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
