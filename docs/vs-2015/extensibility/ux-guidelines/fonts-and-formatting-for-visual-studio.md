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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409910"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_TheEnvironmentFont"></a>Czcionka środowiska
 Wszystkie czcionki w programie Visual Studio muszą być widoczne dla użytkownika na potrzeby dostosowywania. Jest to wykonywane głównie za pomocą strony **czcionki i kolory** w oknie dialogowym **Narzędzia > Opcje** . Są trzy główne kategorie ustawienia czcionek:

- **Czcionka środowiska** — Podstawowa czcionka IDE (zintegrowane środowisko programistyczne), używana dla wszystkich elementów interfejsu, w tym okien dialogowych, menu, okien narzędzi i okien dokumentów. Domyślnie czcionka środowiska jest powiązany czcionki systemowej, który jest wyświetlany jako 9 pt Segoe UI w aktualnych wersjach programu Windows. Przy użyciu jednego czcionki dla wszystkich elementów interfejsu temu wygląd spójny czcionki w całej IDE.

- **Edytor tekstu** — elementy znajdujące się w kodzie i inne edytory tekstowe można dostosować na stronie Edytor tekstu w obszarze **Narzędzia > Opcje**.

- **Określone kolekcje** — okna projektanta, które oferują możliwość dostosowywania elementów interfejsu przez użytkownika, mogą uwidaczniać czcionki specyficzne dla ich powierzchni projektowej na swojej stronie ustawień w obszarze **Narzędzia > Opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie czcionek edytora i zmienianie rozmiaru
 Użytkownicy często będzie powiększyć lub powiększenie rozmiaru i/lub kolor tekstu w edytorze zgodnie z ich preferencji, niezależnie od interfejsu użytkownika ogólne. Ponieważ czcionka środowiska jest używany w przypadku elementów, które mogą być wyświetlane w ramach lub jako część Projektant/edytor, to należy zwrócić uwagę oczekiwane zachowanie, gdy jeden z tych klasyfikacjach czcionki zostanie zmieniona.

 Podczas tworzenia elementów interfejsu użytkownika, które są wyświetlane w edytorze, ale nie są częścią *zawartości*, ważne jest użycie czcionki środowiska, a nie czcionki tekstowej, tak aby elementy zmieniały się w przewidywalny sposób.

1. Kod tekstu w edytorze zmiany rozmiaru z ustawieniem czcionki tekstu kodu i odpowiadać na poziom powiększenia tekst w edytorze.

2. Wszystkie inne elementy interfejsu powinny mieć związek ustawienia czcionki środowisko i reagowanie na zmiany globalne w środowisku. To obejmuje (ale nie jest ograniczona do):

    - Tekst w menu kontekstowe

    - Tekst w zakończeń edytora, takie jak tekst menu żarówki, szybkie znajdowanie okienku Edytora i przejdź do okienka

    - Tekst etykiety w oknach dialogowych, takich jak Znajdź w plikach lub Zrefaktoryzuj

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionka środowiska
 W kodzie macierzystym lub WinFormowym można uzyskać dostęp do czcionki środowiska, wywołując metodę **IUIHostLocale:: GetDialogFont** po wykonaniu zapytania dotyczącego interfejsu z usługi SID_SUIHostLocale.

 W przypadku Windows Presentation Foundation (WPF) należy utworzyć klasę okna dialogowego z klasy **DialogWindow** powłoki zamiast z klasy **okna** WPF.

 W XAML kod wygląda następująco:

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

 Aby wyświetlić okno dialogowe, należy wywołać "**ShowModal ()** " w klasie over **ShowDialog ()** . **ShowModal ()** ustawia poprawny stan modalny w powłoce, zapewnia, że okno dialogowe jest wyśrodkowane w oknie nadrzędnym i tak dalej.

 Kod jest w następujący sposób:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** zwraca wartość logiczną? (wartość null) z **DialogResult**, która może być używana w razie konieczności. Wartość zwracana ma wartość true, jeśli okno dialogowe zostało zamknięte z **przyciskiem OK**.

 Jeśli musisz wyświetlić jakiś interfejs użytkownika WPF, który nie jest oknem dialogowym i jest hostowany we własnym **HwndSource**, na przykład w oknie podręcznym lub oknie PODRZĘDNYm WPF okna nadrzędnego okna dialogowego Win32/WinForms, musisz ustawić **FontFamily** i **FONTSIZE** na elemencie głównym elementu WPF. (Powłoka ustawia właściwości w oknie głównym, ale nie będą dziedziczone ostatnie HWND). Powłoka zawiera zasoby, do których można powiązać właściwości, takie jak to:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="BKMK_Formatting"></a>Formatowanie (skalowanie/pogrubienie) odwołania
 Niektóre okna dialogowe wymaga określonego tekstu pogrubienie lub rozmiar niż czcionka środowiska. Wcześniej czcionki większy niż czcionka środowiska zostały zakodowane jako "czcionka środowiska + 2" lub podobne. Za pomocą fragmentów kodu podanego obsługuje monitorów o dużej rozdzielczości i upewnij się, że tekst wyświetlany zawsze znajduje się na odpowiedni rozmiar i grubość (na przykład światła lub Semilight).

