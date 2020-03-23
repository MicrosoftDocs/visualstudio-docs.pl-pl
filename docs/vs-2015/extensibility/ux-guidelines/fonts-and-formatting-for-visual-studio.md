---
title: Czcionki i formatowanie
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302414"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Czcionka środowiskowa
 Wszystkie czcionki w programie Visual Studio muszą być udostępniane użytkownikowi w celu dostosowania. Odbywa się to przede wszystkim za pośrednictwem strony **Czcionki i kolory** w oknie dialogowym **Narzędzia > Opcje.** Trzy główne kategorie ustawień czcionek to:

- **Czcionka środowiska** — czcionka podstawowa dla IDE (zintegrowane środowisko programistyczne), używana dla wszystkich elementów interfejsu, w tym okien dialogowych, menu, okien narzędzi i okien dokumentów. Domyślnie czcionka środowiska jest powiązana z czcionką systemową, która pojawia się jako interfejs użytkownika Segoe 9 pkt w bieżących wersjach systemu Windows. Użycie jednej czcionki dla wszystkich elementów interfejsu pomaga zapewnić spójny wygląd czcionki w całej idei.

- **Edytor tekstu** — elementy, które pojawiają się w kodzie i innych edytorach tekstowych, można dostosować na stronie Edytor tekstu w **obszarze Narzędzia > Opcje**.

- **Określone kolekcje** — okna projektanta, które oferują użytkownikowi dostosowanie elementów interfejsu, mogą uwidaczniać czcionki specyficzne dla ich powierzchni projektowej na ich własnej stronie ustawień w **narzędzia > opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie i zmiana rozmiaru czcionki edytora
 Użytkownicy często powiększają lub powiększają rozmiar i/lub kolor tekstu w edytorze zgodnie z ich preferencjami, niezależnie od ogólnego interfejsu użytkownika. Ponieważ czcionka środowiska jest używana na elementach, które mogą pojawić się w edytorze/projektancie lub jako część, należy zwrócić uwagę na oczekiwane zachowanie po zmianie jednej z tych klasyfikacji czcionek.

 Podczas tworzenia elementów interfejsu użytkownika, które pojawiają się w edytorze, ale nie są częścią *zawartości,* ważne jest, aby użyć czcionki środowiska, a nie czcionki tekstowej, tak aby elementy zmieniały rozmiar w przewidywalny sposób.

1. W przypadku tekstu kodu w edytorze, zmienić rozmiar z ustawieniem czcionki tekstu kodu i odpowiedzieć na poziom powiększenia tekstu edytora.

2. Wszystkie inne elementy interfejsu powinny być powiązane z ustawieniem czcionki środowiska i reagować na wszelkie globalne zmiany w środowisku. Obejmuje to (ale nie ogranicza się do):

    - Tekst w menu kontekstowych

    - Tekst w ozdobach edytora, takich jak tekst menu żarówki, szybkie znajdowanie okienka edytora i przechodzenie do okienka

    - Etykietuj tekst w oknach dialogowych, takich jak Znajdź w plikach lub Refaktoryzator

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionki środowiskowej
 W kodzie natywnym lub WinForms czcionki środowiska można uzyskać za pomocą metody **IUIHostLocale::GetDialogFont** po kwerendzie interfejsu z usługi SID_SUIHostLocale.

 Dla programu Windows Presentation Foundation (WPF), wyprowadzić klasę okna dialogowego z klasy **DialogWindow** powłoki zamiast klasy **Window** WPF.

 W języku XAML kod wygląda następująco:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Zastąp `Microsoft.VisualStudio.Shell.11.0` bieżącą wersją biblioteki DLL MPF).

 Aby wyświetlić okno dialogowe, wywołanie **"ShowModal()**" w klasie przez **ShowDialog()**. **ShowModal()** ustawia prawidłowy stan modalny w powłoce, zapewnia, że okno dialogowe jest wyśrodkowane w oknie nadrzędnym i tak dalej.

 Kod jest następujący:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** zwraca bool? (nullable Boolean) z **DialogResult**, który może być używany w razie potrzeby. Zwracana wartość jest prawdziwa, jeśli okno dialogowe zostało zamknięte za pomocą **przycisku OK**.

 Jeśli chcesz wyświetlić niektóre WPF UI, który nie jest dialogowy i jest obsługiwany w jego własnym **HwndSource**, takich jak okno podręczne lub okno podrzędne WPF okna nadrzędnego Win32/WinForms, należy ustawić **FontFamily** i **FontSize** na element główny WPF. (Powłoka ustawia właściwości w oknie głównym, ale nie będą dziedziczone obok HWND). Powłoka zapewnia zasoby, z którymi właściwości mogą być powiązane, w ten sposób:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Odwołanie do formatowania (skalowanie/pogruszanie)
 Niektóre okna dialogowe wymagają pogrubienia określonego tekstu lub rozmiaru innego niż czcionka środowiskowa. Wcześniej czcionki większe niż czcionka środowiskowa były kodowane jako "czcionka środowiskowa +2" lub podobne. Za pomocą podanych fragmentów kodu będzie obsługiwać monitory o wysokiej rozdzielczości DPI i upewnij się, że wyświetlany tekst zawsze pojawia się przy prawidłowym rozmiarze i wadze (takich jak Light lub Semilight).

