---
title: Kolory i styl dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303156"
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio

## <a name="use-color-in-visual-studio"></a>Używanie koloru w programie Visual Studio

W programie Visual Studio kolor jest używany przede wszystkim jako narzędzie komunikacji, a nie tylko jako dekoracja. Użyj koloru minimalnie i zarezerwuj go w sytuacjach, w których chcesz:

- Komunikuj znaczenie lub przynależność (na przykład modyfikatory platformy lub języka)

- Przyciągnij uwagę (na przykład wskazując zmianę statusu)

- Popraw czytelność i zapewnij punkty orientacyjne do nawigacji po interfejsie użytkownika

- Zwiększenie celowości

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w programie Visual Studio. Czasami może być trudno dowiedzieć się, której opcji powinieneś użyć lub jak go używać poprawnie. Ten temat pomoże Ci:

- Poznaj różne usługi i systemy używane do definiowania kolorów w programie Visual Studio.

- Wybierz odpowiednią opcję dla danego elementu.

- Prawidłowo użyj wybranej opcji.

> [!NOTE]
> Nigdy nie koduj hex, RGB ani kolorów systemowych do elementów interfejsu użytkownika. Korzystanie z usług pozwala na elastyczność w dostrajaniu barwy. Ponadto bez usługi nie będzie można skorzystać z możliwości przełączania motywów [usługi VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metody przypisywania kolorów do elementów interfejsu programu Visual Studio

Wybierz metodę najlepiej dopasowanymi do elementów interfejsu użytkownika.

| Twój interfejs użytkownika | Metoda | Czym one są? |
| --- | --- | --- |
| Masz osadzone lub autonomiczne okna dialogowe. | **Kolory systemowe** | Nazwy systemów, które umożliwiają systemowi operacyjnemu definiowanie koloru i wyglądu elementów interfejsu użytkownika, takich jak typowe kontrolki okna dialogowego. |
| Masz niestandardowy interfejs użytkownika, który ma być zgodny z ogólnym środowiskiem VS i masz elementy interfejsu użytkownika, które pasują do kategorii i semantyczne znaczenie tokenów udostępnionych. | **Typowe kolory udostępnione** | Istniejące wstępnie zdefiniowane nazwy tokenów kolorów dla określonych elementów interfejsu użytkownika |
| Masz indywidualną operację lub grupę operacji i nie ma wspólnego koloru dla podobnych elementów. | **Kolory niestandardowe** | Nazwy tokenów kolorów, które są specyficzne dla obszaru i nie mają być udostępniane innym interfejsom użytkownika |
| Chcesz zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika lub zawartości (na przykład dla edytorów tekstu lub wyspecjalizowanych okien projektanta). | **Dostosowywanie użytkowników końcowych**<br /><br />**(Okno &gt; dialogowe Opcje narzędzi)** | Ustawienia zdefiniowane na stronie "Czcionki i kolory" w oknie dialogowym **Opcje narzędzi &gt; ** lub wyspecjalizowanej stronie specyficznej dla jednej funkcji interfejsu użytkownika. |

### <a name="visual-studio-themes"></a>Motywy programu Visual Studio

Program Visual Studio zawiera trzy różne motywy kolorów: jasny, ciemny i niebieski. Wykrywa również tryb wysokiego kontrastu, który jest motywem kolorów całego systemu przeznaczonym dla ułatwień dostępu.

Użytkownicy są monitowani, aby wybrać motyw podczas ich pierwszego użycia programu Visual Studio i są w stanie przełączyć motywy później, przechodząc do **Narzędzia &gt; Opcje środowiska &gt; &gt; ogólne** i wybierając nowy motyw z menu rozwijanego "motyw kolorów".

Użytkownicy mogą również użyć Panelu sterowania, aby przełączyć całe systemy na jeden z kilku motywów o wysokim kontraście. Jeśli użytkownik wybierze motyw wysokiego kontrastu, selektor motywu kolorów programu Visual Studio nie ma już wpływu na kolory w programie Visual Studio, chociaż wszelkie zmiany motywu są zapisywane, gdy użytkownik kończy działanie trybu wysokiego kontrastu. Aby uzyskać więcej informacji na temat trybu wysokiego kontrastu, zobacz [Wybieranie kolorów o wysokim kontraście](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Usługa VSColor

Visual Studio udostępnia usługę kolorów środowiska, znany jako usługa VSColor, który umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika do nazwanego wpisu zawierającego wartości kolorów dla każdego motywu programu Visual Studio. Dzięki temu kolory zostaną automatycznie zmienić, aby odzwierciedlić bieżący motyw wybrany przez użytkownika lub systemowy tryb wysokiego kontrastu. Korzystanie z usługi oznacza, że implementacja wszystkich zmian kolorów związanych z motywem jest obsługiwana w jednym miejscu, a jeśli używasz wspólnych kolorów udostępnionych z usługi, interfejs użytkownika automatycznie będzie odzwierciedlać nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="implementation"></a>Wdrażanie

Kod źródłowy programu Visual Studio zawiera kilka plików definicji pakietu, które zawierają listy nazw tokenów i odpowiednie wartości kolorów dla każdego motywu. Usługa kolorów odczytuje VSColors zdefiniowane w tych plikach definicji pakietu. Te kolory są przywoływane w znacznikach XAML `IVsUIShell5.GetThemedColor` lub w kodzie, a następnie ładowane za pośrednictwem metody lub mapowania DynamicResource.

### <a name="system-colors"></a>Kolory systemowe

Typowe formanty domyślnie odwołują się do kolorów systemowych. Jeśli chcesz, aby interfejs użytkownika używał kolorów systemowych, na przykład podczas tworzenia osadzonego lub autonomicznego okna dialogowego, nie musisz nic robić.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Typowe kolory udostępnione w usłudze VSColor

Elementy interfejsu powinny odzwierciedlać ogólne środowisko programu Visual Studio. Korzystając ponownie z typowych kolorów udostępnionych, które są odpowiednie dla składnika interfejsu użytkownika, który projektujesz, upewnij się, że interfejs jest zgodny z innymi interfejsami programu Visual Studio i że kolory będą aktualizowane automatycznie po dodaniu lub zaktualizowaniu motywów.

Przed użyciem typowych kolorów udostępnionych upewnij się, że rozumiesz, jak używać ich poprawnie. Nieprawidłowe użycie typowych kolorów udostępnionych może spowodować niespójne, frustrujące lub mylące środowisko dla użytkowników.

### <a name="user-customizable-colors"></a>Kolory, które można dostosować do potrzeb użytkownika

Zobacz: [Udostępnianie kolorów użytkownikom końcowym](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami należy zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektu. Konfigurowalne składniki interfejsu użytkownika znajdują się w sekcji **Czcionki i kolory** w oknie dialogowym **Opcje narzędzi, &gt; ** w którym użytkownicy mogą zmienić kolor pierwszego planu, kolor tła lub oba te elementy.

![Okno &gt; dialogowe Opcje narzędzi](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Okno &gt; dialogowe Opcje narzędzi

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Usługa VSColor

Visual Studio udostępnia usługę kolorów środowiska, zwaną również usługą VSColor lub usługą kolorów powłoki. Ta usługa umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika z zestawem kolorów nazwa-wartość zawierającym kolory dla każdego motywu. Usługa VSColor musi być używana dla wszystkich elementów interfejsu użytkownika, tak aby kolory automatycznie zmieniać, aby odzwierciedlić bieżący motyw wybrany przez użytkownika i tak, aby interfejs użytkownika powiązany z usługą kolorów środowiska integruje się z nowymi motywami w przyszłych wersjach programu Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa

Usługa kolorów środowiska odczytuje VSColors zdefiniowane w pkgdef dla składnika interfejsu użytkownika. Te VSColors są następnie odwołuje się w znacznikach XAML `IVsUIShell5.GetThemedColor` lub `DynamicResource` kodu i są ładowane za pośrednictwem lub mapowania.

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

Istnieje kilka różnych sposobów dostępu do usługi VSColor, w zależności od rodzaju tokenów kolorów, których używasz i jaki rodzaj kodu masz.

#### <a name="predefined-environment-colors"></a>Wstępnie zdefiniowane kolory środowiska

##### <a name="from-native-code"></a>Z kodu macierzystego

Powłoka zapewnia usługę, która `COLORREF` daje dostęp do kolorów. Usługa/interfejs to:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80.idl wyliczenie `__VSSYSCOLOREX` ma stałe kolorów powłoki. Aby go użyć, przekaż jako wartość indeksu jedną `enum __VSSYSCOLOREX` z wartości z udokumentowanej w MSDN lub `GetSysColor`zwykły numer indeksu akceptowany przez systemowy interfejs API systemu Windows. W ten sposób pobiera z powrotem wartość RGB koloru, który powinien być używany w drugim parametrze.

W przypadku przechowywania pióra lub pędzla `AdviseBroadcastMessages` z nowym kolorem, należy `WM_SYSCOLORCHANGE` (poza powłoki programu Visual Studio) i nasłuchiwać i `WM_THEMECHANGED` wiadomości.

Aby uzyskać dostęp do usługi kolorów w kodzie macierzystym, nawiążesz wywołanie podobne do następującego:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Wartości `COLORREF` zwracane `GetVSSysColorEx()` zawierają tylko składniki R, G,B koloru motywu. Jeśli wpis motywu używa przezroczystości, wartość kanału alfa jest odrzucana przed zwróceniem. W związku z tym jeśli kolor środowiska zainteresowania musi być używany w miejscu, gdzie kanał przezroczystości jest ważne, należy użyć `IVsUIShell5.GetThemedColor` zamiast `IVsUIShell2::GetVSSysColorEx`, jak opisano w dalszej części tego tematu.

##### <a name="from-managed-code"></a>Z kodu zarządzanego

Uzyskiwanie dostępu do usługi VSColor za pośrednictwem kodu macierzystego jest dość proste. Jeśli pracujesz za pomocą kodu zarządzanego, jednak określenie sposobu korzystania z usługi może być trudne. Mając to na uwadze, oto fragment kodu języka C# demonstrujący ten proces:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Jeśli pracujesz w języku Visual Basic, użyj:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Od interfejsu użytkownika WPF

Można powiązać z kolorami programu Visual Studio `ResourceDictionary`za pomocą wartości eksportowanych do aplikacji . Poniżej znajduje się przykład przy użyciu zasobów z tabeli kolorów, a także powiązania z danymi czcionki środowiska w języku XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Klasy pomocnicze i metody kodu zarządzanego

W przypadku kodu zarządzanego biblioteka struktury`Microsoft.VisualStudio.Shell.12.0.dll`zarządzanego pakietu ( ) zawiera kilka klas pomocniczych ułatwiających korzystanie z kolorów tematycznych.

Metody pomocnika w `Microsoft.VisualStudio.Shell.VsColors` klasie w MPF obejmują `GetThemedGDIColor()` i `GetThemedWPFColor()`. Te metody pomocnika zwracają wartość koloru wpisu motywu jako `System.Drawing.Color` lub `System.Windows.Media.Color`, które mają być używane w WinForms lub WPF UI.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Klasa może również służyć do uzyskania identyfikatorów VSCOLOR dla danego klucza zasobów barwy WPF lub odwrotnie.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody klasy `VsColors` kwerendy usługi VSColor do zwracania wartości koloru za każdym razem, gdy są wywoływane. Aby uzyskać wartość `System.Drawing.Color`koloru jako , alternatywą o lepszej wydajności `Microsoft.VisualStudio.PlatformUI.VSThemeColor` jest zamiast tego użyć metod klasy, która buforuje wartości kolorów uzyskane z usługi VSColor. Klasa subskrybuje wewnętrznie do emisji powłoki wiadomości zdarzeń i odrzuca wartość buforowaną, gdy występuje zdarzenie zmiany motywu. Ponadto klasa zapewnia . Wydarzenie przyjazne net, aby subskrybować zmiany motywu. Użyj `ThemeChanged` zdarzenia, aby dodać nowy program `GetThemedColor()` obsługi i użyć `ThemeResourceKeys` metody, aby uzyskać wartości kolorów dla zainteresowania. Przykładowy kod może wyglądać następująco:

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Wybieranie kolorów o wysokim kontraście

### <a name="overview"></a>Omówienie

System Windows używa kilku motywów na poziomie systemu o wysokim kontraście, które zwiększają kontrast kolorów tekstu, tła i obrazów, dzięki czemu elementy są bardziej wyraźne na ekranie. Ze względu na dostępność ważne jest, aby elementy interfejsu programu Visual Studio reagowały poprawnie, gdy użytkownicy przełączają się na motyw wysokiego kontrastu.

Tylko kilka kolorów systemowych może być używany do motywów o wysokim kontraście. Wybierając nazwy kolorów systemu, należy pamiętać o następujących wskazówkach:

- **Wybierz kolory systemowe, które mają takie samo znaczenie semantyczne** jak kolorowanie elementu. Na przykład, jeśli wybierasz kolor o wysokim kontraście dla tekstu w oknie, użyj WindowText, a nie ControlText.

- **Wybierz pary pierwszego planu/tła** razem lub nie będziesz mieć pewności, że wybór koloru będzie działał we wszystkich motywach o wysokim kontraście.

- **Określ, które części interfejsu użytkownika są najważniejsze i upewnij się, że obszary zawartości będą się wyróżniać.** Stracisz wiele szczegółów, które subtelne różnice w odcieniu kolorów normalnie odróżniają, więc użycie silnych kolorów obramowania jest powszechne w definiowaniu obszarów zawartości, ponieważ nie ma wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Zestaw kolorów systemowych

Tabela w [WPF Team Blog: SystemColors Reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) wskazuje pełny zestaw nazw kolorów systemu i odpowiednie odcienie wyświetlane w każdym motywie.

Stosując ten ograniczony zestaw kolorów do interfejsu użytkownika, *oczekuje się, że stracisz subtelne szczegóły, które były obecne w "normalnych" tematów*. Oto przykład interfejsu użytkownika z subtelnymi kolorami szarymi, które są używane do rozróżniania obszarów w oknie narzędzia. Po sparowaniu z tym samym oknem wyświetlanym w trybie wysokiego kontrastu widać, że wszystkie tła mają ten sam odcień, a obramowania tych obszarów są wskazywane tylko przez obramowanie:

![Przykład utraty subtelnych szczegółów w ysuwu](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Przykład utraty subtelnych szczegółów w ysuwu

#### <a name="choosing-text-colors-in-an-editor"></a>Wybieranie kolorów tekstu w edytorze

Kolorowano tekst jest używany w edytorze lub na powierzchni projektowej w celu wskazania znaczenia, na przykład umożliwiającej łatwą identyfikację grup podobnych elementów. W motywie Wysoki kontrast nie masz jednak możliwości rozróżniania więcej niż trzech kolorów tekstu. WindowText, GrayText i HotTrackText są jedynymi kolorami dostępnymi na powierzchniach WindowBackground. Ponieważ nie można użyć więcej niż trzech kolorów, starannie wybierz najważniejsze różnice, które mają być wyświetlane w trybie wysokiego kontrastu.

Barwy dla każdej nazwy tokenu dozwolone na powierzchni edytora, ponieważ pojawiają się w każdym motywie wysokiego kontrastu:

![Porównanie edytora o wysokim kontraście](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Porównanie edytora o wysokim kontraście

Przykłady powierzchni edytora w niebieskim motywie:

![Edytor w niebieskim kompozycji](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Edytor w niebieskim kompozycji

![Edytor kompozycji #1 o wysokim kontraście](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Edytor kompozycji #1 o wysokim kontraście

### <a name="usage-patterns"></a>Wzorce użycia

Wiele typowych elementów interfejsu użytkownika ma już zdefiniowane kolory o wysokim kontraście. Można odwoływać się do tych wzorców użycia przy wyborze własnych nazw kolorów systemu, dzięki czemu elementy interfejsu użytkownika są zgodne z podobnymi składnikami.

| Kolor systemu | Sposób użycia |
| --- | --- |
| ActiveCaption (ActiveCaption) | - Aktywny IDE i rafted glify przycisk okna na hover i naciśnij<br />- Tło paska tytułu dla IDE i rafted windows<br />- Domyślne tło paska stanu |
| Tekst ActiveCaption | - Aktywny IDE i rafted okna na pierwszym planie paska tytułu (tekst i glify)<br />- Tło i obramowanie aktywnych przycisków okien po najechaniu i naciśnięciu przycisku |
| Kontrola | - Pole kombi, lista rozwijana i kontrola wyszukiwania domyślne i wyłączone tło, w tym przycisk rozwijany<br />- Tło przycisku docelowego dokowania<br />- Tło paska poleceń<br />- Tło okna narzędzia |
| ControlDark ( ControlDark ) | - Tło IDE<br />- Separatory menu i paska poleceń<br />- Obramowanie paska poleceń<br />- Cienie menu<br />- Domyślna zakładka okna narzędzia i najedź na obramowanie i separator<br />- Dokument dobrze przepełnienie tło przycisku<br />- Dock granicy glif cel |
| ControlDarkdark (1000) |- Nieskoncentrowane, wybrane okno karty dokumentu |
| Światło kontrolne |- Automatyczne ukrywanie obramowania karty<br />- Pole kombi i lista rozwijana obramowanie<br />- Dock cel tła i granicy |
| ControlLightLight (Światło sterowania) | - Wybrana, skupiona granica tymczasowa |
| Tekst control | - Pole kombi i glif listy rozwijanej<br />- Okno narzędzia niezaznaczony tekst karty |
| Tekst szary |- Pole kombi i lista rozwijana wyłączone obramowanie, glif listy rozwijanej, tekst i tekst elementu menu<br />- Wyłączony tekst menu<br />- Kontrola wyszukiwania "opcje wyszukiwania" tekst nagłówka<br />- Separator sekcji sterowania wyszukiwaniem |
| Wyróżnij | - Wszystkie najechać i naciskać tła i obramowania, z wyjątkiem pola kombi rozwijanego tła przycisku i dokumentu dobrze przepełnienie krawędzi przycisku<br />- Wybrane tła elementów |
| Tekst wyróżnienia | - Wszystkie hover i wciśnięty pierwszy plan (tekst i glify)<br />- Poleczone okno narzędzia i kontrolka okna karty dokumentu na pierwszym planie<br />- Obramowanie paska paska okna narzędzia<br />- Skoncentrowany, wybrany tymczasowy zakładka na pierwszym planie<br />- Dokument dobrze przepełnienie krawędzi przycisku po najechaniu i naciśnij<br />- Wybrane obramowanie ikony|
| HotTrack (HotTrack) | - Przewijanie kciuka tła i obramowania na prasie<br />- Przewijanie glif strzałki na prasie |
| NieaktywnyCaption | - Nieaktywne IDE i rafted glify przycisk okna na hover<br />- Tło paska tytułu dla IDE i rafted windows<br />- Wyłączone tło kontroli wyszukiwania |
| Tekst nieaktywny w celu | - Nieaktywny IDE i rafted windows tytuł pasek pierwszego planu (tekst i glify)<br />- Nieaktywne przyciski okna tło i obramowanie po najechaniu na nie<br />- Nieskoncentrowane tło przycisku okna narzędzia i obramowanie<br />- Wyłączone formancie wyszukiwania na pierwszym planie |
| Menu | - Rozwijane tło menu<br />- Sprawdzone i wyłączone zaznaczyć tło |
| MenuTekst | - Rozwijane obramowanie menu<br />- Sprawdź znaczniki<br />- Glify menu<br />- Tekst menu rozwijanego<br />- Wybrane obramowanie ikony |
| Scrollbar | - Pasek przewijania i tło strzałki paska przewijania, wszystkie stany |
| Okno | - Automatyczne ukrywanie tła karty<br />- Pasek menu i tło półki poleceń<br />- Nieskoncentrowane lub niezaznaczone tło karty okna dokumentu i obramowanie dokumentu, zarówno dla otwartych, jak i tymczasowych kart<br />- Nieskoncentrowane tło paska tytułu okna narzędzia<br />- Tło karty okna narzędzia, zarówno zaznaczone, jak i niezaznaczone |
| WindowFrame (Ramka okna) | - Granica IDE |
| WindowText (Tekst okna) | - Automatyczne ukrywanie karty na pierwszym planie<br />- Wybrana karta okna narzędzia na pierwszym planie<br />- Nieostry kartę okna dokumentu i nieskoncentrowane lub niezaznaczone tymczasowe zakładka pierwszego planu<br />- Domyślny pierwszy plan widoku drzewa i najedź kursorem na niezaznaczony glif<br />- Okno narzędzia wybrane obramowanie karty<br />- Tło kciuka paska przewijania, obramowanie i glif |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Udostępnianie kolorów użytkownikom końcowym

### <a name="overview"></a>Omówienie

Czasami należy zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektu. Najczęstszym sposobem, aby to zrobić, jest użycie okna dialogowego **Opcje narzędzi. &gt; ** Jeśli nie masz wysoce wyspecjalizowanego interfejsu użytkownika, który wymaga specjalnych formantów, najprostszym sposobem przedstawienia dostosowania jest za pośrednictwem **czcionki i kolory** strony w **środowisku** sekcji okna dialogowego. Dla każdego elementu, który można udostępnić do dostosowania, użytkownik może wybrać, aby zmienić kolor pierwszego planu, kolor tła lub obu.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie vspackage dla konfigurowalnych kolorów

VsPackage może kontrolować czcionki i kolory za pomocą niestandardowych kategorii i wyświetlać elementy na stronie właściwości Czcionki i kolory. Korzystając z tego mechanizmu, VSPackages musi implementować [interfejs IVsFontAndColorColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) i skojarzone z nim interfejsy.

Zasadniczo ten mechanizm może służyć do modyfikowania wszystkich istniejących elementów wyświetlania i kategorii, które je zawierają. Jednak nie należy go używać do modyfikowania kategorii Edytor tekstu lub jej elementów wyświetlanych. Aby uzyskać więcej informacji na temat kategorii Edytor tekstu, zobacz [Omówienie czcionek i kolorów](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Aby zaimplementować niestandardowe kategorie lub wyświetlić elementy, vspackage musi:

- **Tworzenie lub identyfikowanie kategorii w rejestrze.** Implementacja IDE **fonts i kolory** strony właściwości strony używa tych informacji, aby poprawnie kwerendy dla usługi obsługującej danej kategorii.

- **Tworzenie lub identyfikowanie grup w rejestrze (opcjonalnie).** Może być przydatne do zdefiniowania grupy, która reprezentuje związek dwóch lub więcej kategorii. Jeśli grupa jest zdefiniowana, IDE automatycznie scala podkategorie i dystrybuuje elementy wyświetlania w grupie.

- **Implementowanie obsługi IDE.**

- **Obsługa zmian czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub zidentyfikować kategorie

Skonstruuj specjalny typ `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` wpisu rejestru kategorii w miejscu, w którym `<Category>` jest niezlokalizowana nazwa kategorii.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi VSPackage obsługujący tę kategorię |

 Usługa określona w rejestrze musi zapewnić implementację [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) dla odpowiedniej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub zidentyfikować grupy

Skonstruuj specjalny typ `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` wpisu rejestru kategorii w miejscu, w którym `<group>` jest niezlokalizowana nazwa grupy.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi VSPackage obsługujący tę kategorię |

Usługa określona w rejestrze musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> zapewnić implementację dla odpowiedniej grupy.

![Wdrożenie IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Wdrożenie`IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Aby zaimplementować obsługę IDE

Implementuj [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), który zwraca interfejs [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs do IDE dla każdej kategorii lub grupy GUID dostarczone.

Dla każdej kategorii, która obsługuje, VSPackage implementuje oddzielne wystąpienie interfejsu [IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Metody zaimplementowane za pośrednictwem [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) musi zapewnić IDE z:

- Listy elementów wyświetlanych w kategorii

- Nazwy zlokalizowane dla elementów wyświetlanych

- Wyświetlanie informacji dla każdego członka kategorii

> [!NOTE]
> Każda kategoria musi zawierać co najmniej jeden element wyświetlania.

IDE używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu do definiowania unii kilku kategorii.

Jego implementacja zapewnia IDE z:

- Lista kategorii, które składają się na daną grupę

- Dostęp do wystąpień [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) obsługujących każdą kategorię w grupie

- Nazwy grup, które można zlokalizować

#### <a name="updating-the-ide"></a>Aktualizowanie ide

IDE buforuje informacje o ustawieniach czcionki i koloru. W związku z tym po każdej modyfikacji konfiguracji czcionki IDE i kolor, zapewnienie, że pamięć podręczna jest aktualna jest najlepszym rozwiązaniem.

Aktualizowanie pamięci podręcznej odbywa się za pośrednictwem interfejsu [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) i może być wykonywane globalnie lub tylko na wybranych elementach.

### <a name="handling-font-and-color-changes"></a>Obsługa zmian czcionek i kolorów

Aby poprawnie obsługiwać kolorowanie tekstu wyświetlanego przez program VSPackage, usługa kolorowania obsługująca program VSPackage musi odpowiadać na zmiany inicjowane przez użytkownika wprowadzone za pośrednictwem strony właściwości Czcionki i kolory.

Aby to zrobić, VSPackage musi:

- **obsługi zdarzeń generowanych** przez IDE implementując [interfejs IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) IDE wywołuje odpowiednią metodę po modyfikacji użytkownika fonts i kolory strony. Na przykład wywołuje [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metody, jeśli nowa czcionka jest zaznaczona.

  **Lub**

- **sondowania IDE pod kątem zmian**. Można to zrobić za pośrednictwem zaimplementowanego przez system interfejsu [IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) Chociaż przede wszystkim dla obsługi trwałości [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metoda można uzyskać informacje o czcionki i koloru dla elementów wyświetlanych. Aby uzyskać więcej informacji na temat ustawień czcionek i kolorów, zobacz artykuł MSDN [Uzyskiwanie dostępu do ustawień zapisanych czcionek i kolorów](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Aby upewnić się, że wyniki sondowania są poprawne, należy użyć interfejsu [IVsFontAndColorCacheManager,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) aby ustalić, czy opróżnianie pamięci podręcznej i aktualizacji są potrzebne przed wywołaniem metod pobierania interfejsu [IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie czcionek niestandardowych i kategorii kolorów bez implementacji interfejsów

W poniższym przykładzie kodu pokazano, jak zarejestrować niestandardową czcionkę i kategorię kolorów bez implementowania interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

W tym przykładzie kodu:

- `"NameID"`= identyfikator zasobu zlokalizowanej nazwy kategorii w pakiecie
- `"ToolWindowPackage"`= Identyfikator GUID pakietu
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`jest tylko przykładem, a rzeczywistą wartością może być nowy identyfikator GUID dostarczony przez realizatora.

### <a name="set-the-font-and-color-property-category-guid"></a>Ustawianie identyfikatora GUID właściwości Czcionka i Kolor

Poniższy przykład kodu pokazuje ustawienie identyfikatorów GUID kategorii.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
