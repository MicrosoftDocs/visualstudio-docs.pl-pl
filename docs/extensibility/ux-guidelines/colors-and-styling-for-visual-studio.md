---
title: Kolory i style dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12555b48550d252ce125ac437c1e30d5ae22fae9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914611"
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio

## <a name="use-color-in-visual-studio"></a>Użyj koloru w programie Visual Studio

W programie Visual Studio kolor jest używany przede wszystkim jako narzędzie do komunikacji, nie tylko jako dekoracja. Użyj co najmniej koloru i zarezerwować je dla sytuacji, w którym chcesz:

- Komunikacji znaczenia lub przynależności (na przykład, Modyfikatory platformy lub języka)

- Zwróć uwagę, (na przykład wskazującego zmianę stanu)

- Zwiększa czytelność i podaj charakterystycznych elementów krajobrazu nawigacji interfejsu użytkownika

- Zwiększ potrzebę

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w programie Visual Studio. Czasami może być trudne do figury się, która opcja jest powinien używać lub jak prawidłowo z niej korzystać. Ten temat pomoże Ci:

- Omówienie różnych usług i systemów, które umożliwiają zdefiniowanie kolorów w programie Visual Studio.

- Wybierz opcję odpowiednią dla danego elementu.

- Poprawnie opcja wybrana.

