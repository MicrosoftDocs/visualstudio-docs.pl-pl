---
title: VSIX Color Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83c56adaec939c5244afff44cb5ff6823a6a713
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923285"
---
# <a name="vsix-color-editor"></a>Edytor kolorów VSIX
Narzędzie edytora koloru rozszerzenia programu Visual Studio można tworzyć i edytować kolorów niestandardowych dla programu Visual Studio. Narzędzie można również wygenerować klucze zasobu motywu, czemu kolory, można użyć w kodzie. To narzędzie jest przydatne do tworzenia rozszerzenia programu Visual Studio, który obsługuje motywów kolorów. To narzędzie może otwierać pliki .pkgdef i XML. Visual Studio motywy (.vstheme plików) może służyć za pomocą rozszerzenia kolor Edytor programu Visual Studio, zmieniając rozszerzenie pliku .xml. Ponadto pliki .vstheme można importować do bieżącego pliku .xml.  
  
 ![VSIX Color Editor Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Color Editor Hero")  
  
 **Pliki definicji pakietów**  
  
 Pliki definicji (.pkgdef) pakietu znajdują się pliki, które definiują motywów. Same kolory są przechowywane w plikach XML kolor motywu, które są kompilowane w plik .pkgdef. Pliki .pkgdef są wdrażane do programu Visual Studio można wyszukiwać lokalizacji, przetwarzane w czasie wykonywania i scalone razem do definiowania motywów.  
  
 **Kolor tokenów**  
  
 Token kolor składa się z czterech elementów:  
  
-   **Nazwa kategorii:** Logiczne grupowanie zestaw kolorów. Użyj istniejącej nazwy kategorii, jeśli istnieją już kolorów, które są specyficzne dla żądanego elementu interfejsu użytkownika lub grupy elementów interfejsu użytkownika.  
  
-   **Nazwa tokenu:** Określa nazwę opisową dla koloru, tokenów i tokenów. Zestawy obejmują tła i pierwszego planu (tekst) token nazwy, a także ich stanów, a te powinny mieć nazwę, tak, aby łatwo identyfikować ich pary i stanów, które odnoszą się do.  
  
-   **Wartości kolorów (lub odcieni):** Wymagane dla każdego kolor motywu. Zawsze twórz tekstu i tła kolorów w parach. Kolory są skojarzone dla tła/pierwszego planu, dzięki czemu kolor tekstu jest zawsze czytelny względem koloru tła, na którym jest rysowana. Te kolory są powiązane i będą używane razem w interfejsie użytkownika. Jeśli w tle nie jest przeznaczony do użytku z tekstem, nie definiują kolor pierwszego planu.  
  
-   **Nazwa koloru systemu:** Do użytku w wyświetlaniu o wysokim kontraście.  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 Jak to możliwe, i ile to możliwe, istniejących kolorów programu Visual Studio należy ponownie użyć zamiast deklarowania nowych. Jednak w przypadkach, gdzie są zdefiniowane nie odpowiednie kolory, kolory niestandardowe powinny być tworzone zapewnienie rozszerzenia motywów zgodne.  
  
 **Tworzenie nowych tokenów kolorów**  
  
 Aby utworzyć kolorów niestandardowych za pomocą edytora koloru rozszerzenia programu Visual Studio, wykonaj następujące kroki:  
  
1. Określ nazwy kategorii i tokenu dla nowych tokenów kolorów.  
  
2. Wybierz odcieni, używających dla każdego motywu i kolorów systemu elementu interfejsu użytkownika dla o wysokim kontraście.  
  
3. Użyj edytora koloru, aby utworzyć nowe tokeny kolorów.  
  
4. Użyj kolorów w rozszerzeniu Visual Studio.  
  
5. Przetestuj zmiany w programie Visual Studio.  
  
   **Krok 1: Określ nazwy kategorii i tokenu dla nowych tokenów kolorów.**  
  
   Preferowany nazewnictwa schemat jest VSColor **[Category] [typ interfejsu użytkownika] [Stan]**. Nie należy używać słowa "color" w nazwach VSColor, ponieważ jest nadmiarowy.  
  
   Nazwy kategorii zapewniają logiczne grupowanie i powinien być zdefiniowany jako wąskiego, jak to możliwe. Na przykład nazwa okna jednego narzędzia może być nazwa kategorii, ale nazwa całej działalności zespołu lub projektu zespołu nie jest. Grupowanie wpisy na kategorie zapobiega rozróżnienie kolory o takiej samej nazwie.  
  
   Nazwa tokenu musi wyraźnie wskazuje typ elementu i sytuacji lub "stan", dla których zostaną zastosowane kolor. Na przykład, aktywne dane Porada firmy **[UI type]** mogą być nazwane "**DataTip**" i **[Stan]** mogą być nazwane "**Active**," wynikowy w Nazwa koloru "**DataTipActive**." Ponieważ porady dotyczące danych mają tekstu, pierwszego planu i kolor tła muszą być zdefiniowane. Za pomocą powiązany tła/pierwszego planu, Edytor kolorów automatycznie utworzy kolory "**DataTipActive**" tła i "**DataTipActiveText**" planu.  
  
   Jeśli element interfejsu użytkownika ma tylko jeden stan **[Stan]** można pominąć część nazwy. Na przykład, jeśli pole wyszukiwania ma obramowanie i nie ma żadnej zmiany stanu, które będą wpływać na kolor obramowania, następnie nazwy dla tokenu kolor obramowania po prostu można wywołać "**SearchBoxBorder**."  
  
   Niektóre typowe nazwami stanów obejmują:  
  
- Aktywne  
  
- Nieaktywne  
  
- MouseOver  
  
- MouseDown  
  
- Wybrane  
  
- Fokus  
  
  Przykłady kilka nazw tokenu dla części kontrolki elementu listy:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Krok 2: Wybierz odcieni, używających dla każdego motywu i kolorów systemu elementu interfejsu użytkownika dla o wysokim kontraście.**  
  
  Podczas wybierania kolorów niestandardowych dla interfejsu użytkownika, wybierz podobne istniejącego elementu interfejsu użytkownika, a następnie użyj jej kolorów jako podstawy. Kolory dla elementów interfejsu użytkownika — wewnętrzne zostały poddane przeglądach i testowaniu, dzięki czemu będą wyglądały odpowiednie i działają prawidłowo w wszystkie motywy.  
  
  **Krok 3: Użyj edytora koloru, aby utworzyć nowe tokeny kolorów.**  
  
  Uruchom Edytor kolorów i Otwórz lub Utwórz nowy plik XML niestandardowy motyw kolorów. Wybierz **Edytuj > nowy kolor** z menu. Spowoduje to otwarcie okna dialogowego do określania kategorii i jedną lub więcej nazw dla wpisów kolorów w ramach tej kategorii:  
  
  ![Nowy kolor Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "nowy kolor Edytor kolorów VSIX")  
  
  Wybierz istniejącą kategorię lub **nową kategorię** Aby utworzyć nową kategorię. Zostanie otwarte inne okno dialogowe Tworzenie nowej nazwy kategorii:  
  
  ![Nowa kategoria Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "nowej kategorii Edytor kolorów VSIX")  
  
  Nowa kategoria stanie się dostępne w **nowy kolor** menu rozwijanego kategoria. Gdy wybierzesz kategorię, wprowadź jedną nazwę dla każdego wiersza dla każdego nowego tokenu kolor, a następnie wybierz pozycję "Utwórz", po zakończeniu:  
  
  ![Kolor nowy edytor kolorów VSIX wypełnione](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "kolor nowy edytor kolorów VSIX wypełnione")  
  
  Wartości kolorów są wyświetlane w pary tła/pierwszego planu, za pomocą "None" wskazujący, że nie został zdefiniowany kolor. Uwaga: Jeśli kolor, który nie ma pary kolor tła/kolor tekstu, tylko tła musi być zdefiniowany.  
  
  ![VSIX Color Editor Color Values](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX Color Editor Color Values")  
  
  Aby edytować token kolorów, wybierz pozycję kolor motywu (kolumna) tego tokenu. Dodaj wartość koloru, wpisując wartość szesnastkowy koloru w formacie ARGB 8-cyfrowy, wprowadzając nazwę kolorów systemowych w komórce, lub przy użyciu menu rozwijanego, aby wybrać żądany kolor przy użyciu zestawu suwaków lub Podaj listę kolorów systemowych.  
  
  ![Kolor edycji Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "kolor edycji Edytor kolorów VSIX")  
  
  ![Tło Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "tła Edytor kolorów VSIX")  
  
  Dla składników, które nie są do wyświetlania tekstu, wprowadź wartość tylko jeden kolor: kolor tła. W przeciwnym razie wprowadź wartości koloru tekstu i tła, oddzielone ukośnikiem.  
  
  Podczas wprowadzania wartości wysokiego kontrastu, wprowadź prawidłowe nazwy kolorów systemu Windows. Nie należy wprowadzać wartości ARGB zapisane na stałe. Można wyświetlić listę nazw kolorów systemu prawidłowe, wybierając pozycję "tła: System"lub" pierwszego planu: System"z menu rozwijanego wartości kolorów. Podczas tworzenia elementów, które mają składników dopisków fonetycznych, parę kolorów systemu poprawne tła/tekstu lub tekst może być niemożliwe.  
  
  Po zakończeniu tworzenia, ustawienia i edytowanie tokenów kolorów, należy je zapisać w żądanej .xml lub w formacie .pkgdef. Kolor tokenów ani na tle ani zestawu pierwszego planu będzie zapisana jako pusty kolorów w formacie XML, ale odrzucone w formacie .pkgdef. Okno dialogowe wyświetli ostrzeżenie o możliwej utracie kolor przy próbie Zapisz kolory pusty plik .pkgdef.  
  
  **Krok 4: Użyj kolorów w rozszerzeniu Visual Studio.**  
  
  Po zdefiniowaniu nowy kolor tokeny, obejmują .pkgdef w pliku projektu za pomocą "Build Action" ustawiony na "Treści" i "Uwzględnić w VSIX" wartość "True".  
  
  ![Edytor kolorów VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef Edytor kolorów VSIX")  
  
  W edytorze programu Visual Studio rozszerzenia kolorów, wybierz Plik > kolory Wyświetl kod zasobów, aby wyświetlić kod, który jest używany do uzyskiwania dostępu do niestandardowego interfejsu użytkownika opartego na WPF.  
  
  ![Podgląd kodu zasobu Edytor kolorów VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Podgląd kodu zasobu Edytor kolorów VSIX")  
  
  Uwzględnij ten kod w klasie statycznej w projekcie. Odwołanie do **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** musi zostać dodane do projektu, aby użyć **elementu ThemeResourceKey** typu.  
  
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
  
 To umożliwia dostęp do kolory w kodzie XAML i pozwala reagować na zmiany motywu interfejsu użytkownika.  
  
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
  
 **Krok 5: Przetestuj zmiany w programie Visual Studio.**  
  
 Edytor kolorów tymczasowo zastosować kolor tokenów do wystąpienia programu Visual Studio, aby wyświetlić zmiany na żywo do kolorów bez odbudowywania pakietu rozszerzenia. Aby to zrobić, kliknij przycisk "Zastosuj ten motyw do uruchomionego z okna programu Visual Studio", znajduje się w nagłówku każdej kolumny motywu. Ten tymczasowy motyw znikną po zamknięciu Edytor kolorów VSIX.  
  
 ![Edytor kolorów VSIX zastosować](../../extensibility/internals/media/vsix-color-editor-apply.png "zastosować Edytor kolorów VSIX")  
  
 Aby zmiany były trwałe, ponownie skompiluj i Wdróż ponownie rozszerzenie programu Visual Studio po dodaniu nowych kolorów do pliku .pkgdef i pisanie kodu, który będzie używać tych kolorów. Ponowne tworzenie rozszerzenia programu Visual Studio spowoduje scalenie wartości rejestru dla nowych kolorów do pozostałych tematów. Następnie uruchom ponownie program Visual Studio, wyświetlanie interfejsu użytkownika i sprawdź, czy nowe kolory są wyświetlane zgodnie z oczekiwaniami.  
  
## <a name="notes"></a>Uwagi  
 To narzędzie jest przeznaczona do użycia na potrzeby tworzenia kolorów niestandardowych dla istniejących kompozycji programu Visual Studio lub w przypadku edycji kolory niestandardowego motywu programu Visual Studio. Aby utworzyć pełną niestandardowych kompozycji programu Visual Studio, Pobierz [Edytor motywów kolorystycznych programu Visual Studio rozszerzenia](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) z galerii rozszerzeń programu Visual Studio.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 **Dane wyjściowe XML kolorów**  
  
 Plik XML generowanych przez narzędzie będzie podobny do następującego:  
  
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
  
 **Dane wyjściowe kolor PKGDEF**  
  
 Plik .pkgdef wygenerowany przez narzędzie będzie podobny do następującego:  
  
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
  
 **Otoki klucze zasobów języka C#**  
  
 Klucze zasobu kolorów, które są generowane przez narzędzie będzie podobny do następującego:  
  
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
  
 **Otoki słownika zasobów WPF**  
  
 Kolor **ResourceDictionary** klucze generowane przez narzędzie będzie podobny do następującego:  
  
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