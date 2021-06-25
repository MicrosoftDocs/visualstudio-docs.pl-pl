---
title: Czcionki i formatowanie dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej na temat czcionek i formatowania dla nowych funkcji projektowych Visual Studio, w tym sposobu używania czcionki środowiska.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e6e26b18c838fc240d7fab398f8626890eed0d31
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901685"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Czcionka środowiska
 Wszystkie czcionki w Visual Studio muszą być widoczne dla użytkownika w celu dostosowania. Odbywa się to głównie za pośrednictwem **strony Czcionki i** kolory w **oknie dialogowym > opcje.** Trzy główne kategorie ustawień czcionek to:

- **Czcionka środowiska** — główna czcionka środowiska IDE (zintegrowane środowisko projektowe), używana dla wszystkich elementów interfejsu, w tym okien dialogowych, menu, okien narzędzi i okien dokumentów. Domyślnie czcionka środowiska jest powiązana z czcionką systemową, która jest wyświetlana jako 9 punktów Segoe UI w bieżących wersjach systemu Windows. Użycie jednej czcionki dla wszystkich elementów interfejsu pomaga zapewnić spójny wygląd czcionki w całym idee.

- **Edytor tekstu** — elementy, które są dostępne w kodzie i innych edytorach opartych na tekście, można dostosować na stronie Edytor tekstu w narzędziu > **opcje.**

- **Określone kolekcje** — okna projektanta, które oferują dostosowywanie elementów interfejsu przez użytkownika, mogą uwidaczniać czcionki specyficzne dla ich powierzchni projektowej na własnej stronie ustawień w menu Narzędzia **> opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie i zmiana rozmiaru czcionki edytora
 Użytkownicy często powiększają lub powiększają rozmiar i/lub kolor tekstu w edytorze zgodnie z ich preferencjami, niezależnie od ogólnego interfejsu użytkownika. Ponieważ czcionka środowiska jest używana na elementach, które mogą pojawiać się w edytorze/projektancie lub w ramach niego, ważne jest, aby zwrócić uwagę na oczekiwane zachowanie w przypadku zmiany jednej z tych klasyfikacji czcionek.

 Podczas tworzenia elementów interfejsu użytkownika, które pojawiają się w edytorze, ale nie są częścią zawartości *,* ważne jest, aby używać czcionki środowiska, a nie czcionki tekstowej, aby elementy zmieniały rozmiar w przewidywalny sposób.

1. W przypadku tekstu kodu w edytorze zmień rozmiar za pomocą ustawienia czcionki tekstu kodu i odpowiedz na poziom powiększenia tekstu edytora.

2. Wszystkie inne elementy interfejsu powinny być powiązane z ustawieniem czcionki środowiska i reagować na wszelkie globalne zmiany w środowisku. Obejmuje to (ale nie tylko):

    - Tekst w menu kontekstowym

    - Tekst w układach edytora, na przykład tekst menu żarówki, okienko edytora szybkiego wyszukiwania i przechodzenie do okienka

    - Tekst etykiety w oknach dialogowych, takich jak **Znajdź w plikach** lub **Refaktoryzacja**

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionki środowiska
 W kodzie Native lub WinForms można uzyskać dostęp do czcionki środowiska, wywołując metodę po zapytaniu `IUIHostLocale::GetDialogFont` interfejsu z `SID_SUIHostLocale` usługi.

 W Windows Presentation Foundation (WPF) należy wyprowadzać klasę okna dialogowego z klasy powłoki `DialogWindow` zamiast klasy `Window` WPF.

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

