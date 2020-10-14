---
title: Używanie danych czasu projektowania z projektant XAML w programie Visual Studio
description: Dowiedz się, jak używać danych czasu projektowania w języku XAML.
ms.date: 09/29/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 9e6daa3e11bc96fe4d0b9499a6a1a7982432583d
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039914"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Używanie danych czasu projektowania z projektant XAML w programie Visual Studio

Niektóre układy są trudne do wizualizacji bez danych. W tym dokumencie będziemy przeglądać jeden z rozwiązań, które deweloperzy pracują nad projektami klasycznymi, mogą używać do tworzenia danych w projektancie XAML. To podejście jest wykonywane przy użyciu istniejącej przestrzeni nazw "d:" z pominięciem. Dzięki temu możesz szybko dodawać dane czasu projektowania do stron lub kontrolek bez konieczności tworzenia pełnego obrazu ViewModel lub po prostu testować, w jaki sposób zmiana właściwości może mieć wpływ na aplikację bez obaw, że te zmiany wpłyną na kompilacje wydań. Wszystkie d: dane są używane tylko przez projektant XAML i żadne wartości przestrzeni nazw, których nie można zignorować, są kompilowane do aplikacji.

> [!NOTE]
> Jeśli używasz platformy Xamarin. Forms, zobacz [dane czasu projektowania platformy Xamarin. Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Podstawowe dane dotyczące czasu projektowania

Dane czasu projektowania to dane, które zostały ustawione, aby ułatwić wizualizację w projektant XAML. Aby rozpocząć, Dodaj następujące wiersze kodu do nagłówka dokumentu XAML, jeśli nie są one jeszcze obecne:

```xml 
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Po dodaniu przestrzeni nazw można umieścić `d:` przed dowolnym atrybutem lub kontrolkę, aby wyświetlić ją tylko w Projektant XAML ale nie w czasie wykonywania.

Na przykład można dodać tekst do bloku textblok, który ma zwykle powiązane z nim dane.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Dane czasu projektowania z tekstem w bloku TextBlock](media\xaml-design-time-textblock.png "Dane czasu projektowania z tekstem etykieta")](media\xaml-design-time-textblock.png#lightbox)

W tym przykładzie, bez `d:Text` , Projektant XAML nie będzie pokazywał niczego dla bloku Text. Zamiast tego wyświetla "name!" miejsce, w którym blok textbędzie miał rzeczywiste dane w czasie wykonywania.

Można używać `d:` z atrybutami dla dowolnej kontrolki platformy UWP lub WPF .NET Core, takich jak kolory, rozmiary czcionek i odstępy. Możesz nawet dodać go do samego formantu.

```xml
<d:Button Content="Design Time Button" />
```

[![Dane czasu projektowania z kontrolką przycisku](media\xaml-design-time-button.png "Dane czasu projektowania z kontrolką przycisku")](media\xaml-design-time-button.png#lightbox)

W tym przykładzie przycisk pojawia się tylko w czasie projektowania. Użyj tej metody, aby umieścić symbol zastępczy w kontrolce niestandardowej lub wypróbować inne kontrolki. Wszystkie `d:` atrybuty i kontrolki zostaną zignorowane podczas wykonywania.

## <a name="preview-images-at-design-time"></a>Podgląd obrazów w czasie projektowania

Można ustawić źródło czasu projektowania dla obrazów, które są powiązane ze stroną lub są ładowane dynamicznie. Dodaj obraz, który ma być wyświetlany w projektant XAML do projektu. Następnie można wyświetlić ten obraz w projektant XAML w czasie projektowania:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Obraz w tym przykładzie musi znajdować się w rozwiązaniu.

## <a name="design-time-data-for-listviews"></a>Dane czasu projektowania dla ListView

Listy kontrolne to popularny sposób wyświetlania danych w aplikacji klasycznej. Jednak trudno jest wizualizować bez żadnych danych. Za pomocą tej funkcji można tworzyć wbudowane ustawieniem właściwości ItemSource danych czasu projektowania. Projektant XAML wyświetla zawartość tablicy w elemencie ListView w czasie projektowania. Jest to przykład dla WPF .NET Core. Aby użyć typu System: String, upewnij się, że dołączasz `xmlns:system="clr-namespace:System;assembly=mscorlib` do nagłówka XAML.

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

[![Dane czasu projektowania z ListView](media\xaml-design-time-listview-strings.png "Dane czasu projektowania z ListView")](media\xaml-design-time-listview-strings.png#lightbox)

Ten poprzedni przykład pokazuje element ListView z trzema blokami TextBlocks w projektant XAML.

Możesz również utworzyć tablicę obiektów danych. Na przykład właściwości publiczne `City` obiektu danych można skonstruować jako dane czasu projektowania.

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

[![Rzeczywisty model w danych czasu projektowania z ListView](media\xaml-design-time-listview-models.png "Rzeczywiste dane modelu czasu projektowania z ListView")](media\xaml-design-time-listview-models.png#lightbox)

Korzyścią jest tutaj, że można powiązać kontrolki z wersją statyczną w czasie projektowania.

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Korzystanie z danych czasu projektowania z niestandardowymi typami i właściwościami

Ta funkcja domyślnie działa tylko z kontrolkami i właściwościami platformy. W tej sekcji przejdziemy do kroków, które należy wykonać, aby umożliwić korzystanie z własnych niestandardowych kontrolek jako formantów czasu projektowania. Aby to umożliwić, należy wykonać trzy wymagania:

- Niestandardowa przestrzeń nazw xmlns 

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Wersja przestrzeni nazw czasu projektowania. Można to osiągnąć przez proste dołączenie/Design na końcu.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Dodawanie prefiksu czasu projektowania do MC: można zignorować

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Po wykonaniu wszystkich tych kroków możesz użyć swojego `myDesignTimeControls` prefiksu, aby utworzyć kontrolki czasu projektowania.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Tworzenie niestandardowej przestrzeni nazw xmlns

Aby utworzyć niestandardową przestrzeń nazw xmlns w WPF .NET Core, należy zmapować niestandardową przestrzeń nazw XML do przestrzeni nazw CLR, w której znajdują się formanty. Możesz to zrobić, dodając `XmlnsDefinition` atrybut poziomu zestawu do `AssemblyInfo.cs` pliku. Plik znajduje się w głównej hierarchii projektu.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpi problem, którego nie ma w tej sekcji, poinformuj nas o tym za pomocą narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Wymagania

- Dane czasu projektowania wymagają programu Visual Studio 2019 w wersji [16,7](/visualstudio/releases/2019/release-notes) lub nowszej.

- Obsługuje projekty klasyczne systemu Windows, które są przeznaczone dla Windows Presentation Foundation (WPF) dla platformy .NET Core i platformy UWP. Ta funkcja jest również dostępna dla .NET Framework, jeśli masz włączoną funkcję wersji zapoznawczej "New WPF projektant XAML for .NET Framework".

- Począwszy od programu Visual Studio 2019 w wersji 16,7, ta funkcja działa ze wszystkimi wbudowanymi kontrolkami z platform WPF i platformy UWP Framework. Obsługa kontrolek innych firm jest teraz dostępna w wersji zapoznawczej 16,8.

### <a name="the-xaml-designer-stopped-working"></a>projektant XAML przestała działać

Spróbuj zamknąć i ponownie otworzyć plik XAML, a następnie wyczyścić i przebudować projekt.

## <a name="see-also"></a>Zobacz też

- [Projektowanie danych czasu przy użyciu programu Xamarin. Forms Preview](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML w aplikacjach WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML w aplikacjach platformy UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML w aplikacjach Xamarin. Forms](/xamarin/xamarin-forms/xaml/)