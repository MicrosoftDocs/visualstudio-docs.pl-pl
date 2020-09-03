---
title: Czcionki i formatowanie dla programu Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd2e8a41ef4b9708df079e94bcac8b8c06189116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536113"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Czcionka środowiska
 Wszystkie czcionki w programie Visual Studio muszą być widoczne dla użytkownika w celu dostosowania. Jest to wykonywane głównie za pomocą strony **czcionki i kolory** w oknie dialogowym **Narzędzia > opcje** . Trzy główne kategorie ustawień czcionki są następujące:

- **Czcionka środowiska** — Podstawowa czcionka IDE (zintegrowane środowisko programistyczne), używana dla wszystkich elementów interfejsu, w tym okien dialogowych, menu, okien narzędzi i okien dokumentów. Domyślnie czcionka środowiska jest powiązana z czcionką systemową, która jest wyświetlana jako 9 pt Segoe UI w bieżących wersjach systemu Windows. Używanie jednej czcionki dla wszystkich elementów interfejsu pomaga zapewnić spójny wygląd czcionki w całym środowisku IDE.

- **Edytor tekstu** — elementy znajdujące się w kodzie i inne edytory tekstowe można dostosować na stronie Edytor tekstu w obszarze **Narzędzia > opcje**.

- **Określone kolekcje** — okna projektanta, które oferują możliwość dostosowywania elementów interfejsu przez użytkownika, mogą uwidaczniać czcionki specyficzne dla ich powierzchni projektowej na swojej stronie ustawień w obszarze **Narzędzia > opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie i zmienianie rozmiarów czcionek edytora
 Użytkownicy często powiększają lub powiększają rozmiar i/lub kolor tekstu w edytorze zgodnie z ich preferencjami niezależnie od ogólnego interfejsu użytkownika. Ponieważ czcionka środowiska jest używana w przypadku elementów, które mogą być wyświetlane w lub w ramach edytora/projektanta, należy pamiętać, że oczekiwane zachowanie, gdy jedna z tych klasyfikacji czcionek zostanie zmieniona.

 Podczas tworzenia elementów interfejsu użytkownika, które są wyświetlane w edytorze, ale nie są częścią *zawartości*, ważne jest użycie czcionki środowiska, a nie czcionki tekstowej, tak aby elementy zmieniały się w przewidywalny sposób.

1. W przypadku tekstu kodu w edytorze Zmień rozmiar z ustawieniem czcionka tekstu kodu i Odpowiedz na poziom powiększenia tekstu edytora.

2. Wszystkie inne elementy interfejsu powinny być powiązane z ustawieniem czcionki środowiska i odpowiadać na wszystkie globalne zmiany w środowisku. Obejmuje to (ale nie tylko):

    - Tekst w menu kontekstowym

    - Tekst w edytorze definiowania układu, np. tekst menu żarówki, szybkie znajdowanie okienka edytora i przejdź do okienka

    - Tekst etykiety w oknach dialogowych, takich jak **Znajdź w plikach** lub **refaktoryzacji**

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionki środowiska
 W kodzie natywnym lub WinFormowym można uzyskać dostęp do czcionki środowiska przez wywołanie metody `IUIHostLocale::GetDialogFont` po wykonaniu zapytania dotyczącego interfejsu z `SID_SUIHostLocale` usługi.

 Dla Windows Presentation Foundation (WPF), należy utworzyć klasę okna dialogowego z `DialogWindow` klasy powłoki zamiast z `Window` klasy WPF.

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

