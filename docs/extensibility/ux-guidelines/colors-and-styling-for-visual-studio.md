---
title: Kolory i style dla programu Visual Studio | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409000"
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio

## <a name="use-color-in-visual-studio"></a>Użyj koloru w programie Visual Studio

W programie Visual Studio kolor jest używany przede wszystkim jako narzędzie do komunikacji, nie tylko jako dekoracja. Użyj co najmniej koloru i zarezerwować je dla sytuacji, w którym chcesz:

- Komunikacji znaczenia lub przynależności (na przykład, Modyfikatory platformy lub języka)

- Zwróć uwagę, (na przykład wskazującego zmianę stanu)

- Zwiększa czytelność i podaj charakterystycznych elementów krajobrazu nawigacji interfejsu użytkownika

- Zwiększ potrzebę

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w programie Visual Studio. Czasami trudno jest ustalić, której opcji używać, lub jak używać jej poprawnie. Ten temat pomoże Ci:

- Omówienie różnych usług i systemów, które umożliwiają zdefiniowanie kolorów w programie Visual Studio.

- Wybierz opcję odpowiednią dla danego elementu.

- Poprawnie opcja wybrana.

> [!NOTE]
> Nigdy nie umieszczaj kolorów szesnastkowych, RGB ani systemowych do elementów interfejsu użytkownika. Korzystając z usług umożliwia elastyczność dostosowywania aplikacji hue. Ponadto bez usługi nie będzie można korzystać z możliwości przełączania motywu [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Elementy interfejsu metody przypisywania kolorów do programu Visual Studio

Wybierz metodę, najlepiej dostosowane do elementów interfejsu użytkownika.

| Interfejs użytkownika | Metoda | Do czego one służą? |
| --- | --- | --- |
| Zostały osadzone lub autonomicznych, okno dialogowe. | **Kolory systemowe** | Nazwy systemu, które umożliwiają systemowi operacyjnemu Definiowanie koloru i wyglądu elementów interfejsu użytkownika, takich jak wspólne kontrolki okna dialogowego. |
| Niestandardowy interfejs użytkownika, który chcesz zachować spójność z całego środowiska programu VS, i posiadasz elementy interfejsu użytkownika, które pasują kategorii i znaczenia semantycznego udostępnionego tokenów. | **Wspólne kolory udostępnione** | Istniejące nazwy tokenu wstępnie zdefiniowany kolor dla określonych elementów interfejsu użytkownika |
| Masz poszczególnych funkcji lub grupy funkcji i udostępnione kolor dla podobnych elementów. | **Kolory niestandardowe** | Kolor tokenu nazw, które są specyficzne dla obszaru i nie jest przeznaczone do udostępnienia za pomocą innego interfejsu użytkownika |
| Chcesz zezwolić użytkownikom końcowym dostosowywanie interfejsu użytkownika lub zawartości (na przykład edytorów tekstu lub wyspecjalizowanych projektanta systemu windows). | **Dostosowywanie użytkownika końcowego**<br /><br />**(Narzędzia &gt; opcje okna dialogowego)** | Ustawienia zdefiniowane na stronie "czcionki i kolory" okna dialogowego **narzędzia &gt; opcje** lub wyspecjalizowana Strona specyficzna dla jednej funkcji interfejsu użytkownika. |

### <a name="visual-studio-themes"></a>Visual Studio motywów

Program Visual Studio oferuje trzy różne motywy kolorów: jasne, ciemne i niebieskie. Ta funkcja wykrywa także trybu wysokiego kontrastu, czyli motyw kolorów systemowe przeznaczone dla ułatwień dostępu.

Użytkownicy są monitowani o wybranie motywu podczas pierwszego korzystania z programu Visual Studio i mogą przełączać motywy później, przechodząc do **opcji narzędzia &gt; opcje &gt; środowisku &gt; ogólne** i wybierając nowy motyw z menu rozwijanego "motyw kolorów".

Użytkownicy umożliwia również Panelu sterowania Przełącz całego systemów w jednym z kilku kompozycji o wysokim kontraście. Jeśli użytkownik wybierze kompozycję Duży kontrast, następnie selektor motywu kolorów programu Visual Studio nie jest już ma wpływ na kolory w programie Visual Studio, mimo że wszelkie zmiany motywu są zapisywane dla, gdy użytkownik opuszcza trybu wysokiego kontrastu. Aby uzyskać więcej informacji o trybie duży kontrast, zobacz [wybieranie duży kontrast kolory](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Usługa VSColor

Program Visual Studio udostępnia usługi kolorów środowiska, znana jako usługa VSColor, dzięki czemu można powiązać wartości kolorów elementy interfejsu użytkownika do wpisu o nazwie zawierające wartości kolorów dla każdego motywu programu Visual Studio. Daje to gwarancję, że kolory automatycznie zmieni się na odzwierciedla bieżący użytkownik wybrał motyw lub system trybu wysokiego kontrastu. Korzystanie z usługi oznacza, że implementacja wszystkie zmiany dotyczące motyw kolorów odbywa się w jednym miejscu i korzystania z typowych udostępnione kolory z usługi interfejs użytkownika będzie automatycznie odzwierciedlał nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="implementation"></a>Wdrażanie

Kod źródłowy programu Visual Studio zawiera kilka plików definicji pakietu, które zawierają listy tokenów nazw i wartości odpowiednich kolorów dla każdego motywu. Usługa kolor odczytuje VSColors zdefiniowane w tych plikach definicji pakietu. Te kolory są przywoływane w znacznikach XAML lub w kodzie, a następnie ładowane za pomocą metody `IVsUIShell5.GetThemedColor` lub mapowania DynamicResource —.

### <a name="system-colors"></a>Kolory systemowe

Formanty standardowe odwoływać się kolory systemowe domyślnie. Jeśli chcesz, aby interfejs użytkownika używał kolorów systemowych, takich jak podczas tworzenia okna dialogowego osadzone lub autonomiczne, nie musisz nic robić.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Typowe udostępnione kolory w usłudze VSColor

Elementów interfejsu powinny odzwierciedlać ogólną środowiska Visual Studio. Korzystając z tych wspólnych kolorów, które są odpowiednie dla projektowanego składnika interfejsu użytkownika, należy się upewnić, że interfejs jest zgodny z innymi interfejsami programu Visual Studio i że kolory będą aktualizowane automatycznie po dodaniu lub zaktualizowaniu motywów.

Przed rozpoczęciem korzystania z typowych udostępnione kolory, upewnij się, że rozumiesz, jak używać ich poprawnie. Niepoprawne użycie wspólnej udostępnione kolory może prowadzić do obsługi niespójne irytujące i mylące dla użytkowników.

### <a name="user-customizable-colors"></a>Kolorów można dostosowywać użytkownika

Zobacz: [Uwidacznianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami trzeba zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Dostosowywalne składniki interfejsu użytkownika znajdują się w sekcji **czcionki i kolory** okna dialogowego **Narzędzia &gt; opcje** , w którym użytkownicy mogą wybrać zmianę koloru pierwszego planu, koloru tła lub obu tych funkcji.

![Narzędzia &gt; opcje okna dialogowego](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 — a_ToolsOptionsDialog")<br />Narzędzia &gt; opcje okna dialogowego

## <a name="BKMK_TheVSColorService"></a>Usługa VSColor

Program Visual Studio udostępnia usługi kolorów środowiska, nazywany również usługi VSColor lub powłoki kolorów. Ta usługa pozwala powiązać wartości kolorów elementy interfejsu użytkownika zestaw zawierający kolorów dla każdego motywu kolorów nazwa wartość. Usługa VSColor należy użyć dla wszystkich elementów interfejsu użytkownika, tak aby kolory automatycznie zmieniać, aby odzwierciedlić bieżący motyw wybrane przez użytkownika tak, aby interfejsu użytkownika powiązany z usługami kolorów środowiska integruje się z nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa

Środowisko usługi kolor odczytuje VSColors zdefiniowane w .pkgdef składnik interfejsu użytkownika. Te VSColors są następnie odwoływane w znacznikach XAML lub kodzie i są ładowane za pomocą `IVsUIShell5.GetThemedColor` lub `DynamicResource` mapowania.

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 — a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

Istnieją różne sposoby dostępu korzystają z usługi VSColor w zależności od tego, jakiego rodzaju kolor tokeny możesz oraz jakiego typu kodu mają.

#### <a name="predefined-environment-colors"></a>Środowisko wstępnie zdefiniowanych kolorów

##### <a name="from-native-code"></a>Z kodu natywnego

Powłoka udostępnia usługę zapewniającą dostęp do `COLORREF` kolorów. Usługa/interfejs jest:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80. idl Wyliczenie `__VSSYSCOLOREX` ma stałe koloru powłoki. Aby go użyć, należy przekazać jako wartość indeksu jedną z wartości z `enum __VSSYSCOLOREX` udokumentowanej w witrynie MSDN lub zwykły numer indeksu, który jest `GetSysColor`przez interfejs API systemu Windows. W ten sposób otrzymuje wartość RGB koloru, który ma zostać użyty w drugim parametrze.

W przypadku przechowywania pióra lub pędzla przy użyciu nowego koloru należy `AdviseBroadcastMessages` (poza powłoką programu Visual Studio) i słuchać `WM_SYSCOLORCHANGE` i `WM_THEMECHANGED` komunikatów.

Aby uzyskać dostęp do usługi Color w kodzie natywnym, należy wywołać wywołanie podobne do poniższego:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Wartości `COLORREF` zwracane przez `GetVSSysColorEx()` zawierają tylko składniki R, G, B koloru motywu. Jeśli wpis motyw używa przezroczystości, wartość kanał alfa jest odrzucany przed zwróceniem. W związku z tym, jeśli wymagany jest kolor środowiska, który ma być używany w miejscu, w którym jest ważne, należy używać `IVsUIShell5.GetThemedColor` zamiast `IVsUIShell2::GetVSSysColorEx`, jak opisano w dalszej części tego tematu.

##### <a name="from-managed-code"></a>Z poziomu kodu zarządzanego

Uzyskiwanie dostępu do usługi VSColor za pomocą natywnego kodu jest dość prosta. Jeśli pracujesz za pomocą kodu zarządzanego, jednak Określanie sposobu korzystania z usługi może być trudne. Mając to na uwadze poniżej przedstawiono fragment kodu języka C# ukazujące tego procesu:

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

Jeśli pracujesz w języku Visual Basic, należy użyć:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Z poziomu interfejsu użytkownika WPF

Można powiązać z kolorami programu Visual Studio za pomocą wartości wyeksportowanych do `ResourceDictionary`aplikacji. Poniżej przedstawiono przykład używa zasobów z tabeli kolorów, a także powiązanie z danymi czcionka środowiska w XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Pomocnik klasy i metody dla kodu zarządzanego

W przypadku kodu zarządzanego Biblioteka struktury pakietu zarządzanego powłoki (`Microsoft.VisualStudio.Shell.12.0.dll`) zawiera kilka klas pomocnika, które ułatwiają korzystanie z nich.

Metody pomocnika w klasie `Microsoft.VisualStudio.Shell.VsColors` w MPF obejmują `GetThemedGDIColor()` i `GetThemedWPFColor()`. Te metody pomocnika zwracają wartość koloru wpisu motywu jako `System.Drawing.Color` lub `System.Windows.Media.Color`, które mają być używane w interfejsie WinForms lub interfejsu użytkownika WPF.

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

Klasy można również uzyskać identyfikatory VSCOLOR dla danego klucza zasobu kolor WPF, lub na odwrót.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody klasy `VsColors` wysyłają zapytania do usługi VSColor, aby zwracały wartość koloru przy każdym wywołaniu. Aby uzyskać wartość koloru jako `System.Drawing.Color`, alternatywą dla lepszej wydajności jest użycie metod klasy `Microsoft.VisualStudio.PlatformUI.VSThemeColor`, w której są buforowane wartości kolorów uzyskane z usługi VSColor. Klasa zdarzeń komunikatów rozgłaszanych powłoki subskrybuje wewnętrznie i odrzuca wartość w pamięci podręcznej, gdy wystąpi zdarzenie Zmienianie motywu. Ponadto zapewnia klasy. Przyjazne dla NET zdarzeń do subskrybowania zmiany motywu. Użyj zdarzenia `ThemeChanged`, aby dodać nowy program obsługi, i użyj metody `GetThemedColor()`, aby uzyskać wartości koloru dla `ThemeResourceKeys` zainteresowania. Przykładowy kod może wyglądać następująco:

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

## <a name="BKMK_ChoosingHighContrastColors"></a>Wybieranie duży kontrast kolorów

### <a name="overview"></a>Omówienie

Windows używa kilka motywów poziomie systemu o wysokim kontraście podnoszących kontrast kolorów tekstu, tła i obrazów, dzięki czemu elementy są wyświetlane na ekranie znacznie. Ze względu na ułatwienia dostępu jest ważne, że elementy interfejsu programu Visual Studio poprawnie odpowiadać, gdy użytkownicy będą przełączać się do motywu o wysokim kontraście.

Tylko niewielki podzbiór kolory systemowe może służyć do dużego kontrastu, motywów. Podczas wybierania systemu nazw kolorów, należy pamiętać o następujących wskazówek:

- **Wybierz kolory systemowe, które mają taką samą semantykę** jak element, który jest kolorem. Na przykład jeśli użytkownik zdecyduje o wysokim kontraście kolor tekstu w oknie umożliwia WindowText i nie ControlText.

- **Wybieraj jednocześnie pary pierwszego planu/tła** lub nie masz pewności, że wybór kolorów będzie działać we wszystkich motywach duży kontrast.

- **Ustal, które części interfejsu użytkownika są najważniejsze i upewnij się, że obszary zawartości zostaną** wystawione. Utracisz dużo szczegółów, dzięki czemu delikatne różnice w odcienie odnoszą się zwykle, dlatego w celu zdefiniowania obszarów zawartości często używane są kolory silnego obramowania, ponieważ nie ma żadnych wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Zestaw kolorów systemu

Tabela na [blogu zespołu WPF: SystemColors Reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) wskazuje pełny zestaw nazw kolorów systemowych i odpowiadający odcieni wyświetlany w każdym motywie.

W przypadku zastosowania tego ograniczonego zestawu kolorów do interfejsu użytkownika należy się *spodziewać, że utracisz delikatne szczegóły, które były obecne w motywach "normal"* . Oto przykład interfejsu użytkownika przy użyciu subtelne szarego kolorów, które są używane do odróżniania obszarów w obrębie okna narzędzi. Po połączeniu się z tym samym oknie, które są wyświetlane w trybie dużego kontrastu, możesz zobaczyć, że wszystkim programistom są tego samego rozwiązania hue, a obramowania te obszary są wskazywane przez samodzielnie obramowania:

![Przykład, w jaki sposób subtelne szczegóły są tracone w duży kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 — a_PropertiesWindow")<br />Przykład, w jaki sposób subtelne szczegóły są tracone w duży kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Wybieranie koloru tekstu w edytorze

Tekst z kolorami jest używany w edytorze lub na powierzchni projektowej w celu wskazania znaczenia, takich jak umożliwienie łatwej identyfikacji grup podobnych elementów. W kompozycję Duży kontrast jednak nie masz możliwość rozróżnienia między więcej niż trzech kolorów tekstu. WindowText, GrayText i HotTrackText są dostępne na powierzchniach WindowBackground kolory tylko. Ponieważ nie można użyć więcej niż trzech kolorów, starannie wybrać najbardziej istotne różnice, które mają być wyświetlane w trybie dużego kontrastu.

Odcieni dla każdego tokenu nazwy dozwolona powierzchni edytora, w jakiej występują na każdym kompozycję Duży kontrast:

![Porównanie edytora duży kontrast](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 — b_HCEditorComparison")<br />Porównanie edytora duży kontrast

Przykłady powierzchni edytora w motyw niebieski:

![Edytor w niebieskim motywie](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 — c_EditorBlue")<br />Edytor w niebieskim motywie

![Edytor w duży kontrast #1 motyw](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 — d_EditorHC1")<br />Edytor w duży kontrast #1 motyw

### <a name="usage-patterns"></a>Wzorce użycia

Wiele typowych elementów interfejsu użytkownika ma już zdefiniowane duży kontrast kolory. Można się odwołać te wzorce użycia podczas wybierania nazw kolorów z własnym systemem tak, aby elementów interfejsu użytkownika są zgodne z podobnych elementów.

| Kolor systemu | Sposób użycia |
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
| Pasek przewijania | — Tło paska przewijania i paska przewijania, wszystkie Stany |
| Okno | -Autoukrywanie tła karty<br />-Pasek menu i tło półki poleceń<br />— Nieskoncentrowane lub niezaznaczone tło karty okna dokumentu i obramowanie dokumentu dla kart otwartych i tymczasowych<br />— Tło paska tytułu dla nieskoncentrowanego się okna narzędzi<br />-Tło karty okna narzędzi, wybrane i niezaznaczone |
| WindowFrame | -IDE — obramowanie |
| WindowText | -Autoukrywanie pierwszego planu karty<br />— Pierwszy plan karty okna narzędzi<br />— Karta okna dokumentu bez fokusu oraz niezaznaczony lub niewybrany tymczasowy plan karty<br />-Tree Wyświetl domyślny pierwszy plan i umieść kursor nad niezaznaczonym symbolem<br />-Okno narzędzia — wybrane obramowanie tabulacji<br />— Tło, obramowanie i symbol paska przewijania |

## <a name="BKMK_ExposingColorsForEndUsers"></a>Uwidacznianie kolorów dla użytkowników końcowych

### <a name="overview"></a>Omówienie

Czasami chcesz zezwolić użytkownikowi końcowemu na dostosowanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Najbardziej typowym sposobem wykonania tej czynności jest użycie okna dialogowego **narzędzia &gt; opcje** . Chyba że masz wysoce wyspecjalizowany interfejs użytkownika, który wymaga specjalnych kontroli, najprostszym sposobem na zaprezentowanie dostosowania jest strona **czcionki i kolory** w sekcji **środowisko** okna dialogowego. Dla każdego elementu, który należy udostępnić dostosowywania użytkownik może wybrać zmienić kolor pierwszego planu i kolor tła.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie pakietu VSPackage dla kolorów można dostosowywać

Pakietu VSPackage można kontrolować, czcionki i kolory za pomocą niestandardowych kategorii i wyświetlania elementów na stronie właściwości czcionki i kolory. W przypadku korzystania z tego mechanizmu pakietów VSPackage musi implementować interfejs [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) i skojarzone z nim interfejsy.

W zasadzie mechanizm ten może służyć do modyfikowania wszystkich istniejących elementów ekranu i kategorie, zawierające je. Jednak nie ją stosować do modyfikowania kategorii edytora tekstu lub jego elementów wyświetlana. Aby uzyskać więcej informacji na temat kategorii Edytor tekstu, zobacz [Omówienie czcionek i kolorów](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Aby implementować niestandardowe kategorie lub wyświetlić elementy, pakietu VSPackage musi:

- **Utwórz lub Zidentyfikuj kategorie w rejestrze.** Implementacja środowiska IDE na stronie właściwości **czcionki i kolory** używa tych informacji, aby prawidłowo wysyłać zapytania dotyczące usługi obsługującej daną kategorię.

- **Utwórz lub Zidentyfikuj grupy w rejestrze (opcjonalnie).** Może być przydatne do definiowania grupy, która reprezentuje sumę dwóch lub więcej kategorii. Grupa jest zdefiniowany, IDE automatycznie scala podkategorii i dystrybuuje wyświetlania elementów w obrębie grupy.

- **Implementowanie obsługi środowiska IDE.**

- **Obsługuj zmiany czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub wskazać kategorii

Utwórz specjalny typ wpisu rejestru kategorii w `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` gdzie `<Category>` jest niezlokalizowaną nazwą kategorii.

Należy wypełnić rejestru za pomocą dwóch wartości:

| Name (Nazwa) | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikowania kategorii |
| Pakiet | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorii |

 Usługa określona w rejestrze musi dostarczyć implementację [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) dla odpowiadającej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub wskazać grupy

Utwórz specjalny typ wpisu rejestru kategorii w `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` gdzie `<group>` jest niezlokalizowaną nazwą grupy.

Należy wypełnić rejestru za pomocą dwóch wartości:

| Name (Nazwa) | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikowania kategorii |
| Pakiet | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorii |

Usługa określona w rejestrze musi dostarczyć implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

![Implementacja IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 — a_FontAndColorGroup")<br />Implementacja `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Obsługa środowiska IDE

Zaimplementuj [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), która zwraca interfejs [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) lub interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> do IDE dla każdego dostarczonego identyfikatora GUID kategorii lub grupy.

Dla każdej kategorii, która obsługuje, pakietu VSPackage implementuje oddzielne wystąpienie interfejsu [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Metody implementowane za pomocą [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) muszą zapewnić IDE z:

- Listy wyświetlania elementów w kategorii

- Lokalizowalne nazwy wyświetlania elementów

- Wyświetlanie informacji dla każdego elementu członkowskiego kategorii

> [!NOTE]
> Każda kategoria musi zawierać co najmniej jeden element wyświetlany.

IDE używa interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>, aby zdefiniować Unię kilku kategorii.

Jego implementacja zapewnia środowisko IDE z:

- Lista kategorii, które składają się na daną grupę

- Dostęp do wystąpień elementu [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) obsługującego każdą kategorię w grupie

- Nazwy grup Lokalizowalny

#### <a name="updating-the-ide"></a>Aktualizowanie środowiska IDE

IDE buforuje informacje o ustawieniach czcionek i kolorów. Dlatego po każdej modyfikacji konfiguracji środowiska IDE czcionek i kolorów, zapewnia, że pamięć podręczna jest aktualne jest najlepszym rozwiązaniem.

Aktualizowanie pamięci podręcznej odbywa się za pomocą interfejsu [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) i może być wykonywane globalnie lub tylko dla wybranych elementów.

### <a name="handling-font-and-color-changes"></a>Obsługa zmian czcionek i kolorów

Aby prawidłowo obsługiwać kolorowanie tekst, który wyświetla pakietu VSPackage, usługa kolorowanie obsługi pakietu VSPackage musi odpowiedzieć na zainicjowanego przez użytkownika zmian za pomocą strony właściwości czcionki i kolory.

Aby to zrobić, pakietu VSPackage musi:

- **Obsługa zdarzeń generowanych przez środowisko IDE** przez implementację interfejsu [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . IDE wywołuje odpowiednią metodę następujące modyfikacje użytkownika strony czcionek i kolorów. Na przykład wywołuje metodę [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) , jeśli wybrano nową czcionkę.

  **ORAZ**

- **sondowanie środowiska IDE pod kątem zmian**. Można to zrobić za pomocą interfejsu [Niepowodzenie IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) zaimplementowanego przez system. Chociaż głównie do obsługi trwałości, Metoda [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) może uzyskać informacje o czcionce i kolorach dla elementów wyświetlanych. Aby uzyskać więcej informacji na temat ustawień czcionek i kolorów, zobacz artykuł MSDN z [dostępem do przechowywanych ustawień czcionek i kolorów](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Aby upewnić się, że wyniki sondowania są poprawne, użyj interfejsu [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) , aby określić, czy opróżnianie pamięci podręcznej i aktualizacja jest konieczna przed wywołaniem metod pobierania interfejsu [Niepowodzenie IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) .

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie niestandardowych czcionek i kolorów kategorii bez implementacji interfejsów

Poniższy przykład kodu pokazuje, jak się zarejestrować niestandardowych czcionek i kolorów kategorii bez implementacji interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Dla tego przykładu kodu:

- `"NameID"` = identyfikator zasobu zlokalizowanej nazwy kategorii w pakiecie
- `"ToolWindowPackage"` = identyfikator GUID pakietu
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` jest tylko przykładem, a rzeczywista wartość może być nowym identyfikatorem GUID dostarczonym przez realizatora.

### <a name="set-the-font-and-color-property-category-guid"></a>Ustaw kategorię właściwości czcionek i kolorów identyfikatora GUID

Poniższy przykładowy kod pokazuje ustawienie kategorii identyfikatorów GUID.

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
