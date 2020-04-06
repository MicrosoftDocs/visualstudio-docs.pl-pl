---
title: Czcionki i formatowanie programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf1550026fb5c9d9395d931f21d48bc4739ea8c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698579"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Czcionka środowiskowa
 Wszystkie czcionki w programie Visual Studio muszą być udostępniane użytkownikowi w celu dostosowania. Odbywa się to przede wszystkim za pośrednictwem strony **Czcionki i kolory** w oknie dialogowym **Narzędzia > Opcje.** Trzy główne kategorie ustawień czcionek to:

- **Czcionka środowiska** — czcionka podstawowa dla IDE (zintegrowane środowisko programistyczne), używana dla wszystkich elementów interfejsu, w tym okien dialogowych, menu, okien narzędzi i okien dokumentów. Domyślnie czcionka środowiska jest powiązana z czcionką systemową, która pojawia się jako interfejs użytkownika Segoe 9 pkt w bieżących wersjach systemu Windows. Użycie jednej czcionki dla wszystkich elementów interfejsu pomaga zapewnić spójny wygląd czcionki w całej idei.

- **Edytor tekstu** - elementy, które pojawiają się w kodzie i innych edytorach tekstowych można dostosować na stronie Edytor tekstu w **narzędzia > opcje**.

- **Określone kolekcje** — okna projektanta, które oferują użytkownikowi dostosowanie elementów interfejsu, mogą uwidaczniać czcionki specyficzne dla ich powierzchni projektowej na ich własnej stronie ustawień w **narzędzia > Opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie i zmiana rozmiaru czcionki edytora
 Użytkownicy często powiększają lub powiększają rozmiar i/lub kolor tekstu w edytorze zgodnie z ich preferencjami, niezależnie od ogólnego interfejsu użytkownika. Ponieważ czcionka środowiska jest używana na elementach, które mogą pojawić się w edytorze/projektancie lub jako część, należy zwrócić uwagę na oczekiwane zachowanie po zmianie jednej z tych klasyfikacji czcionek.

 Podczas tworzenia elementów interfejsu użytkownika, które pojawiają się w edytorze, ale nie są częścią *zawartości,* ważne jest, aby użyć czcionki środowiska, a nie czcionki tekstowej, tak aby elementy zmieniały rozmiar w przewidywalny sposób.

1. W przypadku tekstu kodu w edytorze, zmienić rozmiar z ustawieniem czcionki tekstu kodu i odpowiedzieć na poziom powiększenia tekstu edytora.