Kod w tle:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Zamień na `Microsoft.VisualStudio.Shell.11.0` bieżącą wersję biblioteki DLL MPF).

 Aby wyświetlić okno dialogowe, wywołaj " `ShowModal()` " w klasie nad `ShowDialog()` . `ShowModal()` Ustawia prawidłowy stan modalny w powłoce, zapewnia, że okno dialogowe jest wyśrodkowane w oknie nadrzędnym i tak dalej.

 Kod jest następujący:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` Zwraca wartość logiczną? (wartość null) z `DialogResult` , która może być używana w razie konieczności. Wartość zwracana ma wartość true, jeśli okno dialogowe zostało zamknięte z **przyciskiem OK**.

 Jeśli musisz wyświetlić jakiś interfejs użytkownika WPF, który nie jest oknem dialogowym i znajduje się we własnym obszarze, na przykład w `HwndSource` oknie podręcznym lub oknie podrzędnym WPF okna nadrzędnego Win32/WinForms, musisz ustawić `FontFamily` i `FontSize` na elemencie głównym elementu WPF. (Powłoka ustawia właściwości w oknie głównym, ale nie będzie dziedziczona poza `HWND` ). Powłoka zawiera zasoby, do których można powiązać właściwości, takie jak:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Formatowanie (skalowanie/pogrubienie) odwołania
 Niektóre okna dialogowe wymagają pogrubienia tekstu lub rozmiaru innego niż czcionka środowiska. Wcześniej czcionki o rozmiarze większym od czcionki środowiska były kodowane jako " `environment font +2` " lub podobne. Użycie dostarczonych fragmentów kodu będzie obsługiwać monitory o wysokiej rozdzielczości i upewnij się, że wyświetlany tekst zawsze pojawia się o prawidłowym rozmiarze i wadze (na przykład Light lub Semilight).

> [!NOTE]
> Przed zastosowaniem formatowania upewnij się, że są spełnione wskazówki znajdujące się w [stylu tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle). * *

 Aby skalować czcionkę środowiska, ustaw styl bloku textlub etykiety zgodnie z opisem. Każdy z tych fragmentów kodu, właściwie użyty, wygeneruje poprawną czcionkę, włącznie z odpowiednimi wielkościami i odmianami wagi.

 Gdzie " `vsui` " jest odwołaniem do przestrzeni nazw `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% czcionki środowiska + jasne

**Pojawia się jako:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Używany dla:** (rzadki) unikatowy interfejs użytkownika z oznaczeniem, taki jak na stronie startowej

::: moniker-end

::: moniker range=">=vs-2019"

**Używany dla:** (rzadki) unikatowy interfejs użytkownika z znakiem

::: moniker-end

**Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% czcionki środowiska + jasne
 **Występuje jako:** 28 pt Segoe UI lekkie **użycie dla:** duże tytuły okien dialogowych z podpisem, główny nagłówek w raportach

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% czcionki środowiska + Semilight
 **Pojawia się jako:** 18 pt Segoe UI Semilight **dla:** podpozycje, tytuły w małych i średnich oknach dialogowych

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% czcionki środowiska
 **Pojawia się jako:** 14 pt Segoe UI **use for:** nagłówki sekcji w interfejsie użytkownika i raportach

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% czcionki środowiska
 **Pojawia się jako:** 12 pt Segoe UI **use for:** mniejsze podnagłówki w oknach dialogowych sygnatur i interfejsie użytkownika

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% czcionki środowiska
 **Pojawia się jako:** 11 pt Segoe UI **use for:** nagłówki sekcji w oknach dialogowych podpisów, górnych węzłach w widoku drzewa, Nawigacja tabulatorów pionowych

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Font Environment + Bold
 **Pojawia się jako:** pogrubiony 9 pt Segoe UI **use for:** etykiety i nagłówki podrzędne w oknach dialogowych, raportach i interfejsie użytkownika

 **Kod proceduralny:** Gdzie `textBlock` jest wcześniej zdefiniowanym obiektem TextBlock i `label` jest etykietą zdefiniowaną wcześniej:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Style lokalizowalne
 W niektórych przypadkach lokalizatory muszą modyfikować style czcionek dla różnych ustawień regionalnych, takich jak usuwanie pogrubienia z tekstu dla języków wschodnioazjatyckich. Aby możliwe było lokalizowanie stylów czcionki, te style muszą znajdować się w pliku resx. Najlepszym sposobem na wykonanie tej operacji i nadal edytowanie stylów czcionki w projektancie formularzy programu Visual Studio jest jawne ustawienie stylów czcionki w czasie projektowania. Chociaż powoduje to utworzenie pełnego obiektu czcionki i może wydawać się uszkodzeniem dziedziczenia czcionek nadrzędnych, tylko Właściwość FontStyle jest używana do ustawiania czcionki.

 Rozwiązaniem jest przełączanie zdarzenia formularza okna dialogowego `FontChanged` . W `FontChanged` zdarzeniu Przeszukaj wszystkie kontrolki i sprawdź, czy ich czcionka została ustawiona. Jeśli jest ustawiona, Zmień ją na nową czcionkę w oparciu o czcionkę formularza i poprzedni styl czcionki kontrolki. Przykładem tego kodu jest:

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

 Przy użyciu tego kodu gwarantujemy, że podczas aktualizowania czcionki formularza zostaną również zaktualizowane czcionki kontrolek. Ta metoda powinna być również wywoływana z konstruktora formularza, ponieważ okno dialogowe może nie można pobrać wystąpienia, `IUIService` a `FontChanged` zdarzenie nigdy nie zostanie wywołane. Funkcja przechwytania `FontChanged` zezwoli na dynamiczne pobranie nowej czcionki przez okna dialogowe, nawet jeśli okno dialogowe jest już otwarte.

