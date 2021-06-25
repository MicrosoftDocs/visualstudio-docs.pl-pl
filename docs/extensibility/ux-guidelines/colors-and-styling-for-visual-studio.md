---
title: Kolory i style Visual Studio | Microsoft Docs
description: Dowiedz się, Visual Studio środowisko użytkownika używa koloru jako narzędzia do komunikacji, a nie ze względów czystego wyglądu.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904490"
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio

## <a name="use-color-in-visual-studio"></a>Używanie koloru w Visual Studio

W Visual Studio kolor jest używany głównie jako narzędzie do komunikacji, a nie tylko jako dekoracja. Użyj koloru minimalnie i zarezerwuj go w sytuacjach, w których chcesz:

- Komunikowanie znaczenia lub przynależności (na przykład modyfikatorów platformy lub języka)

- Przyciąganie uwagi (na przykład wskazanie zmiany stanu)

- Popraw czytelność i udostępnij punkty orientacyjne nawigowania po interfejsie użytkownika

- Zwiększenie użyteczności

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w Visual Studio. Czasami może być trudno ustalić, której opcji użyć lub jak jej używać prawidłowo. Ten temat pomoże Ci:

- Poznaj różne usługi i systemy używane do definiowania kolorów w Visual Studio.

- Wybierz poprawną opcję dla danego elementu.

- Poprawnie użyj wybranej opcji.