> [!NOTE]
> Nigdy nie umieszczaj szesnastkowy RGB i kolorów systemowych do elementów interfejsu użytkownika. Korzystając z usług umożliwia elastyczność dostosowywania aplikacji hue. Ponadto bez usługi, nie będzie mógł korzystać z zalet możliwości przełączanie motywów [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Elementy interfejsu metody przypisywania kolorów do programu Visual Studio

Wybierz metodę, najlepiej dostosowane do elementów interfejsu użytkownika.

| Interfejs użytkownika | Metoda | Do czego one służą? |
| --- | --- | --- |
| Zostały osadzone lub autonomicznych, okno dialogowe. | **Kolory systemowe** | Nazwami systemowymi, które umożliwiają systemu operacyjnego zdefiniować wygląd elementów interfejsu użytkownika i kolor, takich jak formanty standardowe okno dialogowe. |
| Niestandardowy interfejs użytkownika, który chcesz zachować spójność z całego środowiska programu VS, i posiadasz elementy interfejsu użytkownika, które pasują kategorii i znaczenia semantycznego udostępnionego tokenów. | **Typowe udostępnione kolory** | Istniejące nazwy tokenu wstępnie zdefiniowany kolor dla określonych elementów interfejsu użytkownika |
| Masz poszczególnych funkcji lub grupy funkcji i udostępnione kolor dla podobnych elementów. | **Kolory niestandardowe** | Kolor tokenu nazw, które są specyficzne dla obszaru i nie jest przeznaczone do udostępnienia za pomocą innego interfejsu użytkownika |
| Chcesz zezwolić użytkownikom końcowym dostosowywanie interfejsu użytkownika lub zawartości (na przykład edytorów tekstu lub wyspecjalizowanych projektanta systemu windows). | **Dostosowywania przez użytkownika końcowego**<br /><br />**(Narzędzia &gt; okna dialogowego Opcje)** | Ustawienia zdefiniowane na stronie "Czcionki i kolory" **narzędzia &gt; opcje** okna dialogowego lub wyspecjalizowanych specyficzne dla funkcji interfejsu użytkownika w jednej strony. |

### <a name="visual-studio-themes"></a>Visual Studio motywów

Program Visual Studio zawiera trzy kompozycje inny kolor: światła, ciemny i niebieski. Ta funkcja wykrywa także trybu wysokiego kontrastu, czyli motyw kolorów systemowe przeznaczone dla ułatwień dostępu.

Użytkownicy wyświetlony monit o wybranie motywu podczas ich pierwszego użycia programu Visual Studio i będą mogli przełączyć motywy później, przechodząc do **narzędzia &gt; opcje &gt; środowiska &gt; ogólne** i wybierając pozycję Nowy motyw z menu rozwijane "motyw kolorów".

Użytkownicy umożliwia również Panelu sterowania Przełącz całego systemów w jednym z kilku kompozycji o wysokim kontraście. Jeśli użytkownik wybierze kompozycję Duży kontrast, następnie selektor motywu kolorów programu Visual Studio nie jest już ma wpływ na kolory w programie Visual Studio, mimo że wszelkie zmiany motywu są zapisywane dla, gdy użytkownik opuszcza trybu wysokiego kontrastu. Aby uzyskać więcej informacji na temat trybu wysokiego kontrastu, zobacz [wybierając duży kontrast — kolory](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Usługa VSColor

Program Visual Studio udostępnia usługi kolorów środowiska, znana jako usługa VSColor, dzięki czemu można powiązać wartości kolorów elementy interfejsu użytkownika do wpisu o nazwie zawierające wartości kolorów dla każdego motywu programu Visual Studio. Daje to gwarancję, że kolory automatycznie zmieni się na odzwierciedla bieżący użytkownik wybrał motyw lub system trybu wysokiego kontrastu. Korzystanie z usługi oznacza, że implementacja wszystkie zmiany dotyczące motyw kolorów odbywa się w jednym miejscu i korzystania z typowych udostępnione kolory z usługi interfejs użytkownika będzie automatycznie odzwierciedlał nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="implementation"></a>Implementacja

Kod źródłowy programu Visual Studio zawiera kilka plików definicji pakietu, które zawierają listy tokenów nazw i wartości odpowiednich kolorów dla każdego motywu. Usługa kolor odczytuje VSColors zdefiniowane w tych plikach definicji pakietu. Te kolory są przywoływany w znaczniku XAML lub w kodzie, a następnie ładowane przy użyciu jednej `IVsUIShell5.GetThemedColor` metody lub mapowania dynamicresource —.

### <a name="system-colors"></a>Kolory systemowe

Formanty standardowe odwoływać się kolory systemowe domyślnie. Jeśli chcesz, aby Twój interfejs użytkownika, aby użyć kolorów systemowych, takich jak podczas tworzenia okna dialogowego osadzone lub autonomicznych, nie trzeba podejmować żadnych działań.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Typowe udostępnione kolory w usłudze VSColor

Elementów interfejsu powinny odzwierciedlać ogólną środowiska Visual Studio. Dzięki ponownemu wykorzystaniu wspólnej udostępnione kolory, które są odpowiednie dla składników interfejsu użytkownika, którą projektujesz, upewnij się że interfejsu jest spójna z innymi interfejsami programu Visual Studio i że kolory automatycznie zaktualizuje podczas motywy są dodawane lub aktualizowane.

Przed rozpoczęciem korzystania z typowych udostępnione kolory, upewnij się, że rozumiesz, jak używać ich poprawnie. Niepoprawne użycie wspólnej udostępnione kolory może prowadzić do obsługi niespójne irytujące i mylące dla użytkowników.

### <a name="user-customizable-colors"></a>Kolorów można dostosowywać użytkownika

Zobacz: [Udostępnianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami można zezwolić użytkownikom końcowym należy dostosować interfejs użytkownika, takich jak podczas tworzenia edytora kodu lub powierzchni projektowej. Elementy interfejsu użytkownika znajdują się w **czcionki i kolory** części **narzędzia &gt; opcje** okno dialogowe, w którym użytkownicy mogą wybierać można zmienić kolor pierwszego planu i kolor tła.

![Narzędzia &gt; okna dialogowego Opcje](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Narzędzia &gt; okno dialogowe Opcje

##  <a name="BKMK_TheVSColorService"></a> Usługa VSColor

Program Visual Studio udostępnia usługi kolorów środowiska, nazywany również usługi VSColor lub powłoki kolorów. Ta usługa pozwala powiązać wartości kolorów elementy interfejsu użytkownika zestaw zawierający kolorów dla każdego motywu kolorów nazwa wartość. Usługa VSColor należy użyć dla wszystkich elementów interfejsu użytkownika, tak aby kolory automatycznie zmieniać, aby odzwierciedlić bieżący motyw wybrane przez użytkownika tak, aby interfejsu użytkownika powiązany z usługami kolorów środowiska integruje się z nowe motywy w przyszłych wersjach programu Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa

Środowisko usługi kolor odczytuje VSColors zdefiniowane w .pkgdef składnik interfejsu użytkownika. Te VSColors następnie odwołuje się XAML znaczników lub innego kodu i są ładowane przy użyciu jednej `IVsUIShell5.GetThemedColor` lub `DynamicResource` mapowania.

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

Istnieją różne sposoby dostępu korzystają z usługi VSColor w zależności od tego, jakiego rodzaju kolor tokeny możesz oraz jakiego typu kodu mają.

#### <a name="predefined-environment-colors"></a>Środowisko wstępnie zdefiniowanych kolorów

##### <a name="from-native-code"></a>Z kodu natywnego

Powłoka udostępnia usługę, która zapewnia dostęp do `COLORREF` kolorów. Usługa/interfejs jest:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80.idl, wyliczenia `__VSSYSCOLOREX` ma stałe kolor powłoki. Aby go użyć, Przekaż jako wartość indeksu jedną z wartości z `enum __VSSYSCOLOREX` udokumentowane w witrynie MSDN lub regularnych indeksu, number, system Windows API, `GetSysColor`, akceptuje. W ten sposób otrzymuje wartość RGB koloru, który ma zostać użyty w drugim parametrze.

Jeśli przechowywanie pióro lub pędzla o nowy kolor, musisz najpierw `AdviseBroadcastMessages` (zniżki w stosunku do programu Visual Studio shell) i posłuchaj `WM_SYSCOLORCHANGE` i `WM_THEMECHANGED` wiadomości.


Aby uzyskać dostęp do usługi kolorów w kodzie natywnym, wprowadzisz wywołań, który jest podobny do tego:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF` Wartości zwracanych przez `GetVSSysColorEx()` zawiera po prostu R, G, B składniki kolor motywu. Jeśli wpis motyw używa przezroczystości, wartość kanał alfa jest odrzucany przed zwróceniem. W związku z tym, jeśli kolorów środowiska zainteresowania musi ma być używany w miejscu, w których kanału przezroczystości jest ważna, należy użyć `IVsUIShell5.GetThemedColor` zamiast `IVsUIShell2::GetVSSysColorEx`, zgodnie z opisem w dalszej części tego tematu.

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

Możesz powiązać kolorów wartości eksportowane do aplikacji z programu Visual Studio `ResourceDictionary`. Poniżej przedstawiono przykład używa zasobów z tabeli kolorów, a także powiązanie z danymi czcionka środowiska w XAML.

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

Dla kodu zarządzanego, biblioteka środowiska pakietu zarządzanego powłoki (`Microsoft.VisualStudio.Shell.12.0.dll`) zawiera kilka klas pomocniczych, które umożliwia korzystanie z motywów kolorów.

Metody pomocnicze w `Microsoft.VisualStudio.Shell.VsColors` zawierają klasy w MPF `GetThemedGDIColor()` i `GetThemedWPFColor()`. Tych metod pomocniczych zwraca wartość koloru motywu wpisu jako `System.Drawing.Color` lub `System.Windows.Media.Color`, który zostanie użyty w WinForms lub WPF UI.

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

Metody `VsColors` klasy zapytań do usługi VSColor, aby zwrócić wartość koloru każdorazowo ich wywołania. Można uzyskać wartości koloru jako `System.Drawing.Color`, alternatywą o lepszej wydajności jest zamiast tego należy użyć metod `Microsoft.VisualStudio.PlatformUI.VSThemeColor` klasy, która buforuje uzyskane z usługi VSColor wartości kolorów. Klasa zdarzeń komunikatów rozgłaszanych powłoki subskrybuje wewnętrznie i odrzuca wartość w pamięci podręcznej, gdy wystąpi zdarzenie Zmienianie motywu. Ponadto zapewnia klasy. Przyjazne dla NET zdarzeń do subskrybowania zmiany motywu. Użyj `ThemeChanged` zdarzenie, aby dodać nowy program obsługi, a następnie użyć `GetThemedColor()` metodę, aby uzyskać kolor wartości `ThemeResourceKeys` zainteresowania. Przykładowy kod może wyglądać następująco:

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

##  <a name="BKMK_ChoosingHighContrastColors"></a> Wybierając duży kontrast — kolory

### <a name="overview"></a>Omówienie

Windows używa kilka motywów poziomie systemu o wysokim kontraście podnoszących kontrast kolorów tekstu, tła i obrazów, dzięki czemu elementy są wyświetlane na ekranie znacznie. Ze względu na ułatwienia dostępu jest ważne, że elementy interfejsu programu Visual Studio poprawnie odpowiadać, gdy użytkownicy będą przełączać się do motywu o wysokim kontraście.

Tylko niewielki podzbiór kolory systemowe może służyć do dużego kontrastu, motywów. Podczas wybierania systemu nazw kolorów, należy pamiętać o następujących wskazówek:

- **Wybierz kolory systemowe, które mają takie samo znaczenie semantyczne** jako element, który jest kolorowania. Na przykład jeśli użytkownik zdecyduje o wysokim kontraście kolor tekstu w oknie umożliwia WindowText i nie ControlText.

- **Wybierz pary tła/na pierwszym planie** razem lub nie będziesz mieć pewność, że wybrany kolor będzie działać w wszystkich tematów o wysokim kontraście.

- **Określić, które części interfejsu użytkownika są najważniejsze i upewnij się, że wyróżnienia obszarów zawartości.** Wiele szczegółów, który zazwyczaj będzie odróżnić niewielkie różnice w odcień koloru, zostaną utracone, więc stosowania kolorów obramowania silne wspólne do definiowania obszarów zawartości, ponieważ istnieją żadnych wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Zestaw kolorów systemu

Tabeli u [Blog zespołu programu WPF: Odwołanie SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) wskazuje kompletny zestaw nazw kolorów systemowych i odpowiednie odcienie wyświetlane w każdym temacie.

Gdy zastosowanie ograniczony zestaw kolorów, aby Twój interfejs użytkownika *oczekuje się, utracisz subtelne szczegółowe informacje, które były obecne w "normal" motywy*. Oto przykład interfejsu użytkownika przy użyciu subtelne szarego kolorów, które są używane do odróżniania obszarów w obrębie okna narzędzi. Po połączeniu się z tym samym oknie, które są wyświetlane w trybie dużego kontrastu, możesz zobaczyć, że wszystkim programistom są tego samego rozwiązania hue, a obramowania te obszary są wskazywane przez samodzielnie obramowania:

![Przykład subtelny sposób szczegółowe informacje zostaną utracone o wysokim kontraście](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Przykład subtelny sposób szczegółowe informacje zostaną utracone o wysokim kontraście

#### <a name="choosing-text-colors-in-an-editor"></a>Wybieranie koloru tekstu w edytorze

Pokolorowany ciąg tekst jest używany w edytorze lub na powierzchni projektowej, aby wskazać znaczenia, jak w przypadku zezwalania ułatwiający identyfikację grupy podobnych elementów. W kompozycję Duży kontrast jednak nie masz możliwość rozróżnienia między więcej niż trzech kolorów tekstu. WindowText, GrayText i HotTrackText są dostępne na powierzchniach WindowBackground kolory tylko. Ponieważ nie można użyć więcej niż trzech kolorów, starannie wybrać najbardziej istotne różnice, które mają być wyświetlane w trybie dużego kontrastu.

Odcieni dla każdego tokenu nazwy dozwolona powierzchni edytora, w jakiej występują na każdym kompozycję Duży kontrast:

![Wysoki kontrast edytora porównania](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Wysoki kontrast edytora porównania

Przykłady powierzchni edytora w motyw niebieski:

![Edytor w motyw niebieski](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Edytor w motyw niebieski

![Edytor w kompozycję Duży kontrast nr 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Edytor w kompozycję Duży kontrast nr 1

### <a name="usage-patterns"></a>Wzorce użycia

Wiele typowych elementów interfejsu użytkownika już dużego kontrastu kolorów zdefiniowane. Można się odwołać te wzorce użycia podczas wybierania nazw kolorów z własnym systemem tak, aby elementów interfejsu użytkownika są zgodne z podobnych elementów.

| Kolor systemu | Użycie |
| --- | --- |
| ActiveCaption | -Active IDE i okna rafted symbole przycisk aktywowany, a następnie naciśnij klawisz<br />-Tło paska title IDE i rafted systemu windows<br />— Tło paska stanu domyślne |
| ActiveCaptionText | -Active IDE i okna rafted dla pierwszego planu paska tytułu (tekst i symbole)<br />-Tło i obramowanie aktywnego okna przycisków po wskazaniu wskaźnikiem, a następnie naciśnij klawisz |
| Formant | — Kontrolowanie domyślne i wyłączone w tle, w tym przycisk listy rozwijanej pola kombi, listy rozwijanej i wyszukiwania<br />-Tło przycisku target dock<br />— Tło paska polecenie<br />— Tło okna Narzędzie |
| ControlDark | -Tło IDE<br />— Separatory pasek menu i poleceń<br />— Obramowania paska polecenie<br />-Shadows menu.<br />-Narzędzie separator i obramowanie domyślne i aktywuje karcie okna<br />— Dobrze dokumentu tło przycisku przepełnienia<br />-Obramowanie symbol target dock |
| ControlDarkDark |— Okno karty po przeniesieniu fokusu wybrany dokument |
| ControlLight |-Obramowanie karty autoukrywanie<br />— Obramowanie pole kombi pola i listy rozwijanej listy<br />-Zadokować docelowej tło i obramowanie |
| ControlLightLight | -Wybrane, ukierunkowane tymczasowego obramowania |
| ControlText | — Pole kombi pola i listy rozwijanej listy glifów<br />— Tekst karta okna, usunięto zaznaczenie narzędzie |
| GrayText |-Pole kombi i listy rozwijanej wyłączone obramowania, symbol listy rozwijanej, tekst i tekst elementu menu<br />— Tekst menu wyłączone<br />— Tekst nagłówka "search options" kontrolki wyszukiwanie<br />— Separator sekcji kontrolek wyszukiwanie |
| Wyróżnij | — Wszystkie aktywowany i po naciśnięciu tła i krawędzie, z wyjątkiem kombi przycisk listy rozwijanej podstawy i dokumentu dobrze przepełnienie przycisk obramowanie pola<br />— Tło wybrany element |
| HighlightText | — Wszystkie wskaźnika i cieniowanie po naciśnięciu (tekst i symbole)<br />-Ukierunkowanych narzędzie okna i dokumentu kartę okna kontrolki pierwszego planu<br />-Obramowanie pasek tytułu okna narzędzia ukierunkowanych<br />-Ukierunkowanych, wybrane karcie tymczasowej pierwszego planu<br />— Dobrze dokumentu obramowania przycisku przepełnienia po wskazaniu wskaźnikiem, a następnie naciśnij klawisz<br />— Wybrana ikona obramowania|
| HotTrack | -Paska przewijania, tło przycisku przewijania i obramowanie przy naciśnięciu<br />-Paska przewijania symbolu strzałki przy naciśnięciu |
| InactiveCaption | -Nieaktywne IDE i okna rafted symbole przycisku po najechaniu wskaźnikiem<br />-Tło paska title IDE i rafted systemu windows<br />— Tło formantu wyszukiwania wyłączone |
| InactiveCaptionText | -Nieaktywne IDE i rafted systemu windows pierwszoplanowych paska tytułu (tekst i symbole)<br />-Nieaktywnego okna przyciski tło i obramowanie, po najechaniu wskaźnikiem<br />— Narzędzie po przeniesieniu fokusu okna przycisk Tło i obramowanie<br />— Wyłączono wyszukiwania kontrolki z pierwszego planu |
| Menu | — Tło menu Lista rozwijana<br />-Checked, jak i wyłączonych znacznik wyboru tła |
| MenuText | -Rozwijanego menu obramowanie<br />-Znacznikami wyboru<br />— Symbole menu<br />— Lista rozwijana tekst menu<br />— Wybrana ikona obramowania |
| Pasek przewijania | -Przewiń paska i Strzałka w tle, wszystkie stany — pasek przewijania |
| Okno | — Automatyczne ukrywanie karty tła<br />-Menu paska i polecenia tła Półka<br />-Po przeniesieniu fokusu lub wybrany dokument okna kartę Tło i obramowanie dokumentu, kartach otwartych i tymczasowego<br />— Tło paska tytułu okna narzędzia po przeniesieniu fokusu<br />-Narzędzie tło karta okna, zarówno zaznaczony i niezaznaczony |
| WindowFrame | — Środowisko IDE obramowanie |
| WindowText | — Automatyczne ukrywanie karty w pierwszym planie<br />-Wybranego narzędzia okna karty w pierwszym planie<br />— Karta w oknie dokumentu po przeniesieniu fokusu i pierwszego planu kartę tymczasowych po przeniesieniu fokusu lub niezaznaczony<br />-Drzewa widok domyślny kolor pierwszego planu i umieść kursor nad niezaznaczone glifów<br />— Obramowanie karty wybranego okna Narzędzie<br />-Paska przewijania tła przycisku przewijania, obramowania i symboli |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> Udostępnianie kolorów dla użytkowników końcowych

### <a name="overview"></a>Omówienie

Czasami warto umożliwiają użytkownikom końcowym należy dostosować interfejs użytkownika, takich jak podczas tworzenia edytora kodu lub powierzchni projektowej. Najczęstszym sposobem to polega na użyciu **narzędzia &gt; opcje** okna dialogowego. Chyba że wysoce specjalistycznych interfejsu użytkownika, który wymaga kontrolek specjalnych, do przedstawienia dostosowania najłatwiej za pośrednictwem **czcionki i kolory** stronie w obrębie **środowiska** części okna dialogowego. Dla każdego elementu, który należy udostępnić dostosowywania użytkownik może wybrać zmienić kolor pierwszego planu i kolor tła.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie pakietu VSPackage dla kolorów można dostosowywać

Pakietu VSPackage można kontrolować, czcionki i kolory za pomocą niestandardowych kategorii i wyświetlania elementów na stronie właściwości czcionki i kolory. Korzystając z tego mechanizmu, należy zaimplementować pakietów VSPackage [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interfejsu i jego skojarzone interfejsy.

W zasadzie mechanizm ten może służyć do modyfikowania wszystkich istniejących elementów ekranu i kategorie, zawierające je. Jednak nie ją stosować do modyfikowania kategorii edytora tekstu lub jego elementów wyświetlana. Aby uzyskać więcej informacji na temat kategorii Edytor tekstów, zobacz [czcionkę i kolor Przegląd](../font-and-color-overview.md).

Aby implementować niestandardowe kategorie lub wyświetlić elementy, pakietu VSPackage musi:

- **Tworzenie lub identyfikowanie kategorie w rejestrze.** Implementacja interfejsu środowiska IDE **czcionki i kolory** strona właściwości używa tych informacji do poprawnie zapytań dla usługi obsługi danej kategorii.

- **Tworzenie lub identyfikowanie grupy w rejestrze (opcjonalnie).** Może być przydatne do definiowania grupy, która reprezentuje sumę dwóch lub więcej kategorii. Grupa jest zdefiniowany, IDE automatycznie scala podkategorii i dystrybuuje wyświetlania elementów w obrębie grupy.

- **Implementowanie Obsługa środowiska IDE.**

- **Obsługa zmian czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub wskazać kategorii

Konstruowania specjalny typ wpisu rejestru kategorii `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` gdzie `<Category>` to niezlokalizowana nazwa kategorii.

Należy wypełnić rejestru za pomocą dwóch wartości:

| Nazwa | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikowania kategorii |
| Package | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorii |

 Usługa określone w rejestrze należy podać implementacja [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) odpowiedniej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub wskazać grupy

Konstruowania specjalny typ wpisu rejestru kategorii `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` gdzie `<group>` to niezlokalizowana Nazwa grupy.

Należy wypełnić rejestru za pomocą dwóch wartości:

| Nazwa | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikowania kategorii |
| Package | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorii |

Usługa określone w rejestrze należy podać implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

![Implementacja IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Implementacja interfejsu `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Obsługa środowiska IDE

Implementowanie [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), która zwraca [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfejsu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu środowiska IDE dla każdej kategorii lub grupa z podanym identyfikatorem GUID.

Dla każdej kategorii, obsługuje on pakietu VSPackage implementuje osobne wystąpienie [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfejsu.

Metody implementowane za pomocą [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) należy podać środowisko IDE z:

- Listy wyświetlania elementów w kategorii

- Lokalizowalne nazwy wyświetlania elementów

- Wyświetlanie informacji dla każdego elementu członkowskiego kategorii

> [!NOTE]
> Każdej kategorii musi zawierać co najmniej jeden element wyświetlania.

IDE używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs zdefiniowanie sumę kilka kategorii.

Jego implementacja zapewnia środowisko IDE z:

- Lista kategorii, które tworzą daną grupę

- Dostęp do wystąpienia [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) Obsługa każdej kategorii, w grupie

- Nazwy grup Lokalizowalny

#### <a name="updating-the-ide"></a>Aktualizowanie środowiska IDE

IDE buforuje informacje o ustawieniach czcionek i kolorów. Dlatego po każdej modyfikacji konfiguracji środowiska IDE czcionek i kolorów, zapewnia, że pamięć podręczna jest aktualne jest najlepszym rozwiązaniem.

Aktualizowanie pamięci podręcznej odbywa się za pośrednictwem [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfejs i mogą być wykonywane globalnie lub tylko na wybranych elementów.

### <a name="handling-font-and-color-changes"></a>Obsługa zmian czcionek i kolorów

Aby prawidłowo obsługiwać kolorowanie tekst, który wyświetla pakietu VSPackage, usługa kolorowanie obsługi pakietu VSPackage musi odpowiedzieć na zainicjowanego przez użytkownika zmian za pomocą strony właściwości czcionki i kolory.

Aby to zrobić, pakietu VSPackage musi:

- **Obsługa zdarzenia generowane przez środowisko IDE** implementując [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interfejsu. IDE wywołuje odpowiednią metodę następujące modyfikacje użytkownika strony czcionek i kolorów. Na przykład wywołuje [onfontchanged —](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metody, jeśli wybrano opcję nowego czcionki.

  **OR**

- **sondowanie środowisko IDE dla zmian**. Można to zrobić za pomocą systemu zaimplementowane [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfejsu. Mimo że przede wszystkim do obsługi trwałości, [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metody można uzyskać informacji czcionek i kolorów dla elementów wyświetlana. Aby uzyskać więcej informacji na temat ustawienia czcionek i kolorów, zobacz artykuł w witrynie MSDN [uzyskiwania dostępu do przechowywanych czcionkę i ustawienia kolorów](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Aby upewnić się, że sondowania wyników są poprawne, należy użyć [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfejs do ustalenia, czy potrzebne przed wywołaniem metody pobierania czyszczenie pamięci podręcznej i zaktualizuj [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfejsu.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie niestandardowych czcionek i kolorów kategorii bez implementacji interfejsów

Poniższy przykład kodu pokazuje, jak się zarejestrować niestandardowych czcionek i kolorów kategorii bez implementacji interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

W tym przykładzie kodu:

- `"NameID"` Identyfikator zasobu Nazwa zlokalizowanej kategorii w pakiecie =
- `"ToolWindowPackage"` = Identyfikator GUID pakietu
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` jest tylko przykładowe i rzeczywista wartość może być udostępniane przez implementujący nowego identyfikatora GUID.

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
