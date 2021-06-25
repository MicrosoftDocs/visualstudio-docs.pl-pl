---
title: Edytor kolorów VSIX | Microsoft Docs
description: Dowiedz się więcej o Visual Studio edytora kolorów rozszerzenia, które umożliwia tworzenie i edytowanie kolorów niestandardowych Visual Studio i generowanie kluczy zasobów motywu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95fec01beabb66180089a75e772b40788a1f7f0d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898943"
---
# <a name="vsix-color-editor"></a>Edytor kolorów VSIX
Narzędzie Visual Studio Color Editor rozszerzenia może tworzyć i edytować kolory niestandardowe dla Visual Studio. Narzędzie może również generować klucze zasobów motywu, dzięki czemu kolory mogą być używane w kodzie. To narzędzie jest przydatne do tworzenia kolorów dla rozszerzenia Visual Studio, które obsługuje kolory. To narzędzie umożliwia otwieranie plików pkgdef i .xml plików. Visual Studio (pliki vstheme) mogą być używane z edytorem kolorów rozszerzenia Visual Studio, zmieniając rozszerzenie pliku na .xml. Ponadto pliki .vstheme można importować do bieżącego .xml plików.

 ![VSIX Color Editor Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "Hero edytora kolorów VSIX")

 **Pliki definicji pakietów**

 Pliki definicji pakietu (pkgdef) to pliki definiujące motywy. Same kolory są przechowywane w plikach kolorów .xml, które są kompilowane do pliku pkgdef. Pliki .pkgdef są wdrażane w Visual Studio lokalizacji z wyszukiwaniem, przetwarzane w czasie uruchamiania i scalane w celu zdefiniowania motywów.

 **Tokeny kolorów**

 Token koloru składa się z czterech elementów:

- **Nazwa kategorii:** Grupowanie logiczne dla zestawu kolorów. Użyj istniejącej nazwy kategorii, jeśli istnieją już kolory specyficzne dla żądanego elementu interfejsu użytkownika lub grupy elementów interfejsu użytkownika.

- **Nazwa tokenu:** Opisowa nazwa tokenu kolorów i zestawów tokenów. Zestawy zawierają nazwy tokenów tła i pierwszego planu (tekst) oraz wszystkie ich stany. Powinny one mieć nazwę, aby można było łatwo zidentyfikować pary i stany, do których mają zastosowanie.

- **Wartości kolorów (lub odcienie):** Wymagany dla każdego kolorowego motywu. Zawsze twórz wartości koloru tła i tekstu w parach. Kolory są sparowane dla tła/pierwszego planu, dzięki czemu kolor tekstu (pierwszego planu) jest zawsze czytelny względem koloru tła, na którym jest rysowany. Te kolory są połączone i będą używane razem w interfejsie użytkownika. Jeśli tło nie jest przeznaczone do użycia z tekstem, nie należy definiować koloru pierwszego planu.

- **Nazwa koloru systemu:** Do użytku na ekranach o dużym kontraście.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 W miarę możliwości i tam, gdzie to możliwe, istniejące Visual Studio powinny być ponownie używane, a nie nowe. Jednak w przypadkach, gdy nie zdefiniowano odpowiednich kolorów, należy utworzyć kolory niestandardowe, aby zachować zgodność z tematami rozszerzeń.

 **Tworzenie nowych tokenów kolorów**

 Aby utworzyć kolory niestandardowe przy użyciu edytora Visual Studio rozszerzenia, wykonaj następujące kroki:

1. Określ nazwy kategorii i tokenów dla nowych tokenów kolorów.

2. Wybierz kolory, których element interfejsu użytkownika będzie używać dla każdego motywu, oraz kolor systemu dla duży kontrast.

3. Użyj edytora kolorów, aby utworzyć nowe tokeny kolorów.

4. Użyj kolorów w rozszerzeniu Visual Studio.