Kod źródłowy:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Zastąp `Microsoft.VisualStudio.Shell.11.0` bieżącą wersją biblioteki DLL MPF).

 Aby wyświetlić okno dialogowe, wywołaj `ShowModal()` " " dla klasy za pośrednictwem klasy `ShowDialog()` . `ShowModal()` Ustawia prawidłowy stan modalny w powłokie, zapewnia wyśrodkowanie okna dialogowego w oknie nadrzędnym i tak dalej.

 Kod jest następujący:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` zwraca wartość logiczną? (wartość logiczna dopuszczana do wartości null) z `DialogResult` wartością , której można użyć w razie potrzeby. Wartość zwracana jest true, jeśli okno dialogowe zostało zamknięte przy użyciu **przycisku OK**.

 Jeśli chcesz wyświetlić interfejs użytkownika WPF, który nie jest oknem dialogowym i jest hostowany we własnym oknie , takim jak okno podręczne lub okno podrzędne WPF w oknie nadrzędnym Win32/WinForms, musisz ustawić elementy i na elemencie głównym elementu `HwndSource` `FontFamily` `FontSize` WPF. (Powłoka ustawia właściwości w oknie głównym, ale nie będą dziedziczone po ciągu `HWND` ). Powłoka udostępnia zasoby, z którymi można powiązyć właściwości, w ten sposób:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Formatowanie (skalowanie/pogrubienie)
 Niektóre okna dialogowe wymagają pogrubienia określonego tekstu lub rozmiaru innego niż czcionka środowiska. Wcześniej czcionki większe niż czcionka środowiska były kodowane jako " `environment font +2` " lub podobne. Użycie podanych fragmentów kodu zapewni obsługę monitorów o wysokiej rozdzielczości DPI i zapewni, że wyświetlany tekst będzie zawsze wyświetlany w prawidłowym rozmiarze i odpowiedniej wagi (np. Jasny lub Półprzezroczysty).

> [!NOTE]
> Przed zastosowaniem formatowania upewnij się, że są stosowane wskazówki w stylu [tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Aby skalować czcionkę środowiska, ustaw styl textblock lub etykiety, jak wskazano. Każdy z tych fragmentów kodu, prawidłowo użyty, wygeneruje poprawną czcionkę, w tym odpowiednie zmiany rozmiaru i wagi.

 Gdzie " `vsui` " jest odwołaniem do przestrzeni nazw `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + jasny

**Wyświetlany jako:** 34 punkty Segoe UI jasny

::: moniker range="vs-2017"

**Użyj dla:** (rzadkie) unikatowego interfejsu użytkownika, takiego jak na stronie startowej

::: moniker-end

::: moniker range=">=vs-2019"

**Użyj dla:** (rzadkie) unikatowego interfejsu użytkownika

::: moniker-end

**Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Ustaw styl textblock lub etykiety, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% czcionki środowiska + jasny
 **Wyświetlany jako:** 28 punktów Segoe UI **do:** duże tytuły okien dialogowych podpisów, główny nagłówek w raportach

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% czcionki środowiska + półlight
 **Wyświetlany jako:** 18 punktów Segoe UI semilight **Use for:** nagie, tytuły w małych i średnich oknach dialogowych

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety w pokazany sposób:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% czcionki środowiska
 **Wyświetlany jako:** 14 punktów Segoe UI **Użyj dla:** nagłówków sekcji w interfejsie użytkownika lub raportach listy dokumentów

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety w pokazany sposób:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>Czcionka środowiska na poziomie 133%
 **Występuje jako:** 12 punktów Segoe UI **Użyj dla:** mniejszych plików w oknach dialogowych podpisów i interfejsie użytkownika źródła dokumentów

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety w pokazany sposób:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% czcionki środowiska
 **Wyświetlany jako:** 11 punktów Segoe UI **użyj dla:** nagłówków sekcji w oknach dialogowych podpisu, górnych węzłów w widoku drzewa, nawigacji po tabułce pionowej

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety w pokazany sposób:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Czcionka środowiska i pogrubienie
 **Wyświetlany jako:** pogrubiony 9 punktów Segoe UI **Użyj dla:** etykiet i podwędzi w oknach dialogowych podpisów, raportach i interfejsie użytkownika źródła dokumentów

 **Kod proceduralny:** Gdzie `textBlock` to wcześniej zdefiniowany textblock i jest wcześniej `label` zdefiniowaną etykietą:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Ustaw styl textblock lub etykiety w pokazany sposób:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Style, które można zlokalizowane
 W niektórych przypadkach w przypadku lokalizacji konieczne będzie zmodyfikowanie stylów czcionek dla różnych ustawień regionalnych, takich jak usunięcie pogrubienia z tekstu w językach azji wschodniej. Aby możliwe było lokalizacji stylów czcionek, te style muszą znajdować się w pliku resx. Najlepszym sposobem osiągnięcia tego celu i nadal edytowania stylów czcionek w projektancie formularzy Visual Studio jest jawne ustawienie stylów czcionek w czasie projektowania. Mimo że powoduje to utworzenie pełnego obiektu czcionki i może wydawać się, że powoduje to zerwanie dziedziczenia czcionek nadrzędnych, do ustawienia czcionki jest używana tylko właściwość FontStyle.

 Rozwiązaniem jest podłączenie zdarzenia formularza okna `FontChanged` dialogowego. W tym `FontChanged` przypadku zapoznaj się ze wszystkimi kontrolkami i sprawdź, czy ich czcionka jest ustawiona. Jeśli jest ustawiona, zmień ją na nową czcionkę na podstawie czcionki formularza i poprzedniego stylu czcionki kontrolki. Przykładem tego w kodzie jest:

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

 Użycie tego kodu gwarantuje, że po zaktualizowaniu czcionki formularza czcionki kontrolek również zostaną zaktualizowane. Ta metoda powinna być również wywoływana z konstruktora formularza, ponieważ okno dialogowe może nie pobrać wystąpienia klasy , a zdarzenie nigdy `IUIService` `FontChanged` nie zostanie wyzwoływana. Podłączanie umożliwi dynamiczne wybieranie nowej czcionki w oknach dialogowych, nawet jeśli `FontChanged` okno dialogowe jest już otwarte.