2. Wszystkie inne elementy interfejsu powinny być powiązane z ustawieniem czcionki środowiska i reagować na wszelkie globalne zmiany w środowisku. Obejmuje to (ale nie ogranicza się do):

    - Tekst w menu kontekstowych

    - Tekst w ozdobach edytora, takich jak tekst menu żarówki, szybkie znajdowanie okienka edytora i przechodzenie do okienka

    - Etykietuj tekst w oknach dialogowych, takich jak **Znajdź w plikach** lub **Refaktoryzator**

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionki środowiskowej
 W kodzie natywnym lub WinForms czcionki środowiska `IUIHostLocale::GetDialogFont` można uzyskać dostęp, `SID_SUIHostLocale` wywołując metodę po kwerendzie interfejsu z usługi.

 Dla programu Windows Presentation Foundation (WPF) należy wyprowadzić `DialogWindow` klasę okna dialogowego `Window` z klasy powłoki zamiast klasy WPF.

 W języku XAML kod wygląda następująco:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Kod za:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Zastąp `Microsoft.VisualStudio.Shell.11.0` bieżącą wersją biblioteki DLL MPF).

 Aby wyświetlić okno`ShowModal()`dialogowe, zadzwoń `ShowDialog()`" " na klasę . `ShowModal()`ustawia prawidłowy stan modalny w powłoce, zapewnia, że okno dialogowe jest wyśrodkowane w oknie nadrzędnym i tak dalej.

 Kod jest następujący:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`zwraca bool? (nullable Boolean) `DialogResult`z , które mogą być używane w razie potrzeby. Zwracana wartość jest prawdziwa, jeśli okno dialogowe zostało zamknięte za pomocą **przycisku OK**.

 Jeśli chcesz wyświetlić niektóre WPF UI, który nie jest `HwndSource`dialogowy i jest obsługiwany w jego własnym , takich jak okno podręczne lub okno podrzędne WPF okna nadrzędnego Win32/WinForms, należy ustawić `FontFamily` i `FontSize` na element główny WPF elementu. (Powłoka ustawia właściwości w oknie głównym, ale nie będą `HWND`dziedziczone obok ). Powłoka zapewnia zasoby, z którymi właściwości mogą być powiązane, w ten sposób:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Odwołanie do formatowania (skalowanie/pogruszanie)
 Niektóre okna dialogowe wymagają pogrubienia określonego tekstu lub rozmiaru innego niż czcionka środowiskowa. Wcześniej czcionki większe niż czcionka środowiska były`environment font +2`kodowane jako " " lub podobne. Za pomocą podanych fragmentów kodu będzie obsługiwać monitory o wysokiej rozdzielczości DPI i upewnij się, że wyświetlany tekst zawsze pojawia się przy prawidłowym rozmiarze i wadze (np.

> [!NOTE]
> Przed zastosowaniem formatowania upewnij się, że postępujesz zgodnie ze wskazówkami znalezionymi w [stylu tekstowym](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Aby skalować czcionkę środowiska, ustaw styl TextBlock lub Label zgodnie ze wskazanymi. Każdy z tych fragmentów kodu, prawidłowo używany, wygeneruje poprawną czcionkę, w tym odpowiednie zmiany rozmiaru i wagi.

 Gdzie`vsui`" " jest odniesieniem `Microsoft.VisualStudio.Shell`do obszaru nazw:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>Czcionka środowiskowa 375% + światło

**Pojawia się jako:** 34 pkt Segoe UI Light

::: moniker range="vs-2017"

**Użyj dla:** (rzadkiego) unikalnego interfejsu użytkownika marki, na przykład na stronie startowej

::: moniker-end

::: moniker range=">=vs-2019"

**Zastosowanie dla:** (rzadki) unikalny, markowy interfejs użytkownika

::: moniker-end

**Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Ustaw styl textblock lub label, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>Czcionka 310% Środowiska + Światło
 **Pojawia się jako:** 28 pkt Segoe UI Light **Use for:** duże tytuły dialogowe podpisu, główny nagłówek w raportach

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>Czcionka 200% Środowiska + Semilight
 **Wygląda jako:** 18 pkt Segoe UI Semilight **Zastosowanie dla:** podpozycji, tytułów w małych i średnich oknach dialogowych

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>Czcionka środowiskowa 155%
 **Pojawia się jako:** 14 pkt Segoe UI **Użyj dla:** nagłówki sekcji w interfejsie użytkownika dokumentu lub raportach

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>Czcionka środowiskowa 133%
 **Pojawia się jako:** 12 pkt Segoe UI **Użyj dla:** mniejszych podpozycji w oknach dialogowych podpisu i dobrze dokumentuj interfejs użytkownika

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>Czcionka środowiskowa 122%
 **Wygląda jak:** 11 pkt Segoe UI **Użyj dla:** nagłówki sekcji w oknach dialogowych podpisu, górne węzły w widoku drzewa, nawigacja w pionie

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Czcionka środowiskowa + pogrubienie
 **Wygląda jak:** pogrubiony interfejs użytkownika Segoe 9 pkt **Użyj dla:** etykiet i podnagłów w oknach dialogowych podpisu, raportów i dobrze dokumentuj interfejs użytkownika

 **Kodeks proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowany `label` TextBlock i jest wcześniej zdefiniowane Etykieta:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Ustaw styl textblock lub label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Style lokalne
 W niektórych przypadkach lokalizatory będą musiały zmodyfikować style czcionek dla różnych ustawień regionalnych, takich jak usuwanie pogrubienia z tekstu dla języków wschodnioazjatyckich. Aby lokalizacja stylów czcionek była możliwa, style te muszą znajdować się w pliku .resx. Najlepszym sposobem, aby to osiągnąć i nadal edytować style czcionek w visual studio projektanta formularzy jest jawnie ustawić style czcionek w czasie projektowania. Mimo że tworzy to obiekt pełnej czcionki i może wydawać się przerwać dziedziczenie czcionek nadrzędnych, tylko FontStyle właściwość jest używana do ustawiania czcionki.

 Rozwiązaniem jest podłączyć `FontChanged` zdarzenie formularza okna dialogowego. W `FontChanged` przypadku, chodzić wszystkie formanty i sprawdzić, czy ich czcionka jest ustawiona. Jeśli jest ustawiona, zmień ją na nową czcionkę na podstawie czcionki formularza i poprzedniego stylu czcionki formantu. Przykładem tego w kodzie jest:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Za pomocą tego kodu gwarantuje, że po zaktualizowaniu czcionki formularza, czcionki formantów zostanie zaktualizowany, jak również. Ta metoda powinna być również wywoływana z konstruktora formularza, ponieważ `IUIService` okno `FontChanged` dialogowe może nie uzyskać wystąpienia i zdarzenie nigdy nie zostanie wywołane. Podłączanie `FontChanged` pozwoli okno dialogowe dynamicznie podnieść nową czcionkę, nawet jeśli okno dialogowe jest już otwarte.

### <a name="testing-the-environment-font"></a>Testowanie czcionki środowiskowej
 Aby upewnić się, że interfejs użytkownika używa czcionki środowiskowej i jest zgodny z ustawieniami rozmiaru, otwórz okno Opcje **> Narzędzia > środowisko > czcionki i kolory** i wybierz "Czcionka środowiska" w menu rozwijanym "Pokaż ustawienia dla:".

 ![Ustawienia czcionek i &gt; kolorów w oknie dialogowym Opcje narzędzi](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Ustawienia czcionek i &gt; kolorów w oknie dialogowym Opcje narzędzi

 Ustaw czcionkę na coś zupełnie innego niż domyślny. Aby było oczywiste, który interfejs użytkownika nie jest aktualizowany, wybierz czcionkę z szeryfami (np. Następnie przetestuj swój interfejs użytkownika, aby upewnić się, że szanuje środowisko. Oto przykład użycia okna dialogowego licencji:

 ![Przykład tekstu interfejsu użytkownika, który nie jest zgodny z czcionką środowiska](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Przykład tekstu interfejsu użytkownika, który nie jest zgodny z czcionką środowiska

 W takim przypadku "Informacje o użytkowniku" i "Informacje o produkcie" nie są zgodne z czcionką. W niektórych przypadkach może to być jawny wybór projektu, ale może to być błąd, jeśli jawna czcionka nie jest określona jako część specyfikacji redline.

 Aby zresetować czcionkę, kliknij przycisk "Użyj ustawień domyślnych" w obszarze **Narzędzia > Opcje > środowisko > czcionki i kolory**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Styl tekstu
 Styl tekstu odnosi się do rozmiaru czcionki, wagi i wielkości liter. Aby uzyskać wskazówki dotyczące implementacji, zobacz [Czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Wielkość liter w tekście

#### <a name="all-caps"></a>Wszystkie czapki
 Nie należy używać wszystkich wersalików dla tytułów lub etykiet w programie Visual Studio.

#### <a name="all-lowercase"></a>Wszystkie małe litery
 Nie należy używać wszystkich małych liter dla tytułów lub etykiet w programie Visual Studio.

#### <a name="sentence-and-title-case"></a>Wyrok i tytuł sprawy
 Tekst w programie Visual Studio należy użyć przypadku tytułu lub zdanie, w zależności od sytuacji.

|Przypadek tytułu należy użyć dla:|Użyj przypadku zdania dla:|
|-------------------------|----------------------------|
|Tytuły okien dialogowych|Etykiety|
|Pola grupowe|Pola wyboru|
|Elementy menu|Przycisków|
|Elementy menu kontekstowego|Elementy pola listy|
|Przyciski|Paski stanu|
|Etykiety tabel||
|Nagłówki kolumn||
|Etykietki narzędzi||

##### <a name="title-case"></a>Sprawa tytułowa
 Wielkość liter jest stylem, w którym pierwsze litery większości lub wszystkich wyrazów w frazie są pisane wielkimi literami. W programie Visual Studio przypadek tytułu jest używany dla wielu elementów, w tym:

- **Etykietki narzędzi.** Przykład: "Podgląd wybranych elementów"

- **Nagłówki kolumn.** Przykład: "Odpowiedź systemu"

- **Elementy menu.** Przykład: "Zapisz wszystko"

  W przypadku używania tytułu są to wytyczne dotyczące tego, kiedy używać wielkich liter i kiedy pozostawić je zasuwają małe litery:

|Wielkie litery|Komentarze i przykłady|
|---------------|---------------------------|
|Wszystkie rzeczowniki||
|Wszystkie zlecenia|W tym "Jest" i inne formy "być"|
|Wszystkie przysłówki|W tym "Niż" i "Kiedy"|
|Wszystkie przymiotniki|W tym "To" i "To"|
|Wszystkie zaimki|W tym zaborczy "Its", jak również "It's", skurcz zaimka "to" i czasownik "jest"|
|Pierwsze i ostatnie słowa, niezależnie od części mowy||
|Przyimki, które są częścią frazy czasownika|"Zamykanie wszystkich okien" lub "Zamykanie systemu"|
|Wszystkie litery akronimu|HTML, XML, URL, IDE, RGB|
|Drugie słowo w słowie złożonym, jeśli jest to rzeczownik lub właściwy przymiotnik, lub jeśli wyrazy mają taką samą wagę|Odsyłacz, Oprogramowanie przed microsoftem, dostęp do odczytu/zapisu, czas wykonywania|

|Małe litery|Przykłady|
|---------------|--------------|
|Drugie słowo w słowie złożonym, jeśli jest to inna część mowy lub imiesłów modyfikujący pierwsze słowo|Jak to zrobić, Start|
|Artykuły, chyba że jedno słowo jest pierwszym słowem w tytule|a, an, the|
|Spójniki współrzędnych|i, ale, ani, ani, lub|
|Przyimki ze słowami czterech lub mniej liter poza wyrażeniem czasownika|do, na, jak, z, na wierzchu|
|"Do" w przypadku użycia w bezokolicznikowej frazie|"Jak sformatować dysk twardy"|

##### <a name="sentence-case"></a>Sprawa zdania
 Przypadek zdania jest standardową metodą pisarską do pisania, w której tylko pierwsze słowo zdania jest pisanych kapitalikiem, wraz z właściwymi rzeczownikami i zaimkiem "I". Ogólnie rzecz biorąc, przypadek zdania jest łatwiejszy do odczytania przez odbiorców na całym świecie, zwłaszcza gdy zawartość zostanie przetłumaczona przez maszynę. Użyj przypadku zdania dla:

1. **Komunikaty na pasku stanu.** Są one proste, krótkie i zawierają tylko informacje o stanie. Przykład: "Ładowanie pliku projektu"

2. **Wszystkie inne elementy interfejsu użytkownika,** w tym etykiety, pola wyboru, przyciski radiowe i elementy pola listy. Przykład: "Zaznacz wszystkie elementy na liście"

### <a name="text-formatting"></a>Formatowanie tekstu
 Domyślne formatowanie tekstu w programie Visual Studio 2013 jest kontrolowane przez [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa pomaga zapewnić spójny wygląd czcionki w całym środowisku IDE (zintegrowane środowisko programistyczne) i należy go używać, aby zagwarantować spójne środowisko dla użytkowników.

 Domyślny rozmiar używany przez usługę czcionek programu Visual Studio pochodzi z systemu Windows i jest wyświetlany jako 9 pkt.

 Formatowanie można zastosować do czcionki środowiska. W tym temacie opisano, jak i gdzie używać stylów. Informacje o implementacji można znaleźć w [polu Czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Pogrubiony tekst
 Pogrubiony tekst jest używany oszczędnie w programie Visual Studio i powinien być zarezerwowany dla:

- etykiety pytań w kreatorach

- wyznaczanie aktywnego projektu w Eksploratorze rozwiązań

- zastąpione wartości w oknie narzędzia Właściwości

- niektóre zdarzenia na listach rozwijanych edytora Visual Basic

- zawartość wygenerowana przez serwer w konspekcie dokumentu dla stron internetowych

- nagłówki sekcji w złożonym oknie dialogowym lub w interfejsie użytkownika projektanta

#### <a name="italics"></a>Kursywa
 Visual Studio nie używa kursywy lub pogrubiony kursywy tekstu kursywy.

#### <a name="color"></a>Kolor

- Niebieski jest zarezerwowany dla hiperłączy (nawigacji i polecenia) i nigdy nie powinien być używany do orientacji.

- Większe nagłówki (czcionka środowiskowa x 155% lub większa) mogą być barwione do następujących celów:

  - Aby zapewnić atrakcyjność wizualną dla interfejsu użytkownika programu Visual Studio signature

  - Aby zwrócić uwagę na określony obszar

  - Aby zaoferować zwolnienie od standardowego ciemnoszarego / czarnego koloru tekstu środowiska

- Kolor w nagłówkach powinien wykorzystywać istniejące kolory marki Visual Studio, głównie główne fioletowe, #FF68217A.

- Podczas używania koloru w nagłówkach należy przestrzegać [wytycznych dotyczących kolorów systemu Windows,](/windows/desktop/uxguide/vis-color)w tym współczynnika kontrastu i innych zagadnień dotyczących ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Projekt interfejsu użytkownika programu Visual Studio ma jaśniejszy wygląd z większą liczącą odstępów. W miarę możliwości zmniejszono lub usunięto paski chromu i tytułu. Podczas gdy gęstość informacji jest wymagana w programie Visual Studio, typografia nadal jest ważna, z naciskiem na bardziej otwarte odstępy między wierszami i zróżnicowanie rozmiarów i wag czcionek.

 Poniższe tabele zawierają szczegóły projektu i przykłady wizualne dla czcionek wyświetlanych używanych w programie Visual Studio. Niektóre odmiany czcionek wyświetlania mają zarówno rozmiar, jak i wagę, takie jak Semilight lub Light, zakodowane w ich wyglądzie.

 Fragmenty kodu implementacji dla wszystkich czcionek wyświetlanych można znaleźć w [odwołaniu do formatowania (skalowanie/pogrubienie).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>Czcionka środowiskowa 375% + światło

|||
|-|-|
|**Zastosowanie:** Rzadko. Unikalny interfejs użytkownika marki tylko.<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj dla interfejsu użytkownika innego niż podpis ui, takich jak Strona początkowa<br />- Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 34 pkt Segoe UI Light<br /><br /> **Przykład wizualny:**<br /><br /> *Obecnie nie jest używany. Może być używany w visual studio 2017 Strona początkowa.*|

#### <a name="310-environment-font--light"></a>Czcionka 310% Środowiska + Światło

::: moniker range="vs-2017"

|||
|-|-|
|**Użycia:**<br /><br /> - Większy nagłówek w oknach dialogowych podpisu<br />- Nagłówek sprawozdania głównego<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj dla interfejsu użytkownika innego niż podpis ui, takich jak Strona początkowa<br />- Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 28 pkt Segoe UI Light<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki 310% środowiska &#43; nagłówek Światło](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Użycia:**<br /><br /> - Większy nagłówek w oknach dialogowych podpisu<br />- Nagłówek sprawozdania głównego<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj dla interfejsu użytkownika innego niż podpis interfejsu użytkownika<br />- Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 28 pkt Segoe UI Light<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki 310% środowiska &#43; nagłówek Światło](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>Czcionka 200% Środowiska + Semilight

|||
|-|-|
|**Użycia:**<br /><br /> - Podpozycje<br />- Tytuły w małych i średnich oknach dialogowych<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze stosować wagę Semilight<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 18 pkt Segoe UI Semillight<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki 200% Environment &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>Czcionka środowiskowa 155%

|||
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w dokumencie dobrze UI<br />- Raporty<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 14 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Czcionka środowiskowa 133%

|||
|-|-|
|**Użycia:**<br /><br /> - Mniejsze podpozycje w oknach dialogowych podpisu<br />- Mniejsze podpozycje w interfejsie użytkownika dobrze dokumentu<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 12 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Czcionka środowiskowa 122%

|||
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w oknach dialogowych podpisu<br />- Wierzchnie węzły w widoku drzewa<br />- Nawigacja w pionie<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 11 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Czcionka środowiskowa + pogrubienie

|||
|-|-|
|**Użycia:**<br /><br /> - Etykiety i podtytuły w oknach dialogowych podpisu<br />- Etykiety i podtytuły w raportach<br />- Etykiety i podtytuły w interfejsie użytkownika dokumentu<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Użyj pogrubionej wagi<br /><br /> **Nie:**<br /><br /> - Kursywa lub pogrubienie kursywa<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** pogrubiony 9 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki Środowisko &#43; Nagłówek pogrubiony](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiskowa

|||
|-|-|
|**Zastosowanie:** Cały inny tekst<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:** Kursywa lub pogrubienie kursywa|**Pojawia się jako:** 9 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki Środowisko](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Dopełnienie i odstępy
 Nagłówki wymagają przestrzeni wokół nich, aby nadać im odpowiedni nacisk. To miejsce różni się w zależności od rozmiaru punktu i tego, co jeszcze znajduje się w pobliżu nagłówka, na przykład reguły poziomej lub wiersza tekstu w czcionce środowiska.

- Idealna wyściółka dla pozycji samej w sobie powinna wynosić 90% przestrzeni wysokości znaku stołecznego. Na przykład nagłówek 28 pt Segoe UI Light ma wysokość limitu 26 pkt, a dopełnienie powinno wynosić około 23 pkt, czyli około 31 pikseli.

- Minimalna przestrzeń wokół nagłówka powinna wynosić 50% wysokości znaku kapitałowego. Mniej miejsca można wykorzystać, gdy nagłówkowi towarzyszy reguła lub inny szczelny element.

- Tekst czcionki pogrubiona środowiska powinien być zgodny z domyślnymi odstępami wysokości i dopełnieniem.

## <a name="see-also"></a>Zobacz też

- [MSDN: Czcionki (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Tekst interfejsu użytkownika (Windows)](/windows/desktop/uxguide/text-ui)