> **Uwaga: Przed zastosowaniem formatowania upewnij się, że postępujesz zgodnie ze wskazówkami znalezionymi w [stylu tekstowym](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Aby skalować czcionkę środowiska, ustaw styl TextBlock lub Label zgodnie ze wskazanymi. Każdy z tych fragmentów kodu, prawidłowo używany, wygeneruje poprawną czcionkę, w tym odpowiednie zmiany rozmiaru i wagi.

 Gdzie "vsui" jest odwołaniem do obszaru nazw Microsoft.VisualStudio.Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>Czcionka środowiskowa 375% + światło
 **Pojawia się jako:** 34 pkt Segoe UI Light

 **Służy do:** (rzadkich) unikalnych markowych interfejsów użytkownika, takich jak strona początkowa

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>Czcionka 310% Środowiska + Światło
 **Pojawia się jako:** 28 pkt Segoe UI Light

 **Służy do:** tytułów okien dialogowych z dużymi podpisami, nagłówka głównego w raportach

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>Czcionka 200% Środowiska + Semilight
 **Pojawia się jako:** 18 pkt Segoe UI Semilight

 **Zastosowanie dla:** podpozycji, tytułów w małych i średnich oknach dialogowych

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>Czcionka środowiskowa 155%
 **Pojawia się jako:** 14 pkt Segoe UI

 **Służy do:** nagłówków sekcji w interfejsie użytkownika lub raportach dotyczących dobrze dokumentu

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>Czcionka środowiskowa 133%
 **Pojawia się jako:** 12 pkt Segoe UI

 **Służy do:** mniejszych podpozycji w oknach dialogowych podpisu i dobrze dokumentuj interfejs użytkownika

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>Czcionka środowiskowa 122%
 **Pojawia się jako:** 11 pkt Segoe UI

 **Służy do:** nagłówków sekcji w oknach dialogowych podpisu, węzłów górnych w widoku drzewa, nawigacji po karcie pionowej

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Czcionka środowiskowa + pogrubienie
 **Pojawia się jako:** pogrubiony 9 pkt Segoe UI

 **Służy do:** etykiet i podnagłów w oknach dialogowych podpisu, raportach i dobrze dokumentuj interfejsu użytkownika

 **Kodeks proceduralny:** Gdzie "textBlock" jest wcześniej zdefiniowane TextBlock i "label" jest wcześniej zdefiniowane Etykiety.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Ustaw styl textblock lub label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Style lokalne
 W niektórych przypadkach lokalizatory będą musiały zmodyfikować style czcionek dla różnych ustawień regionalnych, takich jak usuwanie pogrubienia z tekstu dla języków wschodnioazjatyckich. Aby lokalizacja stylów czcionek była możliwa, style te muszą znajdować się w pliku .resx. Najlepszym sposobem, aby to osiągnąć i nadal edytować style czcionek w visual studio projektanta formularzy jest jawnie ustawić style czcionek w czasie projektowania. Mimo że tworzy to obiekt pełnej czcionki i może wydawać się przerwać dziedziczenie czcionek nadrzędnych, tylko FontStyle właściwość jest używana do ustawiania czcionki.

 Rozwiązaniem jest podłączyć okno dialogowe **fontchanged** zdarzenia. W **FontChanged** zdarzenia, chodzić wszystkie formanty i sprawdzić, czy ich czcionka jest ustawiona. Jeśli jest ustawiona, zmień ją na nową czcionkę na podstawie czcionki formularza i poprzedniego stylu czcionki formantu. Przykładem tego w kodzie jest:

```
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

 Za pomocą tego kodu gwarantuje, że po zaktualizowaniu czcionki formularza, czcionki formantów zostanie zaktualizowany, jak również. Ta metoda powinna być również wywoływana z konstruktora formularza, ponieważ okno dialogowe może nie uzyskać wystąpienia **IUIService** i **FontChanged** zdarzenie nigdy nie będzie uruchamiać. Podłączanie **FontChanged** pozwoli okna dialogowe dynamicznie podnieść nową czcionkę, nawet jeśli okno dialogowe jest już otwarte.

### <a name="testing-the-environment-font"></a>Testowanie czcionki środowiskowej
 Aby upewnić się, że interfejs użytkownika używa czcionki środowiska i jest zgodny z ustawieniami rozmiaru, otwórz okno Opcje **> Narzędzia > środowisko > czcionki i kolory** i wybierz "Czcionka środowiska" w menu rozwijanym "Pokaż ustawienia dla:".

 ![Strona Czcionki i kolory w oknie dialogowym Narzędzia &#62; Opcje](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Ustawienia czcionek i kolorów w oknie dialogowym Narzędzia > Opcje**

 Ustaw czcionkę na coś zupełnie innego niż domyślny. Aby było oczywiste, który interfejs użytkownika nie jest aktualizowany, wybierz czcionkę z szeryfami (na przykład "Times New Roman") i ustaw bardzo duży rozmiar. Następnie przetestuj swój interfejs użytkownika, aby upewnić się, że szanuje środowisko. Oto przykład użycia okna dialogowego licencji:

 ![Przykład okna dialogowego nieużywanie czcionki środowiska](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Przykład tekstu interfejsu użytkownika, który nie jest zgodny z czcionką środowiska**

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
 Domyślne formatowanie tekstu w programie Visual Studio 2013 jest kontrolowane przez [czcionkę Środowisko](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa pomaga zapewnić spójny wygląd czcionki w całym środowisku IDE (zintegrowane środowisko programistyczne) i należy go używać, aby zagwarantować spójne środowisko dla użytkowników.

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

- Podczas używania koloru w nagłówkach należy przestrzegać [wytycznych dotyczących kolorów systemu Windows,](https://msdn.microsoft.com/library/dn742482.aspx)w tym współczynnika kontrastu i innych zagadnień dotyczących ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Projekt interfejsu użytkownika programu Visual Studio ma jaśniejszy wygląd z większą liczącą odstępów. W miarę możliwości zmniejszono lub usunięto paski chromu i tytułu. Podczas gdy gęstość informacji jest wymagana w programie Visual Studio, typografia nadal jest ważna, z naciskiem na bardziej otwarte odstępy między wierszami i zróżnicowanie rozmiarów i wag czcionek.

 Poniższe tabele zawierają szczegóły projektu i przykłady wizualne dla czcionek wyświetlanych używanych w programie Visual Studio. Niektóre odmiany czcionek wyświetlania mają zarówno rozmiar, jak i wagę, takie jak Semilight lub Light, zakodowane w ich wyglądzie.

 Fragmenty kodu implementacji dla wszystkich czcionek wyświetlanych można znaleźć w [odwołaniu do formatowania (skalowanie/pogrubienie).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>Czcionka środowiskowa 375% + światło

|||
|-|-|
|**Zastosowanie:** Rzadko. Unikalny interfejs użytkownika marki tylko.<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj dla interfejsu użytkownika innego niż podpis ui, takich jak Strona początkowa<br />- Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 34 pkt Segoe UI Light<br /><br /> **Przykład wizualny:**<br /><br /> *Obecnie nie jest używany. Może być używany na stronie początkowej.*|

#### <a name="310-environment-font--light"></a>Czcionka 310% Środowiska + Światło

|||
|-|-|
|**Użycia:**<br /><br /> - Większy nagłówek w oknach dialogowych podpisu<br />- Nagłówek sprawozdania głównego<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze używaj lekkiej wagi<br /><br /> **Nie:**<br /><br /> - Użyj dla interfejsu użytkownika innego niż podpis ui, takich jak Strona początkowa<br />- Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 28 pkt Segoe UI Light<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki 310% środowiska &#43; nagłówek Światło](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>Czcionka 200% Środowiska + Semilight

|||
|-|-|
|**Użycia:**<br /><br /> - Podpozycje<br />- Tytuły w małych i średnich oknach dialogowych<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Zawsze stosować wagę Semilight<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 18 pkt Segoe UI Semillight<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki 200% Environment &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>Czcionka środowiskowa 155%

|||
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w dokumencie dobrze UI<br />- Raporty<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 14 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 155%](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Czcionka środowiskowa 133%

|||
|-|-|
|**Użycia:**<br /><br /> - Mniejsze podpozycje w oknach dialogowych podpisu<br />- Mniejsze podpozycje w interfejsie użytkownika dobrze dokumentu<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 12 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 133%](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Czcionka środowiskowa 122%

|||
|-|-|
|**Użycia:**<br /><br /> - Nagłówki sekcji w oknach dialogowych podpisu<br />- Wierzchnie węzły w widoku drzewa<br />- Nawigacja w pionie<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> - Pogrubienie, kursywa lub pogrubienie kursywą<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** 11 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład nagłówka czcionki środowisko 122%](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Czcionka środowiskowa + pogrubienie

|||
|-|-|
|**Użycia:**<br /><br /> - Etykiety i podtytuły w oknach dialogowych podpisu<br />- Etykiety i podtytuły w raportach<br />- Etykiety i podtytuły w interfejsie użytkownika dokumentu<br /><br /> **Zrobić:**<br /><br /> - Użyj przypadku zdanie<br />- Użyj pogrubionej wagi<br /><br /> **Nie:**<br /><br /> - Kursywa lub pogrubienie kursywa<br />- Służy do tekstu podstawowego<br />- Zastosowanie w standardowych formanty Visual Studio<br />- Zastosowanie w oknach narzędzi|**Pojawia się jako:** pogrubiony 9 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki Środowisko &#43; Nagłówek pogrubiony](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiskowa

|||
|-|-|
|**Zastosowanie:** Cały inny tekst<br /><br /> **Wykonaj:** Użyj przypadku zdania<br /><br /> **Nie należy:** Kursywa lub pogrubienie kursywa|**Pojawia się jako:** 9 pkt Segoe UI<br /><br /> **Przykład wizualny:**<br /><br /> ![Przykład czcionki Środowisko](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Dopełnienie i odstępy
 Nagłówki wymagają przestrzeni wokół nich, aby nadać im odpowiedni nacisk. To miejsce różni się w zależności od rozmiaru punktu i tego, co jeszcze znajduje się w pobliżu nagłówka, na przykład reguły poziomej lub wiersza tekstu w czcionce środowiska.

- Idealna wyściółka dla pozycji samej w sobie powinna wynosić 90% przestrzeni wysokości znaku stołecznego. Na przykład nagłówek 28 pt Segoe UI Light ma wysokość limitu 26 pkt, a dopełnienie powinno wynosić około 23 pkt, czyli około 31 pikseli.

- Minimalna przestrzeń wokół nagłówka powinna wynosić 50% wysokości znaku kapitałowego. Mniej miejsca można wykorzystać, gdy nagłówkowi towarzyszy reguła lub inny szczelny element.

- Tekst czcionki pogrubiona środowiska powinien być zgodny z domyślnymi odstępami wysokości i dopełnieniem.

## <a name="see-also"></a>Zobacz też
 [MSDN: Czcionki (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Tekst interfejsu użytkownika (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