> [!NOTE]
> Nigdy nie należy kodować kolorów hex, RGB ani systemowych do elementów interfejsu użytkownika. Korzystanie z usług zapewnia elastyczność dostrajania aplikacji Hue. Ponadto bez usługi nie będzie można korzystać z możliwości przełączania motywów usługi [VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metody przypisywania kolorów do Visual Studio elementów interfejsu

Wybierz metodę najlepiej dostosowaną do twoich elementów interfejsu użytkownika.

| Interfejs użytkownika | Metoda | Jakie? |
| --- | --- | --- |
| Masz osadzone lub autonomiczne okna dialogowe. | **Kolory systemowe** | Nazwy systemów, które umożliwiają systemowi operacyjnej definiowanie koloru i wyglądu elementów interfejsu użytkownika, takich jak typowe kontrolki okna dialogowego. |
| Masz niestandardowy interfejs użytkownika, który ma być spójny z ogólnym środowiskiem programu VS, i masz elementy interfejsu użytkownika, które pasują do kategorii i semantycznego znaczenia tokenów udostępnionych. | **Wspólne kolory udostępnione** | Istniejące wstępnie zdefiniowane nazwy tokenów kolorów dla określonych elementów interfejsu użytkownika |
| Masz pojedynczą cechę lub grupę funkcji i nie ma współużytkowania koloru dla podobnych elementów. | **Kolory niestandardowe** | Nazwy tokenów kolorów, które są specyficzne dla obszaru i nie są przeznaczone do współużytkowania z innym interfejsem użytkownika |
| Chcesz zezwolić użytkownikowi końcowego na dostosowywanie interfejsu użytkownika lub zawartości (na przykład w przypadku edytorów tekstów lub wyspecjalizowanych okien projektanta). | **Dostosowywanie przez użytkownika końcowego**<br /><br />**(Narzędzia &gt; Okno dialogowe Opcje)** | Ustawienia zdefiniowane na stronie "Czcionki i **&gt;** kolory" okna dialogowego Opcje narzędzi lub wyspecjalizowana strona specyficzna dla jednej funkcji interfejsu użytkownika. |

### <a name="visual-studio-themes"></a>Visual Studio motywów

Visual Studio trzy różne motywy kolorów: jasny, ciemny i niebieski. Wykrywa również tryb duży kontrast, który jest motywem kolorów dla całego systemu zaprojektowanym z myślą o ułatwieniach dostępu.

Użytkownicy są monitowany o wybranie motywu podczas pierwszego użycia motywu z systemu Visual Studio i mogą później przełączyć motywy, przechodząc do pozycji Ogólne środowisko opcji narzędzi i wybierając nowy motyw z menu rozwijanego "motyw kolorów". **&gt; &gt; &gt;**

Użytkownicy mogą również używać Panel sterowania, aby przełączać całe systemy do jednego z duży kontrast motywów. Jeśli użytkownik wybierze motyw duży kontrast, selektor motywu kolorów Visual Studio nie ma już wpływu na kolory w programie Visual Studio, mimo że wszelkie zmiany motywu są zapisywane, gdy użytkownik zakończy pracę duży kontrast trybie. Aby uzyskać więcej informacji na duży kontrast trybie, zobacz [Choosing duży kontrast colors (Wybieranie duży kontrast kolorów).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>Usługa VSColor

Visual Studio udostępnia usługę kolorów środowiska, znaną jako usługa VSColor, która umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika z nazwanym wpisem zawierającym wartości kolorów dla każdego Visual Studio motywu. Dzięki temu kolory będą automatycznie zmieniane w celu odzwierciedlenia bieżącego motywu lub trybu duży kontrast użytkownika. Korzystanie z usługi oznacza, że implementacja wszystkich zmian kolorów związanych z motywem jest obsługiwane w jednym miejscu, a jeśli używasz wspólnych kolorów udostępnionych z usługi, interfejs użytkownika będzie automatycznie odzwierciedlać nowe motywy w przyszłych wersjach Visual Studio.

### <a name="implementation"></a>Implementacja

Kod Visual Studio zawiera kilka plików definicji pakietu, które zawierają listy nazw tokenów i odpowiednie wartości kolorów dla każdego motywu. Usługa kolorów odczytuje kolory VSColor zdefiniowane w tych plikach definicji pakietu. Te kolory są przywołyowane w znacznikach XAML lub w kodzie, a następnie ładowane za pośrednictwem metody `IVsUIShell5.GetThemedColor` lub mapowania DynamicResource.

### <a name="system-colors"></a>Kolory systemowe

Typowe kontrolki domyślnie odwołują się do kolorów systemowych. Jeśli chcesz, aby interfejs użytkownika używał kolorów systemowych, takich jak podczas tworzenia osadzonego lub autonomicznego okna dialogowego, nie musisz nic robić.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Wspólne kolory udostępnione w usłudze VSColor

Elementy interfejsu powinny odzwierciedlać ogólny Visual Studio danych. Ponownie korzystając ze wspólnych kolorów odpowiednich dla projektowego składnika interfejsu użytkownika, zapewniasz spójność interfejsu z innymi interfejsami usługi Visual Studio oraz że kolory będą aktualizowane automatycznie po dodaniu lub zaktualizowaniu motywów.

Przed użyciem wspólnych kolorów upewnij się, że rozumiesz, jak ich używać prawidłowo. Nieprawidłowe użycie wspólnych kolorów może spowodować niespójne, frustrujące lub mylące środowisko dla użytkowników.

### <a name="user-customizable-colors"></a>Kolory dostosowywane przez użytkownika

Zobacz: [Udostępnianie kolorów użytkownikom końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami trzeba zezwolić użytkownikowi końcowego na dostosowywanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Dostosowywalne składniki interfejsu użytkownika znajdują się **w &gt;** sekcji **Czcionki** i kolory okna dialogowego Opcje narzędzi, w którym użytkownicy mogą zmieniać kolor pierwszego planu, kolor tła lub oba te elementy.

![Okno &gt; dialogowe Opcje narzędzi](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Okno &gt; dialogowe Opcje narzędzi

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Usługa VSColor

Visual Studio udostępnia usługę kolorów środowiska, nazywaną również usługą VSColor lub usługą kolorów powłoki. Ta usługa umożliwia powiązanie wartości kolorów elementów interfejsu użytkownika z zestawem kolorów nazwa-wartość zawierającym kolory dla każdego motywu. Usługa VSColor musi być używana dla wszystkich elementów interfejsu użytkownika, aby kolory automatycznie zmieniały się w celu odzwierciedlenia bieżącego motywu wybranego przez użytkownika. Dzięki czemu interfejs użytkownika powiązany z usługą kolorów środowiska będzie integrować się z nowymi motywami w przyszłych wersjach Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa

Usługa kolorów środowiska odczytuje elementy VSColor zdefiniowane w pkgdef składnika interfejsu użytkownika. Te kolory VSColor są następnie przywołyowane w znacznikach XAML lub kodzie i są ładowane za pośrednictwem `IVsUIShell5.GetThemedColor` mapowania `DynamicResource` lub .

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

Istnieje kilka różnych sposobów uzyskiwania dostępu do usługi VSColor w zależności od rodzaju używanych tokenów kolorów i rodzaju kodu.

#### <a name="predefined-environment-colors"></a>Wstępnie zdefiniowane kolory środowiska

##### <a name="from-native-code"></a>Z kodu natywnego

Powłoka udostępnia usługę, która zapewnia dostęp `COLORREF` do kolorów. Usługa/interfejs to:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80.idl wyliczenie ma `__VSSYSCOLOREX` stałe koloru powłoki. Aby go użyć, przekaż jako wartość indeksu jedną z wartości z dokumentu w witrynie MSDN lub zwykły numer indeksu akceptowany przez `enum __VSSYSCOLOREX` systemowy interfejs API systemu `GetSysColor` Windows. W ten sposób jest wróci wartość RGB koloru, który powinien być używany w drugim parametrze.

Jeśli przechowujesz pióro lub pędzl z nowym kolorem, musisz (poza powłoką Visual Studio) i nasłuchiwać `AdviseBroadcastMessages` `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` komunikatów i .

Aby uzyskać dostęp do usługi kolorów w kodzie natywnym, należy wykonać wywołanie podobne do tego:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Wartości `COLORREF` zwracane przez element `GetVSSysColorEx()` zawierają tylko składniki R,G,B koloru motywu. Jeśli wpis motywu używa przezroczystości, wartość kanału alfa jest odrzucana przed zwróceniem. W związku z tym, jeśli kolor środowiska musi być używany w miejscu, w którym kanał przezroczystości jest ważny, należy użyć zamiast , zgodnie z opisem w dalszej `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` części tego tematu.

##### <a name="from-managed-code"></a>Z kodu zarządzanego

Uzyskiwanie dostępu do usługi VSColor za pomocą kodu natywnego jest dość proste. Jeśli jednak pracujesz za pomocą kodu zarządzanego, określenie sposobu korzystania z usługi może być trudne. Pamiętając o tym, oto fragment kodu w języku C#, który demonstruje ten proces:

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

Z kolorami Visual Studio można powiązać za pomocą wartości wyeksportowanych do pliku aplikacji `ResourceDictionary` . Poniżej znajduje się przykład użycia zasobów z tabeli kolorów oraz powiązania z danymi czcionek środowiska w języku XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Klasy pomocników i metody dla kodu zarządzanego

W przypadku kodu zarządzanego biblioteka Managed Package Framework () powłoki zawiera kilka klas pomocników ułatwiających korzystanie `Microsoft.VisualStudio.Shell.12.0.dll` z kolorów o tematach.

Metody pomocnika w klasie `Microsoft.VisualStudio.Shell.VsColors` w pliku MPF obejmują `GetThemedGDIColor()` metody i `GetThemedWPFColor()` . Te metody pomocnika zwracają wartość koloru wpisu motywu jako lub , która ma być `System.Drawing.Color` `System.Windows.Media.Color` używana w winForms lub interfejsie użytkownika WPF.

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

Klasa może również służyć do uzyskiwania identyfikatorów VSCOLOR dla danego klucza zasobu koloru WPF lub na odwrót.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody klasy `VsColors` odpytują usługę VSColor w celu zwrócenia wartości koloru za każdym razem, gdy są wywoływane. Aby uzyskać wartość koloru jako , alternatywą dla lepszej wydajności jest użycie metod klasy , która buforuje wartości kolorów uzyskane z `System.Drawing.Color` `Microsoft.VisualStudio.PlatformUI.VSThemeColor` usługi VSColor. Klasa subskrybuje wewnętrznie zdarzenia emisji komunikatów powłoki i odrzuca buforowane wartości, gdy wystąpi zdarzenie zmieniające motyw. Ponadto klasa udostępnia klasę . Zdarzenie przyjazne dla sieci, które subskrybuje zmiany motywu. Użyj zdarzenia , aby dodać nową obsługę, i użyj metody , `ThemeChanged` aby uzyskać wartości kolorów dla `GetThemedColor()` `ThemeResourceKeys` zainteresowania. Przykładowy kod może wyglądać tak:

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

System Windows używa kilku motywów na poziomie systemu o wysokim kontraście, które zwiększają kontrast kolorów tekstu, tła i obrazów, dzięki czemu elementy są bardziej odrębne na ekranie. Ze względu na ułatwienia dostępu ważne jest, aby Visual Studio interfejsu użytkownika odpowiadały prawidłowo, gdy użytkownicy przejdą do duży kontrast motywu.

Tylko kilka kolorów systemowych może służyć do duży kontrast motywów. Podczas wybierania nazw kolorów systemu pamiętaj o następujących wskazówkach:

- **Wybierz kolory systemowe, które mają takie samo znaczenie semantyczne** jak kolorowanie elementu. Jeśli na przykład wybierasz kolor o dużym kontraście dla tekstu w oknie, użyj wartości WindowText, a nie ControlText.

- **Wybierz pary pierwszego planu/tła** ze sobą lub nie będziesz mieć pewności, że twój wybór kolorów będzie działać we wszystkich duży kontrast motywach.

- Ustal, które części interfejsu użytkownika są najważniejsze, i upewnij **się, że obszary zawartości wyróżnią się.** Utracisz wiele szczegółów, które zwykle odróżniałyby subtelne różnice w odcieniach kolorów, dlatego używanie silnych kolorów obramowania jest typowe w przypadku definiowania obszarów zawartości, ponieważ nie ma żadnych wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Systemowy zestaw kolorów

Tabela w blogu [zespołu WPF: SystemColors Reference (Blog zespołu WPF: Odwołanie](/archive/blogs/wpf/systemcolors-reference) do kolorów systemu) wskazuje pełny zestaw nazw kolorów systemu i odpowiednie kolory wyświetlane w każdym motywie.

Podczas stosowania tego ograniczonego zestawu kolorów do interfejsu użytkownika oczekuje się, że utracisz subtelne szczegóły, które były obecne w *"normalnych" motywach*. Oto przykład interfejsu użytkownika z subtelnymi szarymi kolorami, które są używane do rozróżniania obszarów w oknie narzędzi. Po sparowaniu z tym samym oknem wyświetlanym w trybie duży kontrast można zobaczyć, że wszystkie tła są takie same, a granice tych obszarów są wskazywane za pomocą samego obramowania:

![Przykład tego, jak drobne szczegóły są utracone w duży kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Przykład tego, jak drobne szczegóły są utracone w duży kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Wybieranie kolorów tekstu w edytorze

Tekst pokolorowany jest używany w edytorze lub na powierzchni projektowej w celu wskazania znaczenia, takiego jak umożliwienie łatwej identyfikacji grup podobnych elementów. Jednak w duży kontrast motywie tekstowym nie ma możliwości rozróżnienia między więcej niż trzema kolorami tekstu. WindowText, GrayText i HotTrackText to jedyne kolory dostępne na powierzchni WindowBackground. Ponieważ nie można używać więcej niż trzech kolorów, starannie wybierz najważniejsze różnice, które mają być wyświetlane w trybie duży kontrast trybie.

Hues dla każdej nazwy tokenu dozwolone na powierzchni edytora, jak są one wyświetlane w duży kontrast motywu:

![duży kontrast porównanie edytora](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />duży kontrast porównanie edytora

Przykłady powierzchni edytora w motywie Niebieski:

![Edytor w niebieskim motywie](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Edytor w niebieskim motywie

![Edytor w duży kontrast #1 motywu](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Edytor w duży kontrast #1 motywu

### <a name="usage-patterns"></a>Wzorce użycia

Wiele typowych elementów interfejsu użytkownika ma duży kontrast zdefiniowane kolory. Możesz odwoływać się do tych wzorców użycia podczas wybierania własnych nazw kolorów systemu, aby elementy interfejsu użytkownika były spójne z podobnymi składnikami.

| Kolor systemu | Użycie |
| --- | --- |
| ActiveCaption | — Aktywne środowiska IDE i przycisk kreślony okna po najechaniu kursorem i naciśnięciu klawisza<br />— Tło paska tytułu dla środowiska IDE i okien wytłaczonych<br />- Domyślne tło paska stanu |
| ActiveCaptionText | — Aktywne środowiska IDE i okna wytłaczone dla pierwszego planu paska tytułu (tekst i glify)<br />— Tło i obramowanie aktywnych przycisków okna po najechaniu kursorem i naciśnięciu klawisza |
| Kontrola | - Pole kombi, lista rozwijana i kontrolka wyszukiwania — domyślne i wyłączone tło, w tym przycisk listy rozwijanej<br />— Tło przycisku Dokowania docelowego<br />- Tło paska poleceń<br />— Tło okna narzędzi |
| ControlDark | — tło środowiska IDE<br />- Separatory paska menu i poleceń<br />- Obramowanie paska poleceń<br />- Cienie menu<br />- Domyślna karta okna narzędzi oraz obramowanie i separator wskaźnika myszy<br />— Tło przycisku Przepełnienie dobrze udokumentowanych dokumentów<br />- Dokowanie docelowego obramowania glifów |
| ControlDarkDark |— Okno karty wybranego dokumentu bez koncentracji |
| Kontrolka |- Automatyczne ukrywanie obramowania karty<br />- Pole kombi i obramowanie listy rozwijanej<br />— Tło i obramowanie obiektu docelowego Docka |
| KontrolkaLightLight | - Wybrane, ukierunkowane obramowanie tymczasowe |
| ControlText | - Glif pola kombi i listy rozwijanej<br />- Tekst niezaznajdanych kart w oknie narzędzi |
| GrayText |- Pole kombi i lista rozwijana wyłączone obramowanie, glif listy rozwijanej, tekst i tekst elementu menu<br />- Tekst menu wyłączone<br />- Tekst nagłówka kontrolki wyszukiwania "opcje wyszukiwania"<br />- Separator sekcji kontrolki wyszukiwania |
| Wyróżnij | — Wszystkie najeżdżane kursorem tła i obramowania, z wyjątkiem tła przycisku listy rozwijanej pola kombi i obramowania przycisku przepełnienia dokumentu<br />- Tła wybranego elementu |
| HighlightText | — Wszystkie najechane kursorem i naciśnięte pierwszego planu (tekst i glify)<br />- Okno narzędzi z ukierunkowaną kontrolą i kontrolką okna karty dokumentu na pierwszym planie<br />- Ukierunkowane obramowanie paska tytułu okna narzędzi<br />- Skoncentrowane, wybrane tabulatory na pierwszym planie<br />- Dokumentuj dobrze przepełnione obramowanie przycisku po najechaniu kursorem i naciśnięciu<br />- Wybrane obramowanie ikony|
| HotTrack | — Tło i obramowanie na pasku przewijania na naciśnięciu<br />— po naciśnięciu klawisza glyph ze strzałką paska przewijania |
| InactiveCaption | - Nieaktywne idee i przycisk z wykreślaną oknie po zatrzymaniu wskaźnika myszy<br />— Tło paska tytułu dla środowiska IDE i okien wytłaczonych<br />- Wyłączone tło kontrolki wyszukiwania |
| InactiveCaptionText | — Nieaktywne idee i wytłaczony pasek tytułu systemu Windows na pierwszym planie (tekst i glify)<br />— Nieaktywne tło i obramowanie przycisków okna po najechaniu kursorem<br />— Tło i obramowanie przycisku okna narzędzi bez koncentracji<br />- Wyłączono kontrolkę wyszukiwania na pierwszym planie |
| Menu | - Tło menu rozwijanego<br />— Zaznaczone i wyłączone tło znacznika wyboru |
| Tekst Menu | - Obramowanie menu rozwijanego<br />- Znaczniki wyboru<br />- Menu glyphs (Glify menu)<br />- Tekst menu rozwijanego<br />- Wybrane obramowanie ikony |
| Scrollbar | - Pasek przewijania i strzałka paska przewijania tło, wszystkie stany |
| Okno | — Automatyczne ukrywanie tła karty<br />- Pasek menu i tło na półce polecenia<br />— Tło karty okna dokumentu bez koncentracji lub niezaznaone i obramowanie dokumentu, zarówno w przypadku kart otwartych, jak i kart granicznych<br />— Tło paska tytułu okna narzędzi bez koncentracji<br />- Tło karty okna narzędzi, zarówno zaznaczone, jak i niezaznakcjonowane |
| WindowFrame | — obramowanie środowiska IDE |
| WindowText (Tekst okna) | — Automatyczne ukrywanie na pierwszym planie karty<br />- Pierwszy plan karty wybranego okna narzędzi<br />— Karta okna dokumentu bez koncentracji i bez koncentracji lub niewyznana na pierwszym planie karty<br />- Widok drzewa domyślny pierwszy plan i umieść kursor nad niezaznakanym glyph<br />- Obramowanie wybranej karty okna narzędzi<br />— Tło, obramowanie i glif na pasku przewijania |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Udostępnianie kolorów użytkownikom końcowych

### <a name="overview"></a>Omówienie

Czasami trzeba zezwolić użytkownikowi końcowego na dostosowywanie interfejsu użytkownika, na przykład podczas tworzenia edytora kodu lub powierzchni projektowej. Najpowszechniejszym sposobem na to jest użycie okna **dialogowego &gt; Opcje** narzędzi. Jeśli nie masz wysoce wyspecjalizowanego interfejsu użytkownika wymagającego specjalnych kontrolek, najprostszym  sposobem przedstawienia dostosowania jest strona **Czcionki** i kolory w sekcji Środowisko okna dialogowego. Dla każdego elementu uwidocznianego do dostosowania użytkownik może zmienić kolor pierwszego planu, kolor tła lub oba te elementy.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie pakietów VSPackage dla dostosowywalnych kolorów

Pakiet VSPackage może kontrolować czcionki i kolory za pomocą niestandardowych kategorii i wyświetlać elementy na stronie właściwości Czcionki i kolory. W przypadku korzystania z tego mechanizmu pakiet VSPackages musi implementować interfejs [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) i skojarzone z nim interfejsy.

W zasadzie ten mechanizm może służyć do modyfikowania wszystkich istniejących elementów wyświetlanych i kategorii, które je zawierają. Nie należy go jednak używać do modyfikowania kategorii Edytor tekstu ani jej elementów wyświetlanych. Aby uzyskać więcej informacji na temat kategorii Edytor tekstu, zobacz [Font and Color Overview (Omówienie czcionek i kolorów).](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

Aby zaimplementować kategorie niestandardowe lub wyświetlić elementy, pakiet VSPackage musi:

- **Utwórz lub zidentyfikuj kategorie w rejestrze.** Implementacja strony właściwości **Czcionki** i kolory w środowiskach IDE używa tych informacji do poprawnego wykonywania zapytań o usługę obsługową danej kategorii.

- **Utwórz lub zidentyfikuj grupy w rejestrze (opcjonalnie).** Przydatne może być zdefiniowanie grupy, która reprezentuje związek co najmniej dwóch kategorii. Jeśli grupa jest zdefiniowana, IDE automatycznie scala podkategorii i dystrybuuje wyświetlane elementy w grupie.

- **Implementowanie obsługi środowiska IDE.**

- **Obsługa zmian czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub zidentyfikować kategorie

Skonstruuj specjalny typ wpisu rejestru kategorii w obszarze gdzie jest niezmienianą `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` nazwą `<Category>` kategorii.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | GUID | Identyfikator GUID usługi VSPackage obsługującej kategorię |

 Usługa określona w rejestrze musi zapewnić implementację [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) dla odpowiedniej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub zidentyfikować grupy

Skonstruuj specjalny typ wpisu rejestru kategorii, `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` w obszarze gdzie jest `<group>` niezmiejscową nazwą grupy.

Wypełnij rejestr dwiema wartościami:

| Nazwa | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | GUID | Identyfikator GUID utworzony w celu zidentyfikowania kategorii |
| Pakiet | REG_SZ | GUID | Identyfikator GUID usługi VSPackage obsługującej kategorię |

Usługa określona w rejestrze musi zapewniać implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

![Implementacja IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementacja programu `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Aby zaimplementować obsługę środowiska IDE

[Zaimportuj element GetObject,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)który zwraca interfejs [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) lub interfejs do środowiska IDE dla każdej podanej kategorii <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> lub identyfikatora GUID grupy.

Dla każdej obsługującej go kategorii pakiet VSPackage implementuje oddzielne wystąpienie [interfejsu IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Metody implementowane za [pośrednictwem IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) muszą zapewniać w idee:

- Listy elementów wyświetlanych w kategorii

- Zlokalizowane nazwy elementów wyświetlanych

- Wyświetlanie informacji dla każdego członka kategorii

> [!NOTE]
> Każda kategoria musi zawierać co najmniej jeden element wyświetlania.

Ide używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu do definiowania unii kilku kategorii.

Jego implementacja zapewnia idee z:

- Lista kategorii, które należy do danej grupy

- Dostęp do wystąpień [IVsFontAndColorDefaults,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) które obsługują każdą kategorię w grupie

- Nazwy grup, które można zlokalizowane

#### <a name="updating-the-ide"></a>Aktualizowanie środowiska IDE

Ide buforuje informacje o ustawieniach czcionek i kolorów. Dlatego po każdej modyfikacji konfiguracji czcionek i kolorów środowiska IDE najlepszym rozwiązaniem jest upewnienie się, że pamięć podręczna jest aktualne.

Aktualizowanie pamięci podręcznej odbywa się za pośrednictwem [interfejsu IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) i może być wykonywane globalnie lub tylko na wybranych elementach.

### <a name="handling-font-and-color-changes"></a>Obsługa zmian czcionek i kolorów

Aby prawidłowo obsługiwać kolorowanie tekstu wyświetlanego przez pakiet VSPackage, usługa kolorowania obsługująca pakiet VSPackage musi odpowiadać na zmiany inicjowane przez użytkownika wprowadzone za pośrednictwem strony właściwości Czcionki i kolory.

W tym celu pakiet VSPackage musi:

- **obsługa zdarzeń generowanych przez ideę** przez zaimplementowanie [interfejsu IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) Ide wywołuje odpowiednią metodę po modyfikacji strony Czcionki i kolory przez użytkownika. Na przykład wywołuje metodę [OnFontChanged,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) jeśli wybrano nową czcionkę.

  **OR**

- **Sonduj ideę pod celu zmiany.** Można to zrobić za pomocą interfejsu [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) zaimplementowanego przez system. Mimo że metoda [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) służy głównie do obsługi trwałości, można uzyskać informacje o czcionkach i kolorach elementów wyświetlanych. Aby uzyskać więcej informacji na temat ustawień czcionek i kolorów, zobacz artykuł MSDN Accessing Stored Font and Color Settings (Uzyskiwanie dostępu do przechowywanych ustawień [czcionek i kolorów).](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)

> [!NOTE]
> Aby upewnić się, że wyniki sondowania są poprawne, użyj interfejsu [IVsFontAndColorCacheManager,](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) aby określić, czy przed wywołaniem metod pobierania interfejsu [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) potrzebna jest opróżnienie i aktualizacja pamięci podręcznej.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie niestandardowej czcionki i kategorii kolorów bez implementowania interfejsów

Poniższy przykład kodu pokazuje, jak zarejestrować niestandardową czcionkę i kolor Category bez implementowania interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

W tym przykładzie kodu:

- `"NameID"` = identyfikator zasobu zlokalizowanej nazwy kategorii w pakiecie
- `"ToolWindowPackage"` = identyfikator GUID pakietu
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` to tylko przykład, a rzeczywista wartość może być nowym identyfikatorem GUID dostarczonym przez implementatora.

### <a name="set-the-font-and-color-property-category-guid"></a>Ustawianie identyfikatora GUID kategorii właściwości Czcionka i Kolor

W poniższym przykładzie kodu pokazano ustawianie identyfikatorów GUID kategorii.

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