### <a name="testing-the-environment-font"></a>Testowanie czcionki środowiska
 Aby upewnić się, że interfejs użytkownika używa czcionki środowiskowej i uwzględnia ustawienia rozmiaru, Otwórz **narzędzia > opcje > środowisku > czcionki i kolory** i wybierz pozycję "Czcionka środowiskowa" w menu rozwijanym "Pokaż ustawienia dla:".

 ![Ustawienia czcionek i kolorów w &gt; oknie dialogowym Opcje narzędzi](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 — a_OptionsFonts")<br />Ustawienia czcionek i kolorów w &gt; oknie dialogowym Opcje narzędzi

 Ustaw czcionkę na coś innego niż domyślne. Aby określić, który interfejs użytkownika nie jest aktualizowany, wybierz czcionkę z szeryfami (np. "Times New Roman") i ustaw bardzo duży rozmiar. Następnie przetestuj interfejs użytkownika, aby upewnić się, że będzie on odnoszący się do środowiska. Oto przykład przy użyciu okna dialogowego licencji:

 ![Przykładowy tekst interfejsu użytkownika, który nie uwzględnia czcionki środowiska](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 — b_WrongFontDialog")<br />Przykładowy tekst interfejsu użytkownika, który nie uwzględnia czcionki środowiska

 W takim przypadku "informacje o użytkowniku" i "informacje o produkcie" nie respektują czcionki. W niektórych przypadkach może to być jawny wybór projektu, ale może to być usterka, Jeśli czcionka jawna nie zostanie określona jako część specyfikacji Redline.

 Aby zresetować czcionkę, kliknij przycisk "Użyj ustawień domyślnych" w obszarze **narzędzia > opcje > środowisku > czcionki i kolory**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Styl tekstu
 Styl tekstu odnosi się do rozmiaru czcionki, wagi i wielkości liter. Aby uzyskać wskazówki dotyczące implementacji, zobacz [Font Environment](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Wielkość liter tekstu

#### <a name="all-caps"></a>Wszystkie wersaliki
 Nie używaj wersalików dla tytułów ani etykiet w programie Visual Studio.

#### <a name="all-lowercase"></a>Wszystkie małe litery
 Nie używaj małych liter w tytułach lub etykietach w programie Visual Studio.

#### <a name="sentence-and-title-case"></a>Wielkie litery i tytuł
 W zależności od sytuacji tekst w programie Visual Studio powinien korzystać z wielkości liter lub wielkości liter w zdaniu.

|Użyj przypadku tytułu dla:|Użyj przypadku zdania:|
|-------------------------|----------------------------|
|Tytuły okien dialogowych|Etykiety|
|Pola grup|Pola wyboru|
|Elementy menu|Przyciski radiowe|
|Elementy menu kontekstowego|Elementy pola listy|
|Przyciski|Paski stanu|
|Etykiety tabeli||
|Nagłówki kolumn||
|Etykietki narzędzi||

##### <a name="title-case"></a>Wielkość liter w tytule
 Przypadek tytułu jest stylem, w którym pierwsze litery większości lub wszystkich wyrazów w frazie są pisane wielkimi literami. W programie Visual Studio tytuł przypadku jest używany w przypadku wielu elementów, w tym:

- **Etykietki narzędzi.** Przykład: "Podgląd wybranych elementów"

- **Nagłówki kolumn.** Przykład: "odpowiedź systemu"

- **Elementy menu.** Przykład: "Zapisz wszystko"

  W przypadku używania wielkości liter, są to wskazówki dotyczące sytuacji, w których można wyrazić wielką literę i kiedy pozostawić je małymi literami:

|Wielkie litery|Komentarze i przykłady|
|---------------|---------------------------|
|Wszystkie rzeczowniki||
|Wszystkie zlecenia|Dołączenie "is" i innych form "do"|
|Wszystkie zlecenia|W tym "niż" i "When"|
|Wszystkie przymiotniki|Włączenie "This" i "to"|
|Wszystkie rzeczowniki|Łącznie z Possessive "jego", a także "", "umową pronoun" i zlecenie "is"|
|Pierwsze i ostatnie słowa, niezależnie od części mowy||
|Pozycje, które są częścią wyrażenia czasownikowego|"Zamykanie całego systemu Windows" lub "zamykanie systemu"|
|Wszystkie litery akronimu|HTML, XML, URL, IDE, RGB|
|Drugie słowo wyrazu złożonego, jeśli jest to rzeczownik lub właściwy przymiotnik, lub jeśli wyrazy mają równą wagę|Odsyłacze, oprogramowanie przed firmą Microsoft, dostęp do odczytu/zapisu, czas wykonywania|

|Małe litery|Przykłady|
|---------------|--------------|
|Drugie słowo słowa złożonego, jeśli jest to inna część mowy lub Participle modyfikowanie pierwszego wyrazu|Jak to zrobić, jak to zrobić|
|Artykuły, chyba że jest to pierwsze słowo w tytule|a, an, the|
|Współrzędne współrzędnych|and, ale, for, or lub|
|Umieszczanie wyrazów z co najmniej czterema literami poza wyrażeniem orzeczenia|do, do, od, do, z|
|"Do", gdy jest używany w frazie linia nieskończona|"Jak sformatować dysk twardy"|

##### <a name="sentence-case"></a>Przypadek zdania
 Przypadek zdania to standardowa metoda tworzenia wielkich liter, w której tylko pierwszy wyraz zdania jest pisany wielkimi literami, wraz ze wszystkimi odpowiednimi rzeczownikami i pronoun "I". Ogólnie rzecz biorąc, przypadek zdania jest łatwiejszy dla odbiorców na całym świecie, szczególnie w przypadku tłumaczenia zawartości przez maszynę. Użyj przypadku zdania:

1. **Komunikaty paska stanu.** Są one proste, krótkie i zawierają tylko informacje o stanie. Przykład: "Ładowanie pliku projektu"

2. **Wszystkie inne elementy interfejsu użytkownika**, w tym etykiety, pola wyboru, przyciski radiowe i elementy listy. Przykład: "Wybierz wszystkie elementy z listy"

### <a name="text-formatting"></a>Formatowanie tekstu
 Domyślne formatowanie tekstu w Visual Studio 2013 jest kontrolowane przez [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa zapewnia spójny wygląd czcionki w środowisku IDE (zintegrowane środowisko programistyczne) i musi być używana w celu zagwarantowania spójnego środowiska dla użytkowników.

 Domyślny rozmiar używany przez usługę czcionek programu Visual Studio pochodzi z systemu Windows i pojawia się jako 9 punktów.

 Formatowanie można zastosować do czcionki środowiska. W tym temacie opisano, jak i gdzie używać stylów. Aby uzyskać informacje o implementacji, zapoznaj się z [czcionką środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tekst pogrubiony
 Pogrubiony tekst jest oszczędny w programie Visual Studio i powinien być zarezerwowany dla:

- etykiety pytań w kreatorach

- Wyznaczanie aktywnego projektu w Eksplorator rozwiązań

- zastąpione wartości w oknie narzędzia właściwości

- Niektóre zdarzenia z listy rozwijanej edytora Visual Basic

- zawartość wygenerowana przez serwer w konspekcie dokumentu dla stron sieci Web

- nagłówki sekcji w złożonym oknie dialogowym lub interfejsie użytkownika projektanta

#### <a name="italics"></a>Kursywa
 Program Visual Studio nie używa kursywy ani pogrubionej kursywy tekstu.

#### <a name="color"></a>Kolor

- Niebieski jest zarezerwowany dla hiperlinków (Nawigacja i poleceń) i nigdy nie powinien być używany do orientacji.

- Większe nagłówki (czcionka środowiskowa x 155% lub więcej) można kolorować w następujących celach:

  - Aby zapewnić wizualny zaskarżenie do podpisu interfejsu użytkownika programu Visual Studio

  - Aby odwołać uwagę do określonego obszaru

  - Aby zaoferować zwolnienie ze standardowego koloru kolorowego w kolorze szarym/czarnym

- Kolor w nagłówkach powinien wykorzystywać istniejące kolory znakowe programu Visual Studio, a głównie główne, #FF68217A.

- Korzystając z koloru w nagłówkach, należy przestrzegać [wytycznych dotyczących kolorów systemu Windows](/windows/desktop/uxguide/vis-color), w tym współczynnika kontrastu i innych zagadnień dotyczących ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Projektowanie interfejsu użytkownika programu Visual Studio oferuje jaśniejszy wygląd z większą ilością białych znaków. Tam, gdzie to możliwe, Chrome i paski tytułu zostały zredukowane lub usunięte. Chociaż gęstość informacji jest wymagana w programie Visual Studio, Typografia w dalszym ciągu jest ważna, z naciskiem na więcej otwartych odstępów między wierszami i zróżnicowanie rozmiarów i wag czcionek.

 Poniższe tabele zawierają szczegóły projektu i przykłady wizualizacji wyświetlania czcionek używanych w programie Visual Studio. Niektóre Wariacje czcionek wyświetlania mają zarówno rozmiar, jak i grubość, takie jak Semilight lub Light, kodowane w ich wyglądzie.

 Fragmenty kodu implementacji dla wszystkich czcionek wyświetlanych można znaleźć w temacie [Formatowanie (skalowanie/pogrubienie)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>375% czcionki środowiska + jasne

|Użycie|Wygląd|
|-|-|
|**Użycie:** Rzadko. Unikatowy tylko oznakowany interfejs użytkownika.<br /><br /> **Nie**<br /><br /> -Użyj przypadku zdania<br />-Zawsze używaj wagi lekkiej<br /><br /> **Nie:**<br /><br /> -Użyj dla interfejsu użytkownika innego niż interfejs użytkownika podpisu, na przykład Strona startowa<br />— Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 34 pt Segoe UI Light<br /><br /> **Przykład wizualizacji:**<br /><br /> *Obecnie nie jest używana. Może być używany na stronie startowej programu Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% czcionki środowiska + jasne

::: moniker range="vs-2017"

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Większy nagłówek w oknach dialogowych podpisów<br />— Główny nagłówek raportu<br /><br /> **Nie**<br /><br /> -Użyj przypadku zdania<br />-Zawsze używaj wagi lekkiej<br /><br /> **Nie:**<br /><br /> -Użyj dla interfejsu użytkownika innego niż interfejs użytkownika podpisu, na przykład Strona startowa<br />— Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 28 pt Segoe UI Light<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład 310% czcionki środowiskowej &#43; nagłówka światła](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 — a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Większy nagłówek w oknach dialogowych podpisów<br />— Główny nagłówek raportu<br /><br /> **Nie**<br /><br /> -Użyj przypadku zdania<br />-Zawsze używaj wagi lekkiej<br /><br /> **Nie:**<br /><br /> -Użyj dla interfejsu użytkownika innego niż interfejs użytkownika podpisu<br />— Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 28 pt Segoe UI Light<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład 310% czcionki środowiskowej &#43; nagłówka światła](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 — a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% czcionki środowiska + Semilight

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Podnagłówki<br />-Tytuły w małych i średnich oknach dialogowych<br /><br /> **Nie**<br /><br /> -Użyj przypadku zdania<br />-Zawsze używaj wagi Semilight<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 18 pt Segoe UI Semillight<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład czcionki środowiska 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 — b_EF200")|

#### <a name="155-environment-font"></a>155% czcionki środowiska

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Nagłówki sekcji w interfejsie użytkownika prawidłowego dokumentu<br />-Raporty<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />-Użyj w standardowych kontrolkach programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 14 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 — c_EF155")|

#### <a name="133-environment-font"></a>133% czcionki środowiska

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Mniejsze podnagłówki w oknach dialogowych podpisów<br />-Mniejsze podnagłówki w interfejsie użytkownika dobrze<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />-Użyj w standardowych kontrolkach programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 12 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 — d_EF133")|

#### <a name="122-environment-font"></a>122% czcionki środowiska

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Nagłówki sekcji w oknach dialogowych podpisów<br />-Górne węzły w widoku drzewa<br />— Nawigacja na kartach pionowych<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />-Użyj w standardowych kontrolkach programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 11 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 — e_EF122")|

#### <a name="environment-font--bold"></a>Font Environment + Bold

|Użycie|Wygląd|
|-|-|
|**Wykorzystywani**<br /><br /> -Etykiety i nagłówki podrzędne w oknach dialogowych sygnatur<br />-Etykiety i nagłówki podrzędne w raportach<br />-Etykiety i nagłówki podrzędne w interfejsie użytkownika<br /><br /> **Nie**<br /><br /> -Użyj przypadku zdania<br />-Użyj pogrubionej grubości<br /><br /> **Nie:**<br /><br /> -Kursywa lub pogrubiona kursywa<br />— Użyj dla tekstu treści<br />-Użyj w standardowych kontrolkach programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** pogrubiony 9 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład czcionki środowiska &#43; pogrubiony nagłówek](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 — f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiska

|Użycie|Wygląd|
|-|-|
|**Użycie:** Cały tekst<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:** Kursywa lub pogrubiona kursywa|**Pojawia się jako:** 9 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład czcionki środowiska](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 — g_EF")|

### <a name="padding-and-spacing"></a>Uzupełnienie i odstępy
 Nagłówki wymagają miejsca wokół nich, aby dać im odpowiedni nacisk. Ta przestrzeń jest różna w zależności od rozmiaru punktu i od tego, co inne znajduje się w odniesieniu do nagłówka, takiego jak reguła pozioma lub wiersz tekstu w czcionce środowiskowej.

- Idealnym uzupełnieniem dla nagłówka przez siebie może być 90% miejsca na wysokości znaków. Na przykład nagłówek "28 pt Segoe UI światła ma wysokość zakończenia 26 punktów, a uzupełnienie powinno wynosić około 23 pt lub około 31 pikseli.

- Minimalna ilość miejsca w pobliżu nagłówka powinna wynosić od 50% wysokości znaków. W przypadku, gdy do nagłówka jest dołączona reguła lub inny element ociole, można użyć mniejszej ilości miejsca.

- Tekst czcionki pogrubionego środowiska powinien podążać za domyślnym odstępem wysokości i dopełnieniem.

## <a name="see-also"></a>Zobacz też

- [Czcionki (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Tekst interfejsu użytkownika (system Windows)](/windows/desktop/uxguide/text-ui)