> **Uwaga: przed zastosowaniem formatowania upewnij się, że są spełnione wskazówki znajdujące się w [stylu tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Aby skalować czcionka środowiska, należy ustawić styl TextBlock lub etykiety, jak wskazano. Każda z tych fragmentów kodu, prawidłowo używana, spowoduje wygenerowanie poprawne czcionki, w tym odpowiedni rozmiar i grubość odmiany.

 Gdzie "vsui" to odwołanie do przestrzeni nazw Microsoft.VisualStudio.Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + światła
 **Pojawia się jako:** 34 pt Segoe UI Light

 **Używany dla:** (rzadki) unikatowy interfejs użytkownika, na przykład na stronie startowej

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + światła
 **Pojawia się jako:** 28 pt Segoe UI Light

 **Użyj for:** duże tytuły okna dialogowego z podpisem, główny nagłówek w raportach

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>Czcionka środowiska 200% + Semilight
 **Pojawia się jako:** 18 pt Segoe UI Semilight

 **Używane dla:** podpozycje, tytuły w małych i średnich oknach dialogowych

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>Czcionka środowiska 155%
 **Pojawia się jako:** 14 pt Segoe UI

 **Używane dla:** nagłówki sekcji w interfejsie użytkownika i w raportach

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>Czcionka środowiska 133%
 **Pojawia się jako:** 12 pt Segoe UI

 **Używane dla:** mniejsze podnagłówki w oknach dialogowych sygnatur i interfejsie użytkownika

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>Czcionka środowiska 122%
 **Pojawia się jako:** 11 pt Segoe UI

 **Używane dla:** nagłówki sekcji w oknach dialogowych podpisów, górnych węzłach w widoku drzewa, Nawigacja na kartach pionowych

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Czcionka środowiska + pogrubienia
 **Pojawia się jako:** pogrubiony 9 pt Segoe UI

 **Użycie dla:** etykiet i podtytułów w oknach dialogowych, raportach i INTERFEJSie użytkownika programu Documents

 **Kod proceduralny:** Gdzie "TextBlock" jest wcześniej zdefiniowanym obiektem TextBlock i "label" jest wcześniej zdefiniowaną etykietą.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **Kod XAML:** Ustaw styl bloku textlub Label, jak pokazano.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Style Lokalizowalny
 W niektórych przypadkach lokalizatorzy będzie konieczne zmodyfikowanie style dla różnych ustawień regionalnych, takich jak usuwanie pogrubienie z pliku tekstowego języki wschodnioazjatyckie. Aby umożliwić lokalizowanie style, te style, musi być w pliku resx. Najlepszym sposobem, aby to zrobić i nadal edytować style w projektancie formularzy programu Visual Studio jest jawnie ustawić style czcionek w czasie projektowania. Tworzy obiekt pełną czcionki, i mogą wydawać się przerwać dziedziczenia obiektu nadrzędnego czcionek, tylko właściwość FontStyle umożliwia ustawianie czcionki.

 Rozwiązaniem jest podpinanie zdarzenia **FontChanged** formularza. W zdarzeniu **FontChanged** Przeszukaj wszystkie kontrolki i sprawdź, czy ich czcionka została ustawiona. Jeśli je skonfigurowano, można go zmienić na nowej czcionki na podstawie formularza czcionek i styl czcionki z poprzedniego formantu. Na przykład w kodzie jest:

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

 Przy użyciu tego kodu gwarantuje po zaktualizowaniu czcionki formularza czcionki kontrolek uaktualnią także. Ta metoda powinna być również wywoływana z konstruktora formularza, ponieważ okno dialogowe może nie można pobrać wystąpienia elementu **IUIService** , a zdarzenie **FontChanged** nigdy nie zostanie wywołane. Przeciąganie **FontChanged** umożliwia dialogom dynamiczne pobranie nowej czcionki nawet wtedy, gdy okno dialogowe jest już otwarte.

### <a name="testing-the-environment-font"></a>Testowanie czcionka środowiska
 Aby upewnić się, że interfejs użytkownika używa czcionki środowiskowej i uwzględnia ustawienia rozmiaru, Otwórz **narzędzia > opcje > środowisku > czcionki i kolory** i wybierz pozycję "Czcionka środowiskowa" w menu rozwijanym "Pokaż ustawienia dla:".

 ![Strona czcionek i kolorów w oknie &#62; dialogowym Opcje narzędzi](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201 — a_OptionsFonts")

 **Ustawienia czcionek i kolorów w oknie dialogowym Narzędzia > Opcje**

 Ustaw czcionkę coś, co jest bardzo innych niż domyślne. Aby stał się oczywiste, który nie powoduje aktualizacji interfejsu użytkownika, wybierz czcionkę z szeryfów (na przykład "podzbiory"), a następnie ustaw bardzo duży rozmiar. Następnie przetestuj Twój interfejs użytkownika, aby upewnić się, że jej szanuje środowiska. Oto przykład za pomocą okna dialogowego licencji:

 ![Przykładowe okno dialogowe, które nie używa czcionki środowiska](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201 — b_WrongFontDialog")

 **Przykładowy tekst interfejsu użytkownika, który nie uwzględnia czcionki środowiska**

 W tym przypadku "Informacji użytkownika" i "Informacje o produkcie" nie jest uwzględnienie czcionki. W niektórych przypadkach może to być jawne uzasadnienie wyboru tych elementów, ale może być usterkę, jeśli nie określono jawne czcionki w ramach specyfikacji redline.

 Aby zresetować czcionkę, kliknij przycisk "Użyj ustawień domyślnych" w obszarze **narzędzia > opcje > środowisku > czcionki i kolory**.

## <a name="BKMK_TextStyle"></a>Styl tekstu
 Styl tekstu odnosi się do rozmiaru czcionki, waga i wielkość liter w wyrazie. Aby uzyskać wskazówki dotyczące implementacji, zobacz [Font Environment](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Wielkość liter w wyrazie tekstu

#### <a name="all-caps"></a>Wszystkie wersaliki
 Nie należy używać wszystkie wersaliki na tytuły i etykiety w programie Visual Studio.

#### <a name="all-lowercase"></a>Same małe litery
 Nie należy używać tylko małe litery dla tytułów i etykiet w programie Visual Studio.

#### <a name="sentence-and-title-case"></a>Zdania i tytuł
 Tekst w programie Visual Studio należy używać wielkimi literami lub liter, w zależności od sytuacji.

|Tytuł przypadek użycia:|Zdania przypadek użycia:|
|-------------------------|----------------------------|
|Okno dialogowe tytułów|Etykiety|
|Pola grupy|Pola wyboru|
|Elementy menu|Przyciski radiowe|
|Elementy menu kontekstowego|Elementów pola listy|
|Przyciski|Paski stanu|
|Etykiety tabeli||
|Nagłówki kolumn||
|Etykietki narzędzi||

##### <a name="title-case"></a>Wielkimi literami
 Wielkość liter jest styl z tym pierwsze litery większość lub wszystkie wyrazy w frazę. W programie Visual Studio wielkość liter jest używany dla wielu elementów, w tym:

- **Etykietki narzędzi.** Przykład: "podgląd wybranych elementów"

- **Nagłówki kolumn.** Przykład: "System Response"

- **Elementy menu.** Przykład: "Zapisz wszystko"

  Korzystając z wielkimi literami, poniżej przedstawiono wskazówki dotyczące kiedy na wielką słów i kiedy należy pozostawić je jako małe litery:

|Wielkie litery|Komentarze i przykłady|
|---------------|---------------------------|
|Rzeczowniki wszystkie||
|Wszystkie zlecenia|W tym "Is" i inne formy "Aby być"|
|Wszystkich parametrów|W tym "Nie" i "Po"|
|Wszystkie określeniem|W tym "This" i "That"|
|Wszystkie Zaimki|W tym dzierżawczych "Swojej" również jak"," zmniejszenie zrozumieć "on" i czasownika "is"|
|Pierwszy i ostatni wyraz, niezależnie od tego, w części mowy||
|Przyimkami, które są częścią frazy zlecenia|"Zamyka się Windows wszystkie" lub "Zamykania systemu"|
|Wszystkie litery akronim|HTML, XML, ADRES URL, IDE, RGB|
|Drugi wyraz w wyrazem złożonym, jeśli rzeczownik lub przymiotnik poprawne lub jeśli wyrażenie ma weight równe|Odsyłaczy, oprogramowanie Microsoft wstępne odczytu i zapisu, Run-Time|

|Małe litery|Przykłady|
|---------------|--------------|
|Drugi wyraz wyrazem złożonym, jeśli jest inny część mowy lub participle, modyfikując pierwszy wyraz|Instrukcje odbioru|
|Artykuły, chyba że jeden jest pierwszy wyraz w tytule|,,|
|Spójniki współrzędnych|a, ale, ani, lub|
|Przyimkami słów cztery lub mniej litery poza frazy zlecenia|w na, jak w przypadku, poza, w górnej części|
|"To" stosowania nieskończona frazy|"Jak sformatować dysk twardy"|

##### <a name="sentence-case"></a>Jak w zdaniu
 Jak w zdaniu to metoda standardowa wielkość liter do zapisu w kapitalizowane jest tylko pierwszy wyraz zdania, wraz z dowolnej nazwy własne i zrozumieć "I". Ogólnie rzecz biorąc jak w zdaniu jest łatwiejsze dla odbiorców na całym świecie do odczytu, szczególnie jeśli zawartość zostanie zamienione przez maszynę. Zdania przypadek użycia:

1. **Komunikaty paska stanu.** Są one prostych, krótkich i podaj tylko informacje o stanie. Przykład: ładowanie projektu "pliku"

2. **Wszystkie inne elementy interfejsu użytkownika**, w tym etykiety, pola wyboru, przyciski radiowe i elementy listy. Przykład: "Wybierz wszystkie elementy na liście"

### <a name="text-formatting"></a>Formatowanie tekstu
 Domyślne formatowanie tekstu w Visual Studio 2013 jest kontrolowane przez [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa pomaga zapewnić wygląd czcionki spójne w całym środowisku IDE (zintegrowanym środowiskiem programistycznym), a musi być on zagwarantować spójne środowisko dla użytkowników.

 Domyślny rozmiar używany przez usługi Visual Studio czcionki pochodzi z Windows i jest wyświetlany jako 9 (czas pacyficzny).

 Można zastosować formatowanie do czcionka środowiska. W tym temacie opisano, jak i gdzie można stosować style. Aby uzyskać informacje o implementacji, zapoznaj się z [czcionką środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tekst pogrubiony
 Tekst pogrubiony jest rzadko używana w programie Visual Studio i powinna być zarezerwowana dla:

- etykiety pytanie w kreatorach

- Wyznaczanie aktywny projekt w Eksploratorze rozwiązań

- zastąpić wartości w oknie narzędzia właściwości

- wystąpienia określonych zdarzeń na listach rozwijanych w Edytorze Visual Basic

- generowane przez serwer zawartości w konspekt dokumentu dla stron sieci web

- nagłówki sekcji w oknie dialogowym złożonych lub Projektant interfejsu użytkownika

#### <a name="italics"></a>Kursywa
 Program Visual Studio nie korzysta z kursywą lub pogrubiony tekst kursywą.

#### <a name="color"></a>Kolor

- Niebieski jest zarezerwowany dla hiperlinków (Nawigacja i polecenia) i nigdy nie należy używać w przypadku orientacji.

- Większe nagłówki (czcionka środowiska x 155% lub nowszej) można kolorowe do tych celów:

  - Aby zapewnić estetyczny podpisu w interfejsie użytkownika Visual Studio

  - Aby zwrócić uwagę na określonym obszarze

  - Oferowanie zwolnienia z kolor tekstu standardowego środowiska szary/czarny ciemny

- Kolor w nagłówkach należy korzystać z istniejących programu Visual Studio kolory firmowe, przede wszystkim purpurowy głównej #FF68217A.

- Korzystając z koloru w nagłówkach, należy przestrzegać [wytycznych dotyczących kolorów systemu Windows](https://msdn.microsoft.com/library/dn742482.aspx), w tym współczynnika kontrastu i innych zagadnień dotyczących ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Visual Studio UI projektu funkcji jaśniejszy wygląd więcej białymi znakami. Jeśli to możliwe, chrome i paska tytułu zostały obniżone lub usunięte. Gdy gęstość informacji jest wymagane w programie Visual Studio, typografii jest nadal ważny, z naciskiem na bardziej otwarty i ustawić odmianą rozmiary czcionek i wagi.

 W poniższych tabelach zawiera szczegóły projektu oraz przykłady visual display czcionek używane w programie Visual Studio. Warianty czcionki wyświetlania mają rozmiar i wagi, takie jak Semilight lub światła, kodowane do ich występowania.

 Fragmenty kodu implementacji dla wszystkich czcionek wyświetlanych można znaleźć w temacie [Formatowanie (skalowanie/pogrubienie)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + światła

|||
|-|-|
|**Użycie:** Rzadko. Unikatowe marki tylko interfejs użytkownika.<br /><br /> **Nie**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika inne niż podpisu interfejsu użytkownika, takie jak strona początkowa<br />-Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 34 pt Segoe UI Light<br /><br /> **Przykład wizualizacji:**<br /><br /> *Obecnie nie jest używana. Może być używany na stronie startowej.*|

#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + światła

|||
|-|-|
|**Wykorzystywani**<br /><br /> — Większa nagłówka w oknach dialogowych podpisu<br />— Nagłówek raport główny<br /><br /> **Nie**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika inne niż podpisu interfejsu użytkownika, takie jak strona początkowa<br />-Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 28 pt Segoe UI Light<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka &#43; światła 310% środowiska](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202 — a_EF310")|

#### <a name="200-environment-font--semilight"></a>Czcionka środowiska 200% + Semilight

|||
|-|-|
|**Wykorzystywani**<br /><br /> -Podpozycji<br />-Tytuły w małych i średnich okien dialogowych<br /><br /> **Nie**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj Semilight wagi<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 18 pt Segoe UI Semillight<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład Semilight czcionki &#43; środowiska 200%](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202 — b_EF200")|

#### <a name="155-environment-font"></a>Czcionka środowiska 155%

|||
|-|-|
|**Wykorzystywani**<br /><br /> -Section nagłówków w dokumencie dobrze interfejsu użytkownika<br />— Raporty<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 14 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 155%](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202 — c_EF155")|

#### <a name="133-environment-font"></a>Czcionka środowiska 133%

|||
|-|-|
|**Wykorzystywani**<br /><br /> — Mniejsze podpozycji w oknach dialogowych podpisu<br />— Mniejsze podpozycji w dokumencie dobrze interfejsu użytkownika<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 12 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 133%](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202 — d_EF133")|

#### <a name="122-environment-font"></a>Czcionka środowiska 122%

|||
|-|-|
|**Wykorzystywani**<br /><br /> -Section nagłówków w oknach dialogowych podpisu<br />-Najważniejsze węzły w widoku drzewa<br />-Pionowej karcie nawigacji<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** 11 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład nagłówka czcionki środowiska 122%](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202 — e_EF122")|

#### <a name="environment-font--bold"></a>Czcionka środowiska + pogrubienia

|||
|-|-|
|**Wykorzystywani**<br /><br /> -Etykiet oraz nagłówki w oknach dialogowych podpisu<br />-Etykiet oraz nagłówki w raportach<br />-Etykiet i podnagłówkami w dokumencie dobrze interfejsu użytkownika<br /><br /> **Nie**<br /><br /> -Użyj zdaniu<br />-Użyj wagi pogrubienia<br /><br /> **Nie:**<br /><br /> -Kursywa kursywą lub pogrubienia<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** pogrubiony 9 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład pogrubionego nagłówka &#43; czcionki środowiska](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202 — f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiska

|||
|-|-|
|**Użycie:** Cały tekst<br /><br /> **Do:** Użyj przypadku zdania<br /><br /> **Nie należy:** Kursywa lub pogrubiona kursywa|**Pojawia się jako:** 9 pt Segoe UI<br /><br /> **Przykład wizualizacji:**<br /><br /> ![Przykład czcionki środowiska](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202 — g_EF")|

### <a name="padding-and-spacing"></a>Wypełnienie i odstępy
 Nagłówki wymagają ilość wolnego miejsca wokół je, aby dać im odpowiednią wyróżnienia. Miejsce to różni się zależnie od rozmiaru punktów i co jeszcze jest bliski nagłówka, takich jak linii poziomej lub wiersza tekstu w czcionce środowiska.

- Idealne uzupełnienie nagłówek samodzielnie powinna być 90% miejsca wysokość kapitałowych znaków. Na przykład nagłówek Segoe UI Light 28 (czas pacyficzny) ma limit wysokości 26 (czas pacyficzny) i uzupełnienie należy około 23 (czas pacyficzny) lub około 31 pikseli.

- Minimalna ilość miejsca wokół nagłówek powinien wynosić 50% kapitałowych wielkość czcionki. Może być używany mniej miejsca, jeżeli nagłówek towarzyszy regułę lub inny element ściśle dopasowane.

- Pogrubiony tekst czcionka środowiska powinien być zgodny z domyślną interlinia wysokość i uzupełniania.

## <a name="see-also"></a>Zobacz też
 [MSDN: czcionki (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: tekst interfejsu użytkownika (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
