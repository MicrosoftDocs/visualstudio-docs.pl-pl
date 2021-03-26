---
title: Kolory i style dla programu Visual Studio | Microsoft Docs
description: Dowiedz się, w jaki sposób środowisko użytkownika programu Visual Studio używa kolorów jako narzędzia komunikacyjnego, a nie w celu uzyskania przejrzystych powodów.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc98e3c2717b14ac1933e5b41269af1efb8e932f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089917"
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio

## <a name="use-color-in-visual-studio"></a>Użyj koloru w programie Visual Studio

W programie Visual Studio kolor jest używany głównie jako narzędzie komunikacyjne, a nie tylko dekoracja. Użyj kolorowo jako minimum i Zarezerwuj go w sytuacjach, gdy chcesz:

- Przekazywanie informacji o znaczeniu lub przynależności (na przykład w przypadku modyfikatorów platformy lub języka)

- Zwrócenie uwagi (na przykład wskazującej zmianę stanu)

- Zwiększ czytelność i podaj dzielnice na potrzeby nawigowania po interfejsie użytkownika

- Zwiększ pragnienie

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w programie Visual Studio. Czasami trudno jest ustalić, której opcji używać, lub jak używać jej poprawnie. Ten temat pomoże Ci:

- Zapoznaj się z różnymi usługami i systemami używanymi do definiowania kolorów w programie Visual Studio.

- Wybierz poprawną opcję dla danego elementu.

- Prawidłowo Użyj wybranej opcji.