5. Przetestuj zmiany w Visual Studio.

   **Krok 1. Określ nazwy kategorii i tokenów dla nowych tokenów kolorów.**

   Preferowany schemat nazewnictwa dla obiektu VSColor to **[Kategoria] [typ interfejsu użytkownika] [State]**. Nie używaj słowa "color" w nazwach VSColor, ponieważ jest ono nadmiarowe.

   Nazwy kategorii zapewniają logiczne grupowania i powinny być zdefiniowane tak wąsko, jak to możliwe. Na przykład nazwa pojedynczego okna narzędzi może być nazwą kategorii, ale nie jest nazwą całej jednostki biznesowej lub zespołu projektu. Grupowanie wpisów w kategorie pomaga uniknąć pomyłek między kolorami o tej samej nazwie.

   Nazwa tokenu musi wyraźnie wskazywać typ elementu i sytuacje lub "stan", dla których zostanie zastosowany kolor. Na przykład typ [typ interfejsu **użytkownika]** aktywnej etykietki danych może mieć nazwę **"DataTip",** a element **[State]** może mieć nazwę "**Active**,", co spowoduje, że kolor będzie miał nazwę "**DataTipActive".** Ponieważ napiwki danych zawierają tekst, należy zdefiniować zarówno kolor pierwszego planu, jak i tła. Za pomocą parowania tła/pierwszego planu edytor kolorów automatycznie utworzy kolory "**DataTipActive**" dla tła i "**DataTipActiveText**" dla pierwszego planu.

   Jeśli element interfejsu użytkownika ma tylko jeden stan, część **nazwy [State]** może zostać pominięta. Jeśli na przykład pole wyszukiwania ma obramowanie i nie ma zmiany stanu, która miałaby wpływ na kolor obramowania, nazwę tokenu koloru obramowania można po prostu nazwać "**SearchBoxBorder**."

   Niektóre nazwy pospolitych stanu to:

- Aktywna

- Nieaktywne

- Mouseover

- Mousedown

- Wybrane

- Ustawiono fokus

  Przykłady kilku nazw tokenów dla części kontrolki elementu listy:

