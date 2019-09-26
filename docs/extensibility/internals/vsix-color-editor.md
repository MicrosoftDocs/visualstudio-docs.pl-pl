---
title: Edytor kolorów VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bc9381cd1fbd0cf03242683d3fcfb1ea39b8f0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252472"
---
# <a name="vsix-color-editor"></a>Edytor kolorów VSIX
Narzędzie edytora kolorów rozszerzenia programu Visual Studio umożliwia tworzenie i edytowanie niestandardowych kolorów dla programu Visual Studio. Narzędzie może również generować klucze zasobów motywu, aby można było używać ich w kodzie. To narzędzie jest przydatne do tworzenia kolorów dla rozszerzenia programu Visual Studio, które obsługuje Tworzenie motywów. To narzędzie może otwierać pliki pkgdef i XML. Motywy programu Visual Studio (pliki. vstheme) mogą być używane z edytorem kolorów rozszerzenia programu Visual Studio, zmieniając rozszerzenie pliku na. XML. Ponadto pliki vstheme można zaimportować do bieżącego pliku. XML.

 ![Hero edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Hero edytora kolorów VSIX")

 **Pliki definicji pakietów**

 Pliki definicji pakietów (. pkgdef) to pliki, które definiują motywy. Same kolory są przechowywane w plikach Theme Color. XML, które są kompilowane w pliku. pkgdef. Pliki. pkgdef są wdrażane w lokalizacjach wyszukiwania programu Visual Studio, przetwarzane w czasie wykonywania i scalane w celu zdefiniowania motywów.

 **Tokeny koloru**

 Token koloru składa się z czterech elementów:

- **Nazwa kategorii:** Grupowanie logiczne dla zestawu kolorów. Użyj istniejącej nazwy kategorii, jeśli istnieją już kolory specyficzne dla żądanego elementu interfejsu użytkownika lub grupy elementów interfejsu użytkownika.

- **Nazwa tokenu:** Opisowa nazwa tokenu koloru i zestawów tokenów. Zestawy obejmują nazwy tokenów w tle i pierwszego planu (tekst), a także wszystkie ich Stany, które powinny być nazwane, aby można było łatwo identyfikować pary i Stany, do których mają zastosowanie.

- **Wartości koloru (lub odcieni):** Wymagany dla każdego kolorowego motywu. Zawsze twórz wartości koloru tła i tekstu w parach. Kolory są sparowane dla tła/pierwszego planu, tak aby kolor tekstu (pierwszego planu) był zawsze odczytywany względem koloru tła, na którym jest rysowany. Te kolory są połączone i będą używane razem w interfejsie użytkownika. Jeśli tło nie jest przeznaczone do użycia z tekstem, nie Definiuj koloru pierwszego planu.

- **Nazwa koloru systemu:** Do użycia w przypadku ekranów o wysokim kontraście.

## <a name="how-to-use-the-tool"></a>Jak używać narzędzia
 Tak dużo jak to możliwe, a tam, gdzie to konieczne, istniejące kolory programu Visual Studio powinny być ponownie używane zamiast tworzenia nowych. Jednak w przypadku, gdy nie są zdefiniowane żadne odpowiednie kolory, należy utworzyć kolory niestandardowe, aby zachować zgodność z rozszerzeniem.

 **Tworzenie nowych tokenów kolorów**

 Aby utworzyć kolory niestandardowe przy użyciu edytora kolorów rozszerzenia programu Visual Studio, wykonaj następujące kroki:

1. Określ nazwę kategorii i tokenów dla nowych tokenów kolorów.

2. Wybierz odcieni, który będzie używany przez element interfejsu użytkownika dla każdego motywu i kolor systemu dla duży kontrast.

3. Użyj edytora kolorów, aby utworzyć nowe tokeny koloru.

4. Użyj kolorów w rozszerzeniu programu Visual Studio.

5. Przetestuj zmiany w programie Visual Studio.

   **Krok 1. Określ nazwę kategorii i tokenów dla nowych tokenów kolorów.**

   Preferowanym schematem nazewnictwa dla VSColor jest **[Kategoria] [typ interfejsu użytkownika] [stan]** . Nie używaj słowa "Color" w nazwach VSColor, ponieważ są one nadmiarowe.

   Nazwy kategorii zapewniają logiczne grupowania i powinny być zdefiniowane w możliwie najwęższy sposób. Na przykład nazwa pojedynczego okna narzędzi może być nazwą kategorii, ale nie jest to nazwa całej jednostki biznesowej lub zespołu projektu. Grupowanie wpisów w kategorie pozwala uniknąć pomyłek między kolorami o tej samej nazwie.

   Nazwa tokenu musi jasno wskazywać typ elementu i sytuacje, lub "State", dla których zostanie zastosowany kolor. Na przykład aktywna etykietka danych **(typ interfejsu użytkownika)** może mieć nazwę "**etykietki danych**", a **[State]** może mieć nazwę "**Active**", co spowoduje utworzenie koloru "**DataTipActive**". Ponieważ porady dotyczące danych mają tekst, należy zdefiniować zarówno pierwszy plan, jak i kolor tła. Przy użyciu parowania tła/pierwszego planu, Edytor kolorów automatycznie utworzy kolory "**DataTipActive**" dla tła i "**DataTipActiveText**" na pierwszym planie.

   Jeśli element interfejsu użytkownika ma tylko jeden stan, można pominąć część **[State]** nazwy. Na przykład, jeśli pole wyszukiwania ma obramowanie i nie ma żadnych zmian stanu, które mogłyby mieć wpływ na kolor obramowania, wówczas nazwa tokenu koloru obramowania może być po prostu wywoływana jako "**SearchBoxBorder**".

   Poniżej wymieniono niektóre typowe nazwy stanów:

- Aktywne

- Nieaktywne

- MouseOver

- MouseDown

- Wybrane

- Fokus

  Przykłady kilku nazw tokenów dla części kontrolki elementu listy:

- ListItem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Krok 2. Wybierz odcieni, który będzie używany przez element interfejsu użytkownika dla każdego motywu i kolor systemu dla duży kontrast.**

  Wybierając niestandardowe kolory dla interfejsu użytkownika, wybierz podobny istniejący element interfejsu użytkownika i użyj jego kolorów jako podstawy. Kolory dla elementów interfejsu użytkownika w polu zostały poddane przeglądowi i przetestowaniu, więc będą wyglądały odpowiednio i działać poprawnie we wszystkich motywach.

  **Krok 3. Użyj edytora kolorów, aby utworzyć nowe tokeny koloru.**

  Uruchom Edytor kolorów i Otwórz lub Utwórz nowy plik XML niestandardowych kolorów motywu. Wybierz pozycję **edytuj > nowy kolor** z menu. Spowoduje to otwarcie okna dialogowego służącego do określania kategorii i co najmniej jednej nazwy dla wpisów koloru w tej kategorii:

  ![Nowy kolor edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nowy kolor edytora kolorów VSIX")

  Wybierz istniejącą kategorię lub wybierz pozycję **Nowa kategoria** , aby utworzyć nową kategorię. Zostanie otwarte inne okno dialogowe, w którym zostanie utworzona nowa nazwa kategorii:

  ![Nowy kategoria edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Nowy kategoria edytora kolorów VSIX")

  Nowa kategoria stanie się następnie dostępna w nowej kategorii **kolorów** menu rozwijanego. Po wybraniu kategorii Wprowadź jedną nazwę na wiersz dla każdego nowego tokenu koloru i wybierz pozycję "Utwórz" po zakończeniu:

  ![Nowy kolor wypełniony przez Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Nowy kolor wypełniony przez Edytor kolorów VSIX")

  Wartości koloru są pokazywane w parach tła/pierwszego planu, z oznaczeniem "Brak", co oznacza, że kolor nie został zdefiniowany. Uwaga: Jeśli kolor nie ma pary kolorów tekstu/tła, należy zdefiniować tylko tło.

  ![Wartości koloru edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Wartości koloru edytora kolorów VSIX")

  Aby edytować token koloru, wybierz wpis koloru dla motywu (kolumny) tego tokenu. Dodaj wartość koloru, wpisując szesnastkową wartość koloru w 8-cyfrowym formacie ARGB, wprowadzając nazwę koloru systemowego do komórki lub korzystając z menu rozwijanego, aby wybrać odpowiedni kolor za pośrednictwem zestawu suwaków kolorów lub listy kolorów systemu.

  ![Kolor edycji edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Kolor edycji edytora kolorów VSIX")

  ![Tło edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Tło edytora kolorów VSIX")

  W przypadku składników, które nie muszą wyświetlać tekstu, wprowadź tylko jedną wartość koloru: kolor tła. W przeciwnym razie wprowadź wartości dla kolorów tła i tekstu oddzielone ukośnikiem.

  Wprowadzając wartości duży kontrast, wprowadź prawidłowe nazwy kolorów systemu Windows. Nie należy wprowadzać wartości stałe ARGB. Listę prawidłowych nazw kolorów systemu można wyświetlić, wybierając pozycję "tło: System "lub" pierwszy plan: System "z menu rozwijanego wartość koloru. Podczas tworzenia elementów, które mają składniki tekstowe, użyj prawidłowej pary kolorów tła/tekstu lub tekst może być nieczytelny.

  Po zakończeniu tworzenia, ustawiania i edytowania tokenów kolorów Zapisz je w żądanym formacie XML lub pkgdef. Tokeny koloru bez tła ani zestawu pierwszego planu nie będą zapisywane jako puste kolory w formacie. XML, ale zostały odrzucone w formacie. pkgdef. W oknie dialogowym zostanie wyświetlone ostrzeżenie o potencjalnej utracie kolorów w przypadku próby zapisania pustych kolorów w pliku. pkgdef.

  **Krok 4. Użyj kolorów w rozszerzeniu programu Visual Studio.**

  Po zdefiniowaniu nowych tokenów kolorów Uwzględnij plik. pkgdef w pliku projektu z ustawioną opcją "Akcja kompilacji" na "Content", a w polu "Dołącz do VSIX" Ustaw wartość "true".

  ![Pkgdef edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Pkgdef edytora kolorów VSIX")

  W edytorze kolorów rozszerzenia programu Visual Studio wybierz kolejno pozycje Plik > Wyświetl kod zasobu, aby wyświetlić kod, który jest używany do uzyskiwania dostępu do niestandardowych kolorów w interfejsie użytkownika opartym na technologii WPF.

  ![Podgląd kodu zasobów edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Podgląd kodu zasobów edytora kolorów VSIX")

  Uwzględnij ten kod w klasie statycznej w projekcie. Odwołanie do **Microsoft. VisualStudio.\< Shell. VSVersion > 0. dll** należy dodać do projektu, aby użyć typu **elementu themeresourcekey** .

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

 Zapewnia to dostęp do kolorów w kodzie XAML i umożliwia interfejsowi użytkownika reagowanie na zmiany motywu.

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

 **Krok 5. Przetestuj zmiany w programie Visual Studio.**

 Edytor kolorów może tymczasowo zastosować tokeny koloru do uruchomionych wystąpień programu Visual Studio, aby wyświetlić zmiany na żywo na kolorach bez ponownego kompilowania pakietu rozszerzenia. Aby to zrobić, kliknij przycisk "Zastosuj ten motyw w celu uruchomienia programu Visual Studio Windows" znajdującego się w nagłówku każdej kolumny motywu. Ten tymczasowy motyw zostanie odsunięty, gdy Edytor kolorów VSIX zostanie zamknięty.

 ![Zastosowanie edytora kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Zastosowanie edytora kolorów VSIX")

 Aby zmiany były trwałe, należy ponownie skompilować i wdrożyć rozszerzenie programu Visual Studio po dodaniu nowych kolorów do pliku. pkgdef i napisania kodu, który będzie używać tych kolorów. Ponowne skompilowanie rozszerzenia programu Visual Studio spowoduje scalenie wartości rejestru dla nowych kolorów w pozostałej części motywów. Następnie uruchom ponownie program Visual Studio, Wyświetl interfejs użytkownika i sprawdź, czy nowe kolory są wyświetlane zgodnie z oczekiwaniami.

## <a name="notes"></a>Uwagi
 To narzędzie jest przeznaczone do tworzenia niestandardowych kolorów dla istniejących motywów programu Visual Studio lub do edycji kolorów niestandardowego motywu programu Visual Studio. Aby utworzyć kompletne niestandardowe motywy programu Visual Studio, Pobierz [rozszerzenie Edytor motywu kolorów programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) z galerii rozszerzeń programu Visual Studio.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 **Wyjście koloru XML**

 Plik XML wygenerowany przez narzędzie będzie wyglądać podobnie do tego:

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

 Plik. pkgdef wygenerowany przez narzędzie będzie wyglądać podobnie do tego:

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

 **C#otoka kluczy zasobów**

 Klucze zasobów koloru wygenerowane przez narzędzie będą podobne do tego:

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

 Klucze **ResourceDictionary** kolorów generowane przez narzędzie będą podobne do tego:

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