> [!NOTE]
> Nigdy nie umieszczaj kolorów szesnastkowych, RGB ani systemowych do elementów interfejsu użytkownika. Korzystanie z usług pozwala na elastyczność dostrajania barwy. Ponadto bez usługi nie będzie można korzystać z możliwości przełączania motywu [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metody przypisywania kolorów do elementów interfejsu programu Visual Studio

Wybierz metodę najlepiej dopasowaną do elementów interfejsu użytkownika.

| Interfejs użytkownika | Metoda | Jakie? |
| --- | --- | --- |
| Masz osadzone lub autonomiczne okna dialogowe. | **Kolory systemowe** | Nazwy systemu, które umożliwiają systemowi operacyjnemu Definiowanie koloru i wyglądu elementów interfejsu użytkownika, takich jak wspólne kontrolki okna dialogowego. |
| Istnieje niestandardowy interfejs użytkownika, który ma być spójny z ogólnym środowiskiem programu VS i masz elementy interfejsu użytkownika zgodne z kategorią i semantyką znaczenia tokenów udostępnionych. | **Wspólne kolory udostępnione** | Istniejące wstępnie zdefiniowane nazwy tokenów kolorów dla określonych elementów interfejsu użytkownika |
| Użytkownik ma konkretną funkcję lub grupę funkcji i nie ma udostępnionego koloru dla podobnych elementów. | **Kolory niestandardowe** | Nazwy tokenów kolorów, które są specyficzne dla obszaru i nie powinny być współużytkowane z innymi interfejsami użytkownika |
| Chcesz zezwolić użytkownikowi końcowemu na Dostosowywanie interfejsu użytkownika lub zawartości (na przykład w przypadku edytorów tekstu lub wyspecjalizowanych okien projektanta). | **Dostosowywanie użytkownika końcowego**<br /><br />**(Narzędzia &gt; Okno dialogowe opcji)** | Ustawienia zdefiniowane na stronie "czcionki i kolory" okna dialogowego **&gt; Opcje narzędzi** lub wyspecjalizowanej stronie specyficzne dla jednej funkcji interfejsu użytkownika. |

### <a name="visual-studio-themes"></a>Motywy programu Visual Studio

Program Visual Studio oferuje trzy różne motywy kolorów: jasne, ciemne i niebieskie. Wykrywa również tryb duży kontrast, który jest motywem kolorów w całym systemie zaprojektowanym pod kątem ułatwień dostępu.

Użytkownicy są monitowani o wybranie motywu podczas pierwszego korzystania z programu Visual Studio i mogą przełączać motywy później, przechodząc **do &gt; opcji &gt; narzędzia &gt; Ogólne** i wybierając nowy motyw z menu rozwijanego "motyw kolorów".

Użytkownicy mogą również używać panelu sterowania do przełączania całego systemu do jednego z kilku duży kontrast motywy. Jeśli użytkownik wybierze motyw duży kontrast, selektor motywu kolorów programu Visual Studio nie będzie miał już wpływu na kolory w programie Visual Studio, ale wszystkie zmiany motywu są zapisywane dla momentu zakończenia trybu duży kontrast przez użytkownika. Aby uzyskać więcej informacji o trybie duży kontrast, zobacz [wybieranie duży kontrast kolory](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Usługa VSColor

Program Visual Studio udostępnia usługę kolory środowiska, znaną jako usługa VSColor, która umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika z nazwanym wpisem zawierającym wartości koloru dla każdego motywu programu Visual Studio. Gwarantuje to, że kolory zostaną automatycznie zmienione w celu odzwierciedlenia bieżącego motywu wybranego przez użytkownika lub trybu duży kontrast systemu. Korzystanie z usługi oznacza, że implementacja wszystkich zmian kolorów związanych z motywem jest obsługiwana w jednym miejscu, a jeśli używasz wspólnych kolorów udostępnionych z usługi, interfejs użytkownika automatycznie odzwierciedla nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="implementation"></a>Implementacja

Kod źródłowy programu Visual Studio zawiera kilka plików definicji pakietów, które zawierają listy nazw tokenów i odpowiednie wartości koloru dla każdego motywu. Usługa Color odczytuje VSColors zdefiniowane w tych plikach definicji pakietu. Te kolory są przywoływane w znacznikach XAML lub w kodzie, a następnie ładowane za pomocą `IVsUIShell5.GetThemedColor` metody lub mapowania DynamicResource —.

### <a name="system-colors"></a>Kolory systemowe

Formanty wspólne domyślnie przywołują kolory systemowe. Jeśli chcesz, aby interfejs użytkownika używał kolorów systemowych, takich jak podczas tworzenia okna dialogowego osadzone lub autonomiczne, nie musisz nic robić.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Wspólne kolory udostępnione w usłudze VSColor

Elementy interfejsu powinny odzwierciedlać ogólne środowisko programu Visual Studio. Korzystając z tych wspólnych kolorów, które są odpowiednie dla projektowanego składnika interfejsu użytkownika, należy się upewnić, że interfejs jest zgodny z innymi interfejsami programu Visual Studio i że kolory będą aktualizowane automatycznie po dodaniu lub zaktualizowaniu motywów.

Przed użyciem wspólnych udostępnionych kolorów upewnij się, że rozumiesz, jak z nich korzystać. Nieprawidłowe użycie wspólnych udostępnionych kolorów może spowodować niespójne, frustrujące lub mylące środowisko dla użytkowników.

### <a name="user-customizable-colors"></a>Kolory dostosowywane przez użytkownika

Zobacz: [Uwidacznianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami trzeba zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Dostosowywalne składniki interfejsu użytkownika znajdują się w sekcji **czcionki i kolory** okna dialogowego **&gt; Opcje narzędzi** , w którym użytkownicy mogą wybrać zmianę koloru pierwszego planu, koloru tła lub obu tych funkcji.

![&gt;Okno dialogowe Opcje narzędzi](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 — a_ToolsOptionsDialog")<br />&gt;Okno dialogowe Opcje narzędzi

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Usługa VSColor

Program Visual Studio udostępnia usługę kolory środowiska, nazywaną również usługą VSColor lub usługą Color Shell. Ta usługa umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika z zestawem kolorów wartości nazwanych zawierającymi kolory dla każdego motywu. Usługa VSColor musi być używana dla wszystkich elementów interfejsu użytkownika, dzięki czemu kolory automatycznie zmieniają się w celu odzwierciedlenia bieżącego motywu wybranego przez użytkownika, a więc interfejs użytkownika powiązany z usługą kolorów środowiska zostanie zintegrowany z nowymi motywami w przyszłych wersjach programu Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa

Usługa kolor środowiska odczytuje VSColors zdefiniowane w. pkgdef dla składnika interfejsu użytkownika. Te VSColors są następnie odwoływane w znacznikach XAML lub kodzie i są ładowane przy użyciu `IVsUIShell5.GetThemedColor` albo `DynamicResource` mapowania.

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 — a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

Istnieje kilka różnych sposobów uzyskiwania dostępu do usługi VSColor, w zależności od rodzaju tokenów kolorów, z których korzystasz, oraz rodzaju kodu.

#### <a name="predefined-environment-colors"></a>Wstępnie zdefiniowane kolory środowiska

##### <a name="from-native-code"></a>Z kodu natywnego

Powłoka udostępnia usługę zapewniającą dostęp do `COLORREF` kolorów. Usługa/interfejs:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80. idl Wyliczenie `__VSSYSCOLOREX` ma stałe koloru powłoki. Aby go użyć, należy przekazać jako wartość indeksu jedną z wartości z `enum __VSSYSCOLOREX` witryny MSDN lub zwykłym indeksem, który jest akceptowany przez interfejs API systemu Windows `GetSysColor` . Spowoduje to przywrócenie wartości RGB koloru, który ma być używany w drugim parametrze.

W przypadku przechowywania pióra lub pędzla z nowym kolorem należy `AdviseBroadcastMessages` (wyłączyć powłokę programu Visual Studio) i słuchać `WM_SYSCOLORCHANGE` komunikatów i `WM_THEMECHANGED` .

Aby uzyskać dostęp do usługi Color w kodzie natywnym, należy wywołać wywołanie podobne do poniższego:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF`Wartości zwracane przez `GetVSSysColorEx()` zawierają tylko składniki R, G, B koloru motywu. Jeśli wpis motywu używa przezroczystości, wartość kanału alfa zostanie odrzucona przed zwróceniem. W związku z tym, jeśli wymagany jest kolor środowiska zainteresowania w miejscu, w którym jest ważne, należy użyć `IVsUIShell5.GetThemedColor` zamiast `IVsUIShell2::GetVSSysColorEx` , zgodnie z opisem w dalszej części tego tematu.

##### <a name="from-managed-code"></a>Z kodu zarządzanego

Uzyskiwanie dostępu do usługi VSColor za pomocą kodu natywnego jest dość proste. W przypadku korzystania z kodu zarządzanego można jednak określić, jak korzystać z usługi. Z tego względu Oto fragment kodu w języku C# pokazujący ten proces:

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

Jeśli pracujesz w Visual Basic, użyj:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Z interfejsu użytkownika WPF

Można powiązać z kolorami programu Visual Studio za pomocą wartości wyeksportowanych do aplikacji `ResourceDictionary` . Poniżej znajduje się przykład użycia zasobów z tabeli kolorów, a także powiązania z danymi czcionki środowiska w języku XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Klasy pomocnika i metody dla kodu zarządzanego

W przypadku kodu zarządzanego, biblioteka struktury pakietu zarządzanego powłoki ( `Microsoft.VisualStudio.Shell.12.0.dll` ) zawiera kilka klas pomocnika, które ułatwiają korzystanie z nich.

Metody pomocnika w `Microsoft.VisualStudio.Shell.VsColors` klasie w MPF obejmują `GetThemedGDIColor()` i `GetThemedWPFColor()` . Te metody pomocnika zwracają wartość koloru wpisu motywu jako `System.Drawing.Color` lub `System.Windows.Media.Color` , które mają być użyte w interfejsie WinForms lub interfejsu użytkownika WPF.

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

Klasy można również użyć do uzyskania identyfikatorów VSCOLOR dla danego klucza zasobu koloru WPF lub na odwrót.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody `VsColors` klasy kwerendy usługi VSColor, aby zwracały wartość koloru przy każdym wywołaniu. Aby uzyskać wartość koloru jako `System.Drawing.Color` alternatywę dla lepszej wydajności, należy zamiast tego użyć metod `Microsoft.VisualStudio.PlatformUI.VSThemeColor` klasy, w których są buforowane wartości kolorów uzyskane z usługi VSColor. Klasa subskrybuje wewnętrznie zdarzenia rozgłaszania komunikatów i odrzuca buforowaną wartość, gdy wystąpi zdarzenie zmiany motywu. Ponadto Klasa zawiera. Zdarzenie przyjazne dla sieci, aby subskrybować zmiany motywu. Użyj `ThemeChanged` zdarzenia, aby dodać nowy program obsługi, i Użyj `GetThemedColor()` metody, aby uzyskać wartości koloru dla `ThemeResourceKeys` zainteresowania. Przykładowy kod może wyglądać następująco:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Wybieranie duży kontrast kolorów

### <a name="overview"></a>Omówienie

W systemie Windows są używane różne kompozycje na poziomie systemu, które zwiększają kontrast koloru tekstu, tła i obrazów, co sprawia, że elementy pojawiają się bardziej odrębnie na ekranie. Ze względów ułatwień dostępu ważne jest, aby elementy interfejsu programu Visual Studio odpowiadały prawidłowym, gdy użytkownicy przełączają się do motywu duży kontrast.

Do duży kontrast motywów można używać tylko kilku kolorów systemowych. Po wybraniu nazw kolorów systemu należy pamiętać o następujących wskazówkach:

- **Wybierz kolory systemowe, które mają taką samą semantykę** jak element, który jest kolorem. Na przykład jeśli wybierzesz kolor o dużym kontraście dla tekstu w oknie, użyj WindowText, a nie ControlText.

- **Wybieraj jednocześnie pary pierwszego planu/tła** lub nie masz pewności, że wybór kolorów będzie działać we wszystkich motywach duży kontrast.

- **Ustal, które części interfejsu użytkownika są najważniejsze i upewnij się, że obszary zawartości zostaną** wystawione. Utracisz dużo szczegółów, dzięki czemu delikatne różnice w odcienie odnoszą się zwykle, dlatego w celu zdefiniowania obszarów zawartości często używane są kolory silnego obramowania, ponieważ nie ma żadnych wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Zestaw kolorów systemu

Tabela na [blogu zespołu WPF: SystemColors Reference](/archive/blogs/wpf/systemcolors-reference) wskazuje pełny zestaw nazw kolorów systemowych i odpowiadający odcieni wyświetlany w każdym motywie.

W przypadku zastosowania tego ograniczonego zestawu kolorów do interfejsu użytkownika należy się *spodziewać, że utracisz delikatne szczegóły, które były obecne w motywach "normal"*. Oto przykład interfejsu użytkownika z delikatnymi kolorami szarymi, które są używane do rozróżniania obszarów w oknie narzędzi. W przypadku sparowania z tym samym oknem wyświetlanym w trybie duży kontrast można zobaczyć, że wszystkie tła są takie same, a obramowanie tych obszarów jest wskazywane wyłącznie przez obramowanie:

![Przykład, w jaki sposób subtelne szczegóły są tracone w duży kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 — a_PropertiesWindow")<br />Przykład, w jaki sposób subtelne szczegóły są tracone w duży kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Wybieranie kolorów tekstu w edytorze

Tekst z kolorami jest używany w edytorze lub na powierzchni projektowej w celu wskazania znaczenia, takich jak umożliwienie łatwej identyfikacji grup podobnych elementów. W motywie duży kontrast nie ma jednak możliwości rozróżniania między więcej niż trzema kolorami tekstu. WindowText, GrayText i HotTrackText są jedynymi kolorami dostępnymi na powierzchniach WindowBackground. Ponieważ nie można użyć więcej niż trzech kolorów, należy uważnie wybrać najważniejsze różnice, które mają być wyświetlane w trybie duży kontrast.

Odcieni dla każdego z nazw tokenów dozwolonych na powierzchni edytora, tak jak pojawiają się one w każdym duży kontrast motywie:

![Porównanie edytora duży kontrast](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 — b_HCEditorComparison")<br />Porównanie edytora duży kontrast

Przykłady powierzchni edytora w niebieskim motywie:

![Edytor w niebieskim motywie](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 — c_EditorBlue")<br />Edytor w niebieskim motywie

![Edytor w duży kontrast #1 motyw](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 — d_EditorHC1")<br />Edytor w duży kontrast #1 motyw

### <a name="usage-patterns"></a>Wzorce użycia

Wiele typowych elementów interfejsu użytkownika ma już zdefiniowane duży kontrast kolory. Można odwoływać się do tych wzorców użycia podczas wybierania własnych nazw kolorów systemu, tak aby elementy interfejsu użytkownika były spójne z podobnymi składnikami.

| Kolor systemu | Użycie |
| --- | --- |
| ActiveCaption | -Aktywne środowisko IDE i glify przycisku okna do założenia przy aktywowaniu i naciśnięciu klawisza<br />-Tło paska tytułu dla środowiska IDE i okien z zaspływeniem<br />— Tło domyślnego paska stanu |
| ActiveCaptionText | — Aktywne środowisko IDE i tratwy systemu Windows dla pierwszego planu paska tytułu (tekst i glify)<br />— Tło i obramowanie przycisków aktywnego okna po aktywowaniu i naciśnięciu klawisza |
| Kontrola | -Pole kombi, listę rozwijaną oraz domyślne i wyłączone tło formantu wyszukiwania, w tym przycisk listy rozwijanej<br />-Tło przycisku Docker<br />— Tło paska poleceń<br />— Tło okna narzędzi |
| ControlDark | — Tło IDE<br />-Menu i separatory paska poleceń<br />-Obramowanie paska poleceń<br />— Cienie menu<br />-Okno narzędzi domyślne i obramowanie i separator aktywowany<br />— Tło przycisku przepełnienia w dokumencie<br />— Obramowanie symbolu docelowego dokowania |
| ControlDarkDark |— Nieskoncentrowane, wybrane okno karty dokumentu |
| ControlLight |-Autoukrywanie obramowania karty<br />-Pole kombi i obramowanie listy rozwijanej<br />— Tło i obramowanie obiektu docelowego dokowania |
| ControlLightLight | -Wybrane, skoncentrowane obramowanie tymczasowe |
| ControlText | -Pole kombi i symbol listy rozwijanej<br />-Okno narzędzia — niezaznaczony tekst karty |
| GrayText |-Pole kombi i lista rozwijana wyłączone obramowanie, symbol listy rozwijanej, tekst i tekst elementu menu.<br />— Tekst menu wyłączonego<br />— Tekst nagłówka kontrolki wyszukiwania "Opcje wyszukiwania"<br />-Separator sekcji kontrolki wyszukiwania |
| Wyróżnij | — Wszystkie przesuwanie i naciśnięte tła i obramowania, z wyjątkiem pola kombi menu rozwijanego i obramowania<br />-Wybrane tło elementu |
| HighlightText | — Wszystkie aktywowane i naciśnięte klawisze (tekst i glify)<br />Na pierwszym planie okna narzędzi i okna karty dokumentu<br />Obramowanie paska tytułu okna narzędziowe ukierunkowane<br />— Skoncentrowany, wybrany tymczasowy plan tabulacji<br />-Obramowanie przycisku oblewania dokumentu po aktywowaniu i naciśnięciu klawisza<br />-Wybrano obramowanie ikon|
| HotTrack | — Tło i obramowanie paska przewijania przy naciśnięciu przycisku<br />— Symbol strzałki paska przewijania przy naciśnięciu |
| InactiveCaption | — Ikony przycisków nieaktywnego środowiska IDE i tratw<br />-Tło paska tytułu dla środowiska IDE i okien z zaspływeniem<br />-Wyłączone tło kontrolki wyszukiwania |
| InactiveCaptionText | -Nieaktywne środowisko IDE i tratwowy pasek tytułu systemu Windows (tekst i glify)<br />-Nieaktywne przyciski okna i obramowanie po aktywowaniu<br />— Tło i obramowanie przycisku okna narzędzia nieskoncentrowane<br />— Wyłączono pierwszy plan sterowania wyszukiwaniem |
| Menu | — Tło menu rozwijanego<br />-Zaznaczone i wyłączone tło znacznika wyboru |
| MenuText | — Obramowanie menu rozwijanego<br />-Znaczniki Check<br />— Glify menu<br />— Tekst menu rozwijanego<br />-Wybrano obramowanie ikon |
| Paski | — Tło paska przewijania i paska przewijania, wszystkie Stany |
| Okno | -Autoukrywanie tła karty<br />-Pasek menu i tło półki poleceń<br />— Nieskoncentrowane lub niezaznaczone tło karty okna dokumentu i obramowanie dokumentu dla kart otwartych i tymczasowych<br />— Tło paska tytułu dla nieskoncentrowanego się okna narzędzi<br />-Tło karty okna narzędzi, wybrane i niezaznaczone |
| WindowFrame | -IDE — obramowanie |
| WindowText | -Autoukrywanie pierwszego planu karty<br />— Pierwszy plan karty okna narzędzi<br />— Karta okna dokumentu bez fokusu oraz niezaznaczony lub niewybrany tymczasowy plan karty<br />-Tree Wyświetl domyślny pierwszy plan i umieść kursor nad niezaznaczonym symbolem<br />-Okno narzędzia — wybrane obramowanie tabulacji<br />— Tło, obramowanie i symbol paska przewijania |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Uwidacznianie kolorów dla użytkowników końcowych

### <a name="overview"></a>Omówienie

Czasami chcesz zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Najbardziej typowym sposobem wykonania tej czynności jest użycie okna dialogowego **&gt; Opcje narzędzi** . Chyba że masz wysoce wyspecjalizowany interfejs użytkownika, który wymaga specjalnych kontroli, najprostszym sposobem na zaprezentowanie dostosowania jest strona **czcionki i kolory** w sekcji **środowisko** okna dialogowego. Dla każdego elementu, który można dostosowywać, użytkownik może zdecydować się na zmianę koloru pierwszego planu, koloru tła lub obu tych elementów.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie pakietu VSPackage dla dostosowywalnych kolorów

Pakietu VSPackage może kontrolować czcionki i kolory za pomocą niestandardowych kategorii i wyświetlać elementy na stronie właściwości czcionki i kolory. W przypadku korzystania z tego mechanizmu pakietów VSPackage musi implementować interfejs [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) i skojarzone z nim interfejsy.

W zasadzie ten mechanizm może służyć do modyfikowania wszystkich istniejących elementów wyświetlanych i kategorii, które je zawierają. Nie należy jednak jej używać do modyfikowania kategorii edytora tekstu ani elementów wyświetlanych. Aby uzyskać więcej informacji na temat kategorii Edytor tekstu, zobacz [Omówienie czcionek i kolorów](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015).

Aby zaimplementować niestandardowe kategorie lub elementy wyświetlane, pakietu VSPackage musi:

- **Utwórz lub Zidentyfikuj kategorie w rejestrze.** Implementacja środowiska IDE na stronie właściwości **czcionki i kolory** używa tych informacji, aby prawidłowo wysyłać zapytania dotyczące usługi obsługującej daną kategorię.

- **Utwórz lub Zidentyfikuj grupy w rejestrze (opcjonalnie).** Przydatne może być zdefiniowanie grupy, która reprezentuje Unię z co najmniej dwóch kategorii. W przypadku zdefiniowania grupy środowisko IDE automatycznie scala podkategorie i dystrybuuje wyświetlane elementy w grupie.

- **Implementowanie obsługi środowiska IDE.**

- **Obsługuj zmiany czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub zidentyfikować kategorie

Utwórz specjalny typ wpisu rejestru kategorii w obszarze `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` gdzie `<Category>` jest niezlokalizowaną nazwą kategorii.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorię |

 Usługa określona w rejestrze musi dostarczyć implementację [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) dla odpowiadającej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub zidentyfikować grupy

Utwórz specjalny typ wpisu rejestru kategorii w obszarze `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` gdzie `<group>` jest niezlokalizowaną nazwą grupy.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorię |

Usługa określona w rejestrze musi dostarczyć implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

![Implementacja IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 — a_FontAndColorGroup")<br />Implementacja programu `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Aby zaimplementować obsługę środowiska IDE

Zaimplementuj [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), która zwraca interfejs [IVSFONTANDCOLORDEFAULTS](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs IDE dla każdego podanego identyfikatora GUID kategorii lub grupy.

Dla każdej kategorii, która obsługuje, pakietu VSPackage implementuje oddzielne wystąpienie interfejsu [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Metody implementowane za pomocą [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) muszą zapewnić IDE z:

- Listy elementów wyświetlanych w kategorii

- Lokalizowalne nazwy dla elementów wyświetlanych

- Wyświetl informacje dla każdego elementu członkowskiego kategorii

> [!NOTE]
> Każda kategoria musi zawierać co najmniej jeden element wyświetlany.

IDE używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu do definiowania Unii kilku kategorii.

Jego implementacja zapewnia środowisko IDE z:

- Lista kategorii, które składają się na daną grupę

- Dostęp do wystąpień elementu [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) obsługującego każdą kategorię w grupie

- Nazwy grup lokalizowalnych

#### <a name="updating-the-ide"></a>Aktualizowanie środowiska IDE

IDE buforuje informacje o ustawieniach czcionek i kolorów. W związku z tym, po każdej modyfikacji konfiguracji czcionek i kolorów IDE, zapewnienie, że pamięć podręczna jest aktualna.

Aktualizowanie pamięci podręcznej odbywa się za pomocą interfejsu [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) i może być wykonywane globalnie lub tylko dla wybranych elementów.

### <a name="handling-font-and-color-changes"></a>Obsługa zmian czcionki i koloru

Aby prawidłowo obsługiwać Kolorowanie tekstu wyświetlanego przez pakietu VSPackage, usługa kolorowania obsługująca pakietu VSPackage musi odpowiadać na zmiany zainicjowane przez użytkownika za pomocą strony właściwości czcionki i kolory.

Aby to zrobić, pakietu VSPackage musi:

- **Obsługa zdarzeń generowanych przez środowisko IDE** przez implementację interfejsu [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . IDE wywołuje odpowiednią metodę po zmodyfikowaniu przez użytkownika strony czcionki i kolory. Na przykład wywołuje metodę [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) , jeśli wybrano nową czcionkę.

  **OR**

- **sondowanie środowiska IDE pod kątem zmian**. Można to zrobić za pomocą interfejsu [Niepowodzenie IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) zaimplementowanego przez system. Chociaż głównie do obsługi trwałości, Metoda [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) może uzyskać informacje o czcionce i kolorach dla elementów wyświetlanych. Aby uzyskać więcej informacji na temat ustawień czcionek i kolorów, zobacz artykuł MSDN z [dostępem do przechowywanych ustawień czcionek i kolorów](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015).

> [!NOTE]
> Aby upewnić się, że wyniki sondowania są poprawne, użyj interfejsu [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) , aby określić, czy opróżnianie pamięci podręcznej i aktualizacja jest konieczna przed wywołaniem metod pobierania interfejsu [Niepowodzenie IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) .

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie niestandardowej kategorii czcionek i kolorów bez implementowania interfejsów

Poniższy przykład kodu demonstruje, jak zarejestrować niestandardową kategorię czcionki i koloru bez implementowania interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Dla tego przykładu kodu:

- `"NameID"` = Identyfikator zasobu zlokalizowanej nazwy kategorii w pakiecie
- `"ToolWindowPackage"` = Identyfikator GUID pakietu
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` jest tylko przykładem, a rzeczywista wartość może być nowym identyfikatorem GUID dostarczonym przez realizatora.

### <a name="set-the-font-and-color-property-category-guid"></a>Ustaw identyfikator GUID kategorii właściwości i koloru

W poniższym przykładzie kodu pokazano, jak ustawić identyfikatory GUID kategorii.

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