- Listitem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Krok 2. Wybierz kolory, które będą przez element interfejsu użytkownika dla każdego motywu, oraz kolor systemu dla duży kontrast.**

  Podczas wybierania kolorów niestandardowych dla interfejsu użytkownika wybierz podobny istniejący element interfejsu użytkownika i użyj jego kolorów jako podstawy. Kolory elementów interfejsu użytkownika w polu zostały poddane przeglądowi i testom, więc będą wyglądać odpowiednio i zachowywać się poprawnie we wszystkich motywach.

  **Krok 3. Użyj edytora kolorów, aby utworzyć nowe tokeny kolorów.**

  Uruchom edytor kolorów i otwórz lub utwórz nowe kolory motywu niestandardowego .xml pliku. Wybierz **z > pozycję Edytuj** nowy kolor. Spowoduje to otwarcie okna dialogowego określającego kategorię i co najmniej jedną nazwę wpisów kolorów w tej kategorii:

  ![Nowy kolor w edytorze kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nowy kolor w edytorze kolorów VSIX")

  Wybierz istniejącą kategorię lub wybierz **pozycję Nowa kategoria,** aby utworzyć nową kategorię. Zostanie otwarte kolejne okno dialogowe, tworząc nową nazwę kategorii:

  ![VSIX Color Editor New Category](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nowa kategoria w edytorze kolorów VSIX")

  Nowa kategoria stanie się następnie dostępna z menu rozwijanego **Nowa** kategoria koloru. Po wybraniu kategorii wprowadź jedną nazwę w każdym wierszu dla każdego nowego tokenu koloru i po zakończeniu wybierz pozycję "Utwórz":

  ![Edytor kolorów VSIX Nowy wypełniony kolor](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Edytor kolorów VSIX Nowy wypełniony kolor")

  Wartości kolorów są wyświetlane w parach tła/pierwszego planu z wartością "Brak" wskazującą, że kolor nie został zdefiniowany. Uwaga: jeśli kolor nie ma pary kolorów tekstu/tła, należy zdefiniować tylko tło.

  ![Wartości kolorów edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Wartości kolorów edytora kolorów VSIX")

  Aby edytować token kolorów, wybierz wpis koloru dla motywu (kolumny) tego tokenu. Dodaj wartość koloru, wpisując wartość koloru hex w 8-cyfrowym formacie ARGB, wprowadzając nazwę koloru systemu w komórce lub używając menu rozwijanego, aby wybrać żądany kolor za pomocą zestawu suwaków kolorów lub listy kolorów systemowych.

  ![Edytuj kolor w edytorze kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Edytuj kolor w edytorze kolorów VSIX")

  ![Tło edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Tło edytora kolorów VSIX")

  W przypadku składników, które nie muszą wyświetlać tekstu, wprowadź tylko jedną wartość koloru: kolor tła. W przeciwnym razie wprowadź wartości koloru tła i tekstu oddzielone ukośnikiem.

  Podczas wprowadzania wartości dla duży kontrast wprowadź prawidłowe nazwy kolorów systemu Windows. Nie należy wprowadzać wartości ARGB na dysku. Listę prawidłowych nazw kolorów systemu można wyświetlić, wybierając pozycję "Tło: System" lub "Foreground: System" z menu rozwijanych wartości kolorów. Podczas tworzenia elementów, które mają składniki tekstowe, należy użyć poprawnej pary kolorów systemu tła/tekstu lub tekst może być nieczytelny.

  Po zakończeniu tworzenia, ustawiania i edytowania tokenów kolorów zapisz je w żądanym formacie .xml pkgdef. Tokeny kolorów z tłem ani zestawem pierwszego planu zostaną zapisane jako puste kolory w formacie .xml, ale odrzucone w formacie PKGDEF. W przypadku próby zapisania pustych kolorów w pliku pkgdef zostanie wyświetlone okno dialogowe z ostrzeżeniem o potencjalnej utracie kolorów.

  **Krok 4. Użyj kolorów w rozszerzeniu Visual Studio rozszerzenia.**

  Po zdefiniowaniu nowych tokenów kolorów uwzględnij plik pkgdef w pliku projektu z ustawieniem "Akcja kompilacji" ustawionym na wartość "Zawartość", a "Uwzględnij w VSIX" ustawionym na wartość "True".

  ![Edytor kolorów VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Edytor kolorów VSIX pkgdef")

  W edytorze Visual Studio kolorów rozszerzenia wybierz pozycję Plik > Wyświetl kod zasobu, aby wyświetlić kod używany do uzyskiwania dostępu do kolorów niestandardowych w interfejsie użytkownika opartym na platformie WPF.

  ![Przeglądarka kodu zasobów edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Przeglądarka kodu zasobów edytora kolorów VSIX")

  Uwzględnij ten kod w klasie statycznej w projekcie. Odwołanie do **pliku Microsoft.VisualStudio.Shell \<VSVersion>.0.dll** należy dodać do projektu, aby używać typu **ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Umożliwia to dostęp do kolorów w kodzie XAML i umożliwia interfejsowi użytkownika reagowanie na zmiany motywu.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Krok 5. Testowanie zmian w Visual Studio.**

 Edytor kolorów może tymczasowo zastosować tokeny kolorów do uruchomionych wystąpień rozszerzenia Visual Studio wyświetlić zmiany kolorów na żywo bez ponownego kompilowania pakietu rozszerzenia. W tym celu kliknij przycisk "Zastosuj ten motyw do uruchomionych Visual Studio windows" znajdujący się w nagłówku każdej kolumny motywu. Ten motyw tymczasowy zniknie po zamknięciu edytora kolorów VSIX.

 ![Zastosowanie edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Zastosowanie edytora kolorów VSIX")

 Aby zmiany stały, ponownie skompilować i ponownie Visual Studio rozszerzenia po dodaniu nowych kolorów do pliku pkgdef i napisaniu kodu, który będzie używać tych kolorów. Ponowne skompilowanie Visual Studio scali wartości rejestru dla nowych kolorów z resztą motywów. Następnie ponownie Visual Studio, wyświetl interfejs użytkownika i sprawdź, czy nowe kolory są wyświetlane zgodnie z oczekiwaniami.

## <a name="notes"></a>Uwagi
 To narzędzie jest przeznaczone do tworzenia kolorów niestandardowych dla wcześniej Visual Studio motywów lub do edytowania kolorów niestandardowego Visual Studio motywu. Aby utworzyć pełne niestandardowe Visual Studio motywów, pobierz rozszerzenie [edytora](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) motywów Visual Studio kolorów z galerii Visual Studio Extensions.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 **Dane wyjściowe koloru XML**

 Plik .xml wygenerowany przez narzędzie będzie podobny do tego:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Dane wyjściowe koloru PKGDEF**

 Plik pkgdef wygenerowany przez narzędzie będzie podobny do tego:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Otoka kluczy zasobów języka C#**

 Klucze zasobów kolorów wygenerowane przez narzędzie będą podobne do tych:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Otoka słownika zasobów WPF**

 Kolor kluczy **ResourceDictionary** wygenerowanych przez narzędzie będzie podobny do tego:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
