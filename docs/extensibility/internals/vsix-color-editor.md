---
title: Edytor kolorów VSIX | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704041"
---
# <a name="vsix-color-editor"></a>Edytor kolorów VSIX
Narzędzie Edytor kolorów rozszerzenia programu Visual Studio może tworzyć i edytować niestandardowe kolory programu Visual Studio. Narzędzie może również generować klucze zasobów motywu, dzięki czemu kolory mogą być używane w kodzie. To narzędzie jest przydatne do tworzenia kolorów dla rozszerzenia programu Visual Studio, który obsługuje motywy. To narzędzie może otwierać pliki pkgdef i xml. Motywy programu Visual Studio (pliki vstheme) mogą być używane z Edytorem kolorów rozszerzenia programu Visual Studio, zmieniając rozszerzenie pliku na xml. Ponadto pliki vstheme można zaimportować do bieżącego pliku xml.

 ![VSIX Color Editor Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Color Editor Hero")

 **Pliki definicji pakietów**

 Pliki definicji pakietu (pkgdef) to pliki definiujące motywy. Same kolory są przechowywane w kolorach motywu .xml plików, które są kompilowane do pliku pkgdef. Pliki pkgdef są wdrażane w lokalizacjach z wyszukujalnymi w programie Visual Studio, przetwarzane w czasie wykonywania i scalane w celu definiowania motywów.

 **Tokeny kolorów**

 Kolor tokenu składa się z czterech elementów:

- **Nazwa kategorii:** Logiczne grupowanie dla zestawu kolorów. Użyj istniejącej nazwy kategorii, jeśli istnieją już kolory, które są specyficzne dla żądanego elementu interfejsu użytkownika lub grupy elementów interfejsu użytkownika.

- **Nazwa tokenu:** Opisowa nazwa zestawów tokenów kolorów i tokenów. Zestawy obejmują nazwy tokenów tła i pierwszego planu (tekst), a także wszystkie ich stany, a te powinny być nazwane, aby łatwo identyfikować pary i stany, do których się odnoszą.

- **Wartości kolorów (lub odcieni):** Potrzebne dla każdego kolorowego motywu. Zawsze należy tworzyć wartości kolorów tła i tekstu w parach. Kolory są sparowane dla tła/pierwszego planu, dzięki czemu kolor tekstu (pierwszego planu) jest zawsze czytelny na tle, na którym jest rysowany. Kolory te są połączone i będą używane razem w interfejsie użytkownika. Jeśli tło nie jest przeznaczone do użytku z tekstem, nie należy definiować koloru pierwszego planu.

- **Nazwa koloru systemu:** Do stosowania w wyświetlaczach o wysokim kontraście.

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 W miarę możliwości i w stosownych przypadkach istniejące kolory programu Visual Studio powinny być ponownie stosowane zamiast tworzenia nowych. Jednak w przypadkach, gdy nie zdefiniowano odpowiednich kolorów, należy utworzyć kolory niestandardowe, aby zachować zgodność motywów rozszerzenia.

 **Tworzenie nowych tokenów kolorów**

 Aby utworzyć niestandardowe kolory za pomocą Edytora kolorów rozszerzenia programu Visual Studio, wykonaj następujące kroki:

1. Określ nazwy kategorii i tokenów dla nowych tokenów kolorów.

2. Wybierz barwy, które będzie używany przez element interfejsu użytkownika dla każdego motywu i kolor systemu dla wysokiego kontrastu.

3. Użyj edytora kolorów, aby utworzyć nowe tokeny kolorów.

4. Użyj kolorów w rozszerzeniu programu Visual Studio.

5. Przetestuj zmiany w programie Visual Studio.

   **Krok 1: Określ nazwy kategorii i tokenów dla nowych tokenów kolorów.**

   Preferowanym schematem nazewnictwa vscolor jest **[Kategoria] [Typ interfejsu użytkownika] [Stan]**. Nie należy używać słowa "kolor" w nazwach VSColor, ponieważ jest ono zbędne.

   Nazwy kategorii zapewniają logiczne grupowania i powinny być definiowane tak wąsko, jak to możliwe. Na przykład nazwa pojedynczego okna narzędzia może być nazwą kategorii, ale nazwa całej jednostki biznesowej lub zespołu projektu nie jest. Grupowanie wpisów w kategorie pomaga zapobiegać pomyłce kolorów o tej samej nazwie.

   Nazwa tokenu musi wyraźnie wskazywać typ elementu i sytuacje lub "stan", dla którego zostanie zastosowany kolor. Na przykład aktywny typ **[typu interfejsu użytkownika]** końcówki danych może być nazwany **"DataTip",** a **[Stan]** może być nazwany **"Aktywny",** co spowoduje nazwę koloru "**DataTipActive**." Ponieważ wskazówki dotyczące danych mają tekst, należy zdefiniować zarówno kolor pierwszego planu, jak i tło. Korzystając z parowania tła/pierwszego planu, edytor kolorów automatycznie utworzy kolory "**DataTipActive**" dla tła i "**DataTipActiveText**" dla pierwszego planu.

   Jeśli element interfejsu użytkownika ma tylko jeden stan, **[State]** część nazwy można pominąć. Na przykład, jeśli pole wyszukiwania ma obramowanie i nie ma zmiany stanu, która miałaby wpływ na kolor obramowania, nazwa koloru tokenu obramowania może być po prostu nazywana "**SearchBoxBorder**."

   Niektóre typowe nazwy państw obejmują:

- Aktywne

- Nieaktywne

- Mouseover

- Mousedown

- Wybrano

- Ustawiono fokus

  Przykłady kilku nazw tokenów dla części formantu elementu listy:

- Listitem

- ListItemBorder (ListItemBorder)

- ListaItemMouseOver

- ListItemMouseOverBorder

- ListaWybrana

- ListItemSelectedBorder

- ListaItemDisabled

- ListaItemDisabledBorder

  **Krok 2: Wybierz barwy, które będzie używany przez element interfejsu użytkownika dla każdego motywu i kolor systemu dla wysokiego kontrastu.**

  Wybierając kolory niestandardowe dla interfejsu użytkownika, wybierz podobny istniejący element interfejsu użytkownika i użyj jego kolorów jako podstawy. Kolory elementów interfejsu użytkownika w polu zostały poddane przeglądowi i testom, dzięki czemu będą wyglądać odpowiednio i zachowywać się poprawnie we wszystkich motywach.

  **Krok 3: Użyj edytora kolorów, aby utworzyć nowe tokeny kolorów.**

  Uruchom edytor kolorów i otwórz lub utwórz nowy niestandardowy plik xml o kolorach motywu. Z menu **wybierz polecenie Edytuj > Nowy kolor.** Spowoduje to otwarcie okna dialogowego określającego kategorię i jedną lub więcej nazw wpisów kolorów w tej kategorii:

  ![Vsix Color Editor Nowy kolor](../../extensibility/internals/media/vsix-color-editor-new-color.png "Vsix Color Editor Nowy kolor")

  Wybierz istniejącą kategorię lub wybierz **pozycję Nowa kategoria,** aby utworzyć nową kategorię. Otworzy się kolejne okno dialogowe, tworząc nową nazwę kategorii:

  ![VSIX Color Editor Nowa kategoria](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Color Editor Nowa kategoria")

  Nowa kategoria będzie wtedy dostępna w menu rozwijanym Kategoria **Nowy kolor.** Po wybraniu kategorii wprowadź jedną nazwę na wiersz dla każdego nowego tokenu kolorowego i wybierz "Utwórz" po zakończeniu:

  ![Vsix Color Editor Nowy kolor wypełniony](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Vsix Color Editor Nowy kolor wypełniony")

  Wartości kolorów są wyświetlane w parach tła/pierwszego planu, z napisem "Brak" wskazującym, że kolor nie został zdefiniowany. Uwaga: jeśli kolor nie ma pary kolorów tekstu/tła, należy zdefiniować tylko tło.

  ![Wartości kolorów edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Wartości kolorów edytora kolorów VSIX")

  Aby edytować token kolorów, wybierz wpis koloru dla motywu (kolumny) tego tokenu. Dodaj wartość koloru, wpisując wartość koloru szesnastkowego w 8-cyfrowym formacie ARGB, wprowadzając nazwę koloru systemowego do komórki, lub korzystając z menu rozwijanego, aby wybrać żądany kolor za pomocą zestawu suwaków kolorów lub listy kolorów systemowych.

  ![Edytor kolorów VSIX Edytuj kolor](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Edytor kolorów VSIX Edytuj kolor")

  ![Tło edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Tło edytora kolorów VSIX")

  W przypadku komponentów, które nie muszą wyświetlać tekstu, wprowadź tylko jedną wartość koloru: kolor tła. W przeciwnym razie wprowadź wartości zarówno dla koloru tła, jak i tekstu, oddzielone ukośnikiem do przodu.

  Podczas wprowadzania wartości dla wysokiego kontrastu wprowadź prawidłowe nazwy kolorów systemu Windows. Nie należy wprowadzać zakodowanych na stałe wartości ARGB. Listę prawidłowych nazw kolorów systemu można wyświetlić, wybierając "Tło: System" lub "Pierwszy plan: System" z menu rozwijanych wartości kolorów. Podczas tworzenia elementów, które mają składniki tekstu, należy użyć poprawnej pary kolorów systemu tła/tekstu lub tekst może być nieczytelny.

  Po zakończeniu tworzenia, ustawiania i edytowania tokenów kolorów zapisz je w żądanym formacie xml lub pkgdef. Tokeny kolorów bez tła ani zestawu pierwszego planu nie zostaną zapisane jako puste kolory w formacie xml, ale odrzucone w formacie pkgdef. Okno dialogowe ostrzega o potencjalnej utracie kolorów, jeśli spróbujesz zapisać puste kolory w pliku pkgdef.

  **Krok 4: Użyj kolorów w rozszerzeniu programu Visual Studio.**

  Po zdefiniowaniu nowych tokenów kolorów, uwzględnij .pkgdef w pliku projektu z "Build Action" ustawiony na "Zawartość" i "Dołącz w VSIX" ustawiony na "True".

  ![Vsix Color Editor pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Vsix Color Editor pkgdef")

  W Edytorze kolorów rozszerzenia programu Visual Studio wybierz pozycję Plik > Kod zasobu widoku, aby wyświetlić kod używany do uzyskiwania dostępu do niestandardowych kolorów w interfejsie użytkownika opartym na WPF.

  ![Przeglądarka kodu edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Przeglądarka kodu edytora kolorów VSIX")

  Dołącz ten kod w klasie statycznej w projekcie. Odwołanie do **pliku Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** musi zostać dodany do projektu, aby użyć **ThemeResourceKey** typu.

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

 **Krok 5: Testowanie zmian w programie Visual Studio.**

 Edytor kolorów można tymczasowo zastosować tokeny kolorów do uruchomionych wystąpień programu Visual Studio, aby wyświetlić zmiany na żywo do kolorów bez przebudowy pakietu rozszerzenia. Aby to zrobić, kliknij przycisk "Zastosuj ten motyw do uruchamiania okien programu Visual Studio" znajdujący się w nagłówku każdej kolumny motywu. Ten tymczasowy motyw zniknie po zamknięciu edytora kolorów VSIX.

 ![Zastosowanie edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Zastosowanie edytora kolorów VSIX")

 Aby zmiany były trwałe, należy przebudować i ponownie wdrożyć rozszerzenie programu Visual Studio po dodaniu nowych kolorów do pliku pkgdef i zapisaniu kodu, który będzie używał tych kolorów. Przebudowa rozszerzenia programu Visual Studio scali wartości rejestru dla nowych kolorów do pozostałych motywów. Następnie ponownie wyelikuj program Visual Studio, wyświetl interfejs użytkownika i sprawdź, czy nowe kolory są wyświetlane zgodnie z oczekiwaniami.

## <a name="notes"></a>Uwagi
 To narzędzie jest przeznaczone do tworzenia niestandardowych kolorów dla istniejących wcześniej motywów programu Visual Studio lub do edytowania kolorów niestandardowego motywu programu Visual Studio. Aby utworzyć pełne niestandardowe motywy programu Visual Studio, pobierz [rozszerzenie Edytora motywów color studio programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) z Galerii rozszerzeń programu Visual Studio.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 **Dane wyjściowe kolorów XML**

 Plik xml wygenerowany przez narzędzie będzie podobny do tego:

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

 **Wyjście kolorów PKGDEF**

 Plik .pkgdef wygenerowany przez narzędzie będzie podobny do tego:

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

 Kolorowe klucze zasobów wygenerowane przez narzędzie będą podobne do tych:

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

 Kolor **ResourceDictionary** klucze generowane przez narzędzie będzie podobny do tego:

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