### <a name="testing-the-environment-font"></a>Testowanie czcionki środowiska
 Aby upewnić się, że interfejs użytkownika używa czcionki środowiska i przestrzega ustawień rozmiaru, otwórz menu rozwijane Narzędzia > Opcje > Environment > Czcionki i **kolory, a** następnie wybierz pozycję "Czcionka środowiska" w menu rozwijanym "Pokaż ustawienia dla:".

 ![Ustawienia czcionek i kolorów w oknie dialogowym &gt; Opcje narzędzi](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Ustawienia czcionek i kolorów w oknie dialogowym &gt; Opcje narzędzi

 Ustaw czcionkę na zupełnie inną niż domyślna. Aby było oczywiste, którego interfejsu użytkownika nie można zaktualizować, wybierz czcionkę z serifami (na przykład "Times New Roman") i ustaw bardzo duży rozmiar. Następnie przetestuj interfejs użytkownika, aby upewnić się, że respektuje środowisko. Oto przykład użycia okna dialogowego licencji:

 ![Przykładowy tekst interfejsu użytkownika, który nie obsługuje czcionki środowiska](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Przykładowy tekst interfejsu użytkownika, który nie obsługuje czcionki środowiska

 W takim przypadku "Informacje o użytkowniku" i "Informacje o produkcie" nie respektują czcionki. W niektórych przypadkach może to być jawny wybór projektu, ale może to być usterka, jeśli jawna czcionka nie jest określona jako część specyfikacji linii czerwonej.

 Aby zresetować czcionkę, kliknij pozycję "Użyj wartości domyślnych" w obszarze Narzędzia > opcje > **environment > czcionki i kolory.**

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Styl tekstu
 Styl tekstu odnosi się do rozmiaru czcionki, wagi i wielkości czcionki. Aby uzyskać wskazówki dotyczące implementacji, [zobacz Czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Wielkością casingu tekstu

#### <a name="all-caps"></a>Wszystkie limity
 Nie używaj wszystkich limitów dla tytułów lub etykiet w Visual Studio.

#### <a name="all-lowercase"></a>Wszystkie małe litery
 Nie używaj małych liter w tytułach lub etykietach w Visual Studio.

#### <a name="sentence-and-title-case"></a>Zdanie i litera tytułu
 Tekst w Visual Studio używać liter tytułowych lub zdań, w zależności od sytuacji.

|Użyj przypadku tytułu dla:|Używaj przypadków zdań w przypadku:|
|-------------------------|----------------------------|
|Tytuły okien dialogowych|Etykiety|
|Pola grup|Pola wyboru|
|Elementy menu|Przycisków|
|Elementy menu kontekstowego|Elementy pola listy|
|Przyciski|Paski stanu|
|Etykiety tabel||
|Nagłówki kolumn||
|Etykietki narzędzi||

##### <a name="title-case"></a>Przypadek w tytule
 Litera tytułu to styl, w którym pierwsze litery większości lub wszystkich wyrazów w frazie są oznaczane literami. W Visual Studio tytuł jest używany dla wielu elementów, w tym:

- **Etykietki narzędzi.** Przykład: "Podgląd wybranych elementów"

- **Nagłówki kolumn.** Przykład: "Odpowiedź systemowa"

- **Elementy menu.** Przykład: "Zapisz wszystko"

  W przypadku używania wielkich liter są to wskazówki dotyczące tego, kiedy należy używać wielkich liter i kiedy należy pozostawić je małymi literami:

|Wielkie litery|Komentarze i przykłady|
|---------------|---------------------------|
|Wszystkie rzeczowniki||
|Wszystkie zlecenia|W tym "Is" i inne formy "to be"|
|Wszystkie przysłowy|W tym "Than" i "When"|
|Wszystkie przymiotniki|W tym "This" i "That"|
|Wszystkie zaimki|Uwzględniając zaimek dzierżawczy "Its" oraz "It's", zaimek "it" i czasownik "is"|
|Pierwsze i ostatnie słowa, niezależnie od części mowy||
|Przyimki, które są częścią frazy czasownikowej|"Zamykanie wszystkich okien" lub "Zamykanie systemu"|
|Wszystkie litery akronimów|HTML, XML, URL, IDE, RGB|
|Drugie słowo w słowie złożonych, jeśli jest rzeczownikiem lub prawidłowym przymiotnikem lub jeśli wyrazy mają równą wagę|Odsyłacz, Oprogramowanie firmy Microsoft, Dostęp do odczytu/zapisu, Run-Time|

|Małe litery|Przykłady|
|---------------|--------------|
|Drugie słowo w słowie złożonych, jeśli jest inną częścią mowy lub częścią modyfikującą pierwszy wyraz|How-to, Take-off|
|Artykuły, chyba że jeden z nich jest pierwszym słowem w tytule|a, an, the|
|Współrzędne koniunkty|and, but, for, nor, or|
|Przyimki ze słowami o czterech lub mniejszej liczbie liter poza frazą czasownika|into, on, as for, out, on top of|
|"Do", gdy jest używana w frazie wytłaszaowej|"How to Format Your Hard Disk" (Jak sformatować dysk twardy)|

##### <a name="sentence-case"></a>Litera zdania
 Litera zdania to standardowa metoda pisania, w której jest pisane tylko pierwsze słowo zdania, wraz z dowolnymi właściwymi rzeczownikami i zaimkami "I". Ogólnie rzecz biorąc, litera zdania jest łatwiejsza do odczytania przez odbiorców na całym świecie, zwłaszcza gdy zawartość zostanie przetłumaczona przez maszynę. Używaj przypadków zdań w przypadku:

1. **Komunikaty paska stanu.** Są one proste, krótkie i zawierają tylko informacje o stanie. Przykład: "Ładowanie pliku projektu"

2. **Wszystkie inne elementy interfejsu** użytkownika , w tym etykiety, pola wyboru, przyciski radiowe i elementy pola listy. Przykład: "Zaznacz wszystkie elementy na liście"

### <a name="text-formatting"></a>Formatowanie tekstu
 Domyślne formatowanie tekstu w Visual Studio 2013 jest kontrolowane przez [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa pomaga zapewnić spójny wygląd czcionek w całym środowisku IDE (zintegrowanym środowisku projektowym) i należy jej używać w celu zagwarantowania spójnego środowiska dla użytkowników.

 Domyślny rozmiar używany przez usługę Visual Studio czcionki pochodzi z systemu Windows i jest wyświetlany jako 9 punktów.

 Formatowanie można zastosować do czcionki środowiska. W tym temacie opisano, jak i gdzie używać stylów. Aby uzyskać informacje o implementacji, zapoznaj się [z czcionką środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tekst pogrubiony
 Tekst pogrubiony jest używany oszczędnie Visual Studio i powinien być zarezerwowany dla:

- etykiety pytań w kreatorach

- wyznaczanie aktywnego projektu w Eksplorator rozwiązań

- przesłanianie wartości w oknie narzędzia Właściwości

- niektóre zdarzenia na listach Visual Basic rozwijanej edytora

- zawartość wygenerowana przez serwer w konspekcie dokumentu dla stron internetowych

- nagłówki sekcji w złożonym oknie dialogowym lub interfejsie użytkownika projektanta

#### <a name="italics"></a>Kursywa
 Visual Studio nie używa kursywą ani pogrubionym tekstem kursywą.

#### <a name="color"></a>Kolor

- Niebieski jest zarezerwowany dla hiperlinków (nawigacja i polecenia) i nigdy nie powinien być używany do orientacji.

- Większe nagłówki (czcionka środowiska x 155% lub większa) mogą być kolorowane do tych celów:

  - Aby zapewnić wizualne odwołanie do interfejsu użytkownika Visual Studio podpisów

  - Aby zwrócić uwagę na określony obszar

  - Aby odciążyć standardowy ciemnoszary/czarny kolor tekstu środowiska

- Kolor w nagłówkach powinien wykorzystywać istniejące Visual Studio kolorów marki, przede wszystkim głównego purpurowego #FF68217A.

- W przypadku używania koloru w nagłówkach należy przestrzegać wytycznych dotyczących kolorów systemu [Windows,](/windows/desktop/uxguide/vis-color)w tym współczynnika kontrastu i innych kwestii dotyczących ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Visual Studio interfejsu użytkownika ma jaśniejszy wygląd z większą przestrzenią. Tam, gdzie to możliwe, paski chrome i tytułu zostały ograniczone lub usunięte. Chociaż gęstość informacji jest Visual Studio, typologia jest nadal ważna, z naciskiem na większe odstępy między wierszami oraz odmianę rozmiarów i wag czcionek.

 Poniższe tabele zawierają szczegóły projektu i przykłady wizualizacji czcionek wyświetlanych używanych w Visual Studio. Niektóre odmiany czcionek mają rozmiar i wagę, takie jak Semilight lub Light, zakodowane w ich wyglądzie.

 Fragmenty kodu implementacji dla wszystkich czcionek wyświetlanych można znaleźć w te informacje dotyczące formatowania [(skalowania/pogrubienia).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% czcionka środowiska + jasny

|Użycie|Wygląd|
|-|-|
|**Użycie:** Rzadko. Tylko unikatowy, znakowany interfejs użytkownika.<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdania<br />— Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj interfejsu użytkownika innego niż interfejs użytkownika sygnatury, takiego jak strona startowa<br />— Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 34 punkty Segoe UI jasny<br /><br /> **Przykład wizualizacji:**<br /><br /> *Obecnie nie jest używany. Może być używany na stronie Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% czcionki środowiska + jasny

::: moniker range="vs-2017"

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Większy nagłówek w oknach dialogowych sygnatur<br />— Główny nagłówek raportu<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdania<br />— Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj interfejsu użytkownika innego niż interfejs użytkownika sygnatury, takiego jak strona startowa<br />— Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 28 punktów Segoe UI jasny<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład 310% czcionki środowiska &#43; jasnym nagłówku](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Większy nagłówek w oknach dialogowych sygnatur<br />— Główny nagłówek raportu<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdania<br />— Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj interfejsu użytkownika innego niż interfejs użytkownika sygnatury<br />— Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 28 punktów Segoe UI jasny<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład 310% czcionki środowiska &#43; jasnym nagłówku](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% czcionki środowiska + półlight

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Podniebne<br />— Tytuły w małych i średnich oknach dialogowych<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdania<br />— Zawsze używaj wagi półlight<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 18 punktów Segoe UI półprzezroczysła<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład 200% czcionki środowiska &#43; półlight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% czcionki środowiska

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w interfejsie użytkownika dobrze dokumentu<br />— Raporty<br /><br /> **Wykonaj:** Używanie przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w standardowych kontrolkach Visual Studio standardowych<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 14 punktów Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki Środowisko na poziomie 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Czcionka środowiska na poziomie 133%

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> — Mniejsze rozmiary w oknach dialogowych podpisów<br />- Mniejsze rozmiary w interfejsie użytkownika dobrze dokumentu<br /><br /> **Wykonaj:** Używanie przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie kursywa<br />- Użyj dla tekstu treści<br />- Użyj w standardowych kontrolkach Visual Studio standardowych<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** 12 punktów Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki Środowisko na poziomie 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Czcionka środowiska na poziomie 122%

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w oknach dialogowych sygnatur<br />— Najważniejsze węzły w widoku drzewa<br />— Nawigacja po kartach pionowych<br /><br /> **Wykonaj:** Używanie przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub kursywa pogrubiona<br />- Użyj dla tekstu treści<br />— Używanie w standardowych kontrolkach Visual Studio standardowych<br />- Użyj w oknach narzędzi|**Wyświetlane jako:** 11 punktów Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki Środowisko na poziomie 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Czcionka środowiska i pogrubienie

|Użycie|Wygląd|
|-|-|
|**Użycia:**<br /><br /> - Etykiety i podgrzybki w oknach dialogowych sygnatur<br />- Etykiety i podgrzybki w raportach<br />- Etykiety i podgrzybki w interfejsie użytkownika dobrze dokumentu<br /><br /> **Zrobić:**<br /><br /> — Używaj przypadków zdań<br />— Użyj pogrubienia wagi<br /><br /> **Nie:**<br /><br /> — Kursywa lub kursywa pogrubiona<br />- Użyj dla tekstu treści<br />— Używanie w standardowych kontrolkach Visual Studio standardowych<br />- Użyj w oknach narzędzi|**Wyświetlany jako:** pogrubiony, 9 punktów Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykładowa czcionka environment z &#43; pogrubioną](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiska

|Użycie|Wygląd|
|-|-|
|**Użycie:** Cały inny tekst<br /><br /> **Wykonaj:** Używanie przypadku zdania<br /><br /> **Nie:** Kursywa lub kursywa pogrubiona|**Wyświetlany jako:** 9 punktów Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład czcionki Environment](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Wypełnienie i odstępy
 Nagłówki wymagają miejsca wokół nich, aby nadać im odpowiednie wyróżnienie. Ta przestrzeń różni się w zależności od rozmiaru punktu i innych informacji w pobliżu nagłówka, takich jak reguła pozioma lub wiersz tekstu w czcionce środowiska.

- Idealne uzupełnienie nagłówka samo w sobie powinno stanowić 90% spacji wysokości znaku głównego. Na przykład nagłówek Light o wartości 28 punktów Segoe UI ma wysokość limitu 26 punktów, a wypełnienie powinno mieć około 23 punktów lub około 31 pikseli.

- Minimalna przestrzeń wokół nagłówka powinna być 50% wysokości znaku capital. Mniej miejsca może być używane, gdy nagłówkowi towarzyszy reguła lub inny ściśle dopasowany element.

- Tekst czcionki środowiska pogrubiony powinien być zgodne z domyślną wysokością wiersza i wypełnieniem.

## <a name="see-also"></a>Zobacz też

- [Czcionki (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Interfejs użytkownika tekstu (Windows)](/windows/desktop/uxguide/text-ui)
