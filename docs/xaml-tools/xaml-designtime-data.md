---
title: Używanie danych czasu projektowania z projektant XAML w Visual Studio
description: Dowiedz się, jak używać danych w czasie projektowania w języku XAML.
ms.date: 11/17/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 915fe38da63f0b3994a809b20515fdc18e0790ce
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2021
ms.locfileid: "107913075"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Używanie danych czasu projektowania z projektant XAML w Visual Studio

Niektóre układy trudno wizualizować bez danych. W tym dokumencie będziemy przeglądać jedno z podejść, które deweloperzy pracujący nad projektami pulpitu mogą wykorzystać do pozorowania danych w projektancie XAML. To podejście jest wykonywane przy użyciu istniejącej zignorowalnej przestrzeni nazw "d:". Dzięki temu podejściu można szybko dodawać dane w czasie projektowania do stron lub kontrolek bez konieczności tworzenia pełnego modelu ViewModel lub po prostu przetestowania, jak zmiana właściwości może wpłynąć na aplikację, bez obaw, że te zmiany wpłyną na kompilacje wydania. Wszystkie d: dane są używane tylko przez projektant XAML i nie można zignorować wartości przestrzeni nazw są kompilowane do aplikacji.

> [!NOTE]
> Jeśli używasz platformy Xamarin.Forms, zobacz Xamarin.Forms Design Time Data (Dane czasu projektowania platformy [Xamarin.Forms)](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Podstawy danych czasu projektowania

Dane czasu projektowania to pozorowanie danych ustawionych w celu ułatwienia wizualizacji kontrolek w projektant XAML. Aby rozpocząć, dodaj następujące wiersze kodu do nagłówka dokumentu XAML, jeśli jeszcze nie są obecne:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Po dodaniu przestrzeni nazw można umieścić przed dowolnym atrybutem lub kontrolką, aby pokazać ją tylko w projektant XAML ale nie w `d:` czasie wykonywania.

Na przykład można dodać tekst do textblock, który zwykle ma powiązane dane.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Dane czasu projektowania z tekstem w tekście TextBlock](media\xaml-design-time-textblock.png "Dane czasu projektowania z tekstem etykiety")](media\xaml-design-time-textblock.png#lightbox)

W tym przykładzie bez `d:Text` projektant XAML nie będą wyświetlane żadne informacje dla textblock. Zamiast tego wyświetla on "Name!" gdzie TextBlock będzie zawierał rzeczywiste dane w czasie wykonywania.

Można używać z atrybutami dla dowolnej kontrolki platformy UWP lub WPF .NET Core, takich jak kolory, rozmiary `d:` czcionek i odstępy. Możesz nawet dodać go do samej kontrolki.

```xml
<d:Button Content="Design Time Button" />
```

[![Dane czasu projektowania za pomocą kontrolki Przycisk](media\xaml-design-time-button.png "Dane czasu projektowania z kontrolką Przycisk")](media\xaml-design-time-button.png#lightbox)

W tym przykładzie przycisk jest wyświetlany tylko w czasie projektowania. Użyj tej metody, aby umieścić symbol zastępczy w kontrolce niestandardowej lub wypróbować różne kontrolki. Wszystkie `d:` atrybuty i kontrolki zostaną zignorowane podczas wykonywania.

## <a name="preview-images-at-design-time"></a>Podgląd obrazów w czasie projektowania

Można ustawić źródło czasu projektowania dla obrazów, które są powiązane ze stroną lub ładowane dynamicznie. Dodaj obraz, który ma być pokazywany w projektant XAML do projektu. Następnie możesz wyświetlić ten obraz na projektant XAML w czasie projektowania:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Obraz w tym przykładzie musi istnieć w rozwiązaniu.

## <a name="design-time-data-for-listviews"></a>Dane czasu projektowania dla elementów ListView

ListViews to popularny sposób wyświetlania danych w aplikacji klasycznej. Jednak są one trudne do zwizualizowania bez żadnych danych. Za pomocą tej funkcji można tworzyć wbudowane dane czasu projektowania ItemSource lub Items. W projektant XAML zostaną wyświetlone informacje o tym, co znajduje się w tej tablicy w widoku ListView w czasie projektowania.

### <a name="wpf-net-core--example"></a>Przykład platformy WPF .NET Core
Aby użyć typu system:String, upewnij się, że w `xmlns:system="clr-namespace:System;assembly=mscorlib` nagłówku XAML znajduje się ciąg .

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Dane czasu projektowania za pomocą listView](media\xaml-design-time-listview-strings.png "Dane czasu projektowania za pomocą listView")](media\xaml-design-time-listview-strings.png#lightbox)

W poprzednim przykładzie pokazano widok ListView z trzema blokami TextBlock w projektant XAML.

Można również utworzyć tablicę obiektów danych. Na przykład właściwości publiczne obiektu danych mogą być konstruowane `City` jako dane w czasie projektowania.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Aby użyć klasy w języku XAML, należy zaimportować przestrzeń nazw w węźle głównym.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Rzeczywisty model w danych czasu projektowania z listView](media\xaml-design-time-listview-models.png "Rzeczywiste dane czasu projektowania modelu za pomocą listView")](media\xaml-design-time-listview-models.png#lightbox)

Zaletą tej metody jest możliwość powiązania kontrolek ze statyczną wersją modelu w czasie projektowania.

### <a name="uwp-example"></a>Przykład platformy uniwersalnej systemu Windows 

X:Array nie jest obsługiwana w UWP. W związku z tym możemy użyć `<d:ListView.Items>` zamiast tego. Aby użyć typu system:String, upewnij się, że w `http://schemas.microsoft.com/winfx/2009/xaml` nagłówku XAML znajduje się ciąg .

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Używanie danych czasu projektowania z niestandardowymi typami i właściwościami

Ta funkcja domyślnie działa tylko z kontrolkami i właściwościami platformy. W tej sekcji ominiemy kroki niezbędne do umożliwienia używania własnych kontrolek niestandardowych jako kontrolek czasu projektowania— nowej możliwości dostępnej dla klientów korzystających z programu Visual Studio 2019 w wersji [16.8](/visualstudio/releases/2019/release-notes/) lub nowszej. Aby to umożliwić, należy spełnić trzy wymagania:

- Niestandardowa przestrzeń nazw xmlns

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Wersja przestrzeni nazw w czasie projektowania. Można to osiągnąć, po prostu dołączając /design na końcu.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Dodawanie prefiksu czasu projektowania do mc:Ignorable

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Po zakończeniu wszystkich tych kroków możesz użyć prefiksu do `myDesignTimeControls` utworzenia kontrolek czasu projektowania.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Tworzenie niestandardowej przestrzeni nazw xmlns

Aby utworzyć niestandardową przestrzeń nazw xmlns na platformie WPF .NET Core, musisz zamapować niestandardową przestrzeń nazw XML na przestrzeń nazw CLR, w których znajdują się kontrolki. Można to zrobić, dodając atrybut `XmlnsDefinition` na poziomie zestawu w `AssemblyInfo.cs` pliku. Plik znajduje się w hierarchii głównej projektu.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpi problem, który nie został wymieniony w tej sekcji, daj nam znać za pomocą narzędzia [Zgłoś](../ide/how-to-report-a-problem-with-visual-studio.md) problem.

### <a name="requirements"></a>Wymagania

- Dane czasu projektowania wymagają programu Visual Studio 2019 w wersji [16.7 lub](/visualstudio/releases/2019/release-notes-v16.7) nowszej.

- Obsługuje projekty pulpitu systemu Windows, które Windows Presentation Foundation (WPF) dla platformy .NET Core i platformy uniwersalnej systemu Windows. Ta funkcja jest również dostępna dla .NET Framework w kanale [w wersji zapoznawczej.](/visualstudio/releases/2019/release-notes-preview) Aby ją włączyć, przejdź do opcji Narzędzia Funkcje środowiska w wersji  >    >    >  **zapoznawczej,** wybierz pozycję Nowy projektant XAML **WPF** dla wersji .NET Framework a następnie ponownie uruchom Visual Studio.

- Począwszy od Visual Studio 2019 r. w wersji 16.7, ta funkcja działa ze wszystkimi kontrolkami WPF i UWP. Obsługa kontrolek innych firm jest teraz dostępna w [wersji 16.8.](/visualstudio/releases/2019/release-notes/)

### <a name="the-xaml-designer-stopped-working"></a>Działanie projektant XAML przestało działać

Spróbuj zamknąć i ponownie otworzyć plik XAML oraz czyścić i ponownie kompilować projekt.

## <a name="see-also"></a>Zobacz też

- [Dane czasu projektowania za pomocą programu podglądu platformy Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [Język XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Język XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [Język XAML w aplikacjach platformy Xamarin.Forms](/xamarin/xamarin-forms/xaml/)