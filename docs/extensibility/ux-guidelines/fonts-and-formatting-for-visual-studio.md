---
title: Czcionki i formatowanie dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f510568c977579fa3e48d57db548040d16dcb574
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335491"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowanie dla programu Visual Studio
## <a name="BKMK_TheEnvironmentFont"></a> Czcionka środowiska
 Wszystkie czcionki w programie Visual Studio muszą być widoczne dla użytkownika na potrzeby dostosowywania. To przede wszystkim odbywa się za pośrednictwem **czcionki i kolory** strony w **Narzędzia > Opcje** okna dialogowego. Są trzy główne kategorie ustawienia czcionek:

- **Czcionka środowiska** -głównej czcionkę dla środowiska IDE (zintegrowanym środowiskiem programistycznym), dla wszystkich elementów interfejsu, w tym okna dialogowe, menu, okien narzędzi i oknami dokumentu. Domyślnie czcionka środowiska jest powiązany czcionki systemowej, który jest wyświetlany jako 9 pt Segoe UI w aktualnych wersjach programu Windows. Przy użyciu jednego czcionki dla wszystkich elementów interfejsu temu wygląd spójny czcionki w całej IDE.

- **Edytor tekstu** — czy powierzchni w kodzie i innych edytorów tekstowych można dostosować w edytorze tekstu elementów strony w **Narzędzia > Opcje**.

- **Określonych kolekcji** -powierzchni projektanta systemu windows, które oferują dostosowywania ich elementy interfejsu użytkownika może narazić czcionki specyficzne dla ich projektu, w ich własnych strony ustawień w **Narzędzia > Opcje**.

### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie czcionek edytora i zmienianie rozmiaru
 Użytkownicy często będzie powiększyć lub powiększenie rozmiaru i/lub kolor tekstu w edytorze zgodnie z ich preferencji, niezależnie od interfejsu użytkownika ogólne. Ponieważ czcionka środowiska jest używany w przypadku elementów, które mogą być wyświetlane w ramach lub jako część Projektant/edytor, to należy zwrócić uwagę oczekiwane zachowanie, gdy jeden z tych klasyfikacjach czcionki zostanie zmieniona.

 Podczas tworzenia elementów interfejsu użytkownika, które pojawiają się w edytorze, ale nie są niebędące częścią *zawartości*, ważne jest, aby użyć czcionka środowiska i nie czcionki tekstu, aby elementy zmiany rozmiaru w przewidywalny sposób.

1. Kod tekstu w edytorze zmiany rozmiaru z ustawieniem czcionki tekstu kodu i odpowiadać na poziom powiększenia tekst w edytorze.

2. Wszystkie inne elementy interfejsu powinny mieć związek ustawienia czcionki środowisko i reagowanie na zmiany globalne w środowisku. To obejmuje (ale nie jest ograniczona do):

    - Tekst w menu kontekstowe

    - Tekst w zakończeń edytora, takie jak żarówki tekst menu, okienka edytora szybkiego wyszukiwania i przejdź do okienka

    - Etykieta tekst w oknach dialogowych, takich jak **Znajdź w plikach** lub **refaktoryzacji**

### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do czcionka środowiska
 W kodzie natywnym, czy WinForms, czcionka środowiska może zostać oceniony przez wywołanie metody `IUIHostLocale::GetDialogFont` po wykonaniu zapytania względem interfejsu z `SID_SUIHostLocale` usługi.

 Dla Windows Presentation Foundation (WPF), pochodzi z klasy okna dialogowego z poziomu powłoki `DialogWindow` klasy zamiast firmy WPF `Window` klasy.

 W XAML kod wygląda następująco:

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

Kod:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Zastąp `Microsoft.VisualStudio.Shell.11.0` z bieżącą wersją biblioteki dll MPF.)

 Aby wyświetlić okno dialogowe, należy wywołać "`ShowModal()`" w klasie za pośrednictwem `ShowDialog()`. `ShowModal()` Ustawia stan modalny w powłoce, gwarantuje, że okno dialogowe jest wyśrodkowywana w okno nadrzędne i tak dalej.

 Kod jest w następujący sposób:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` Zwraca wartość typu wartość logiczna? (wartość logiczna dopuszczającego wartość null) z `DialogResult`, których można używać w razie potrzeby. Wartość zwracana jest wartość true, jeśli okno dialogowe zostało zamknięte z **OK**.

 Jeśli chcesz wyświetlić niektórych WPF UI, który nie jest wyświetlone okno dialogowe i znajduje się w jego własnej `HwndSource`, np. oknie podręcznym lub okna podrzędnego WPF w Win32/WinForms okna nadrzędnego, należy ustawić `FontFamily` i `FontSize` dla elementu głównego elementu WPF. (Powłoka ustawia właściwości w oknie głównym, ale nie będą dziedziczone ostatnie `HWND`). Powłoka zawiera zasoby, do których można powiązać właściwości, takie jak to:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="BKMK_Formatting"></a> Formatowanie odwołania (skalowanie/pogrubienie)
 Niektóre okna dialogowe wymaga określonego tekstu pogrubienie lub rozmiar niż czcionka środowiska. Wcześniej czcionki większy niż czcionka środowiska zostały zakodowane jako "`environment font +2`" lub podobne. Korzystania z fragmentów kodu podanego obsługuje monitorów o dużej rozdzielczości i upewnij się, że tekst wyświetlany zawsze znajduje się na właściwy rozmiar i grubość (na przykład lub Semilight światła).

> **Uwaga: Przed zastosowaniem formatowania, upewnij się, są następujące wskazówki w [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Aby skalować czcionka środowiska, należy ustawić styl TextBlock lub etykiety, jak wskazano. Każda z tych fragmentów kodu, prawidłowo używana, spowoduje wygenerowanie poprawne czcionki, w tym odpowiedni rozmiar i grubość odmiany.

 Gdzie "`vsui`" to odwołanie do przestrzeni nazw `Microsoft.VisualStudio.Shell`:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + światła

**Wygląda następująco:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Na użytek:** (rzadkiego) unikatowy marki interfejsu użytkownika, takie jak w stronę początkową

::: moniker-end

::: moniker range=">=vs-2019"

**Na użytek:** (rzadkiego) unikatowy marki interfejsu użytkownika

::: moniker-end

**Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + światła
 **Wygląda następująco:** 28 (czas pacyficzny) Segoe UI Light **na użytek:** tytułów okna dialogowego podpisu dużych, głównym, nagłówkiem w raportach

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>Czcionka środowiska 200% + Semilight
 **Wygląda następująco:** 18 pkt Segoe UI Semilight **na użytek:** podpozycji, tytułu w małych i średnich okien dialogowych

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>Czcionka środowiska 155%
 **Wygląda następująco:** 14 punktów Segoe UI **na użytek:** nagłówki sekcji w dokumencie również interfejs użytkownika lub raportów

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>Czcionka środowiska 133%
 **Wygląda następująco:** 12 pkt. Segoe UI **na użytek:** mniejszych podpozycji w dokumencie i okna dialogowe sygnatury dobrze interfejsu użytkownika

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>Czcionka środowiska 122%
 **Wygląda następująco:** 11 (czas pacyficzny) Segoe UI **na użytek:** sekcji nagłówków w oknach dialogowych podpisu, najważniejsze węzły w widoku drzewa, tabulator pionowy nawigacji

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Czcionka środowiska + pogrubienia
 **Pojawia się jako:** pogrubiony 9 (czas pacyficzny) Segoe UI **na użytek:** etykiet oraz nagłówki w oknach dialogowych podpisu, raporty i dokumentu dobrze interfejsu użytkownika

 **Kod proceduralny:** Gdzie `textBlock` to uprzednio zdefiniowany TextBlock i `label` jest uprzednio zdefiniowanej etykiety:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Ustaw styl TextBlock lub etykiety, jak pokazano:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Style Lokalizowalny
 W niektórych przypadkach lokalizatorzy będzie konieczne zmodyfikowanie style dla różnych ustawień regionalnych, takich jak usuwanie pogrubienie z pliku tekstowego języki wschodnioazjatyckie. Aby umożliwić lokalizowanie style, te style, musi być w pliku resx. Najlepszym sposobem, aby to zrobić i nadal edytować style w projektancie formularzy programu Visual Studio jest jawnie ustawić style czcionek w czasie projektowania. Tworzy obiekt pełną czcionki, i mogą wydawać się przerwać dziedziczenia obiektu nadrzędnego czcionek, tylko właściwość FontStyle umożliwia ustawianie czcionki.

 Rozwiązanie polega na połączeniu formularza okna dialogowego `FontChanged` zdarzeń. W `FontChanged` zdarzeń, zapoznaj się z wszystkich kontrolek i sprawdź, jeśli ustawiono ich czcionki. Jeśli je skonfigurowano, można go zmienić na nowej czcionki na podstawie formularza czcionek i styl czcionki z poprzedniego formantu. Na przykład w kodzie jest:

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

 Przy użyciu tego kodu gwarantuje po zaktualizowaniu czcionki formularza czcionki kontrolek uaktualnią także. Ta metoda również powinien zostać wywołany z konstruktora formularza, ponieważ okno dialogowe może nie można pobrać wystąpienia `IUIService` i `FontChanged` zdarzenia nigdy nie zostanie uruchomiony. Przechwytywanie `FontChanged` umożliwi wyświetlanie okien dialogowych dynamicznie przejmą nowej czcionki, nawet jeśli jest już otwarte okno dialogowe.

### <a name="testing-the-environment-font"></a>Testowanie czcionka środowiska
 Aby upewnić się, że Twój interfejs użytkownika korzysta z czcionka środowiska i uwzględnia ustawienia rozmiaru, otwórz **Narzędzia > Opcje > środowisko > czcionki i kolory** i wybierz pozycję "Czcionka środowiska" w obszarze "Pokaż ustawienia dla:" menu rozwijanego.

 ![Ustawienia czcionek i kolorów w narzędziach &gt; okna dialogowego Opcje](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />Ustawienia czcionek i kolorów w narzędziach &gt; okno dialogowe Opcje

 Ustaw czcionkę coś, co jest bardzo innych niż domyślne. Aby stał się oczywiste, który nie powoduje aktualizacji interfejsu użytkownika, wybierz czcionkę z szeryfów (na przykład "podzbiory"), a następnie ustaw bardzo duży rozmiar. Następnie przetestuj Twój interfejs użytkownika, aby upewnić się, że jej szanuje środowiska. Oto przykład za pomocą okna dialogowego licencji:

 ![Przykładowy tekst interfejsu użytkownika, który nie uwzględnia czcionka środowiska](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />Przykładowy tekst interfejsu użytkownika, który nie uwzględnia czcionka środowiska

 W tym przypadku "Informacji użytkownika" i "Informacje o produkcie" nie jest uwzględnienie czcionki. W niektórych przypadkach może to być jawne uzasadnienie wyboru tych elementów, ale może być usterkę, jeśli nie określono jawne czcionki w ramach specyfikacji redline.

 Aby zresetować czcionki, kliknij przycisk "Użyj ustawień domyślnych" w obszarze **Narzędzia > Opcje > środowisko > czcionki i kolory**.

## <a name="BKMK_TextStyle"></a> Styl tekstu
 Styl tekstu odnosi się do rozmiaru czcionki, waga i wielkość liter w wyrazie. Aby uzyskać wytyczne dotyczące implementacji, zobacz [czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

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

- **Etykietki narzędzi.** Przykład: "Podgląd wybranych elementów"

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

1. **Komunikaty paska stanu.** Są one prostych, krótkich i podaj tylko informacje o stanie. Przykład: "Trwa ładowanie pliku projektu"

2. **Wszystkie inne elementy interfejsu użytkownika**, łącznie z etykiety, pola wyboru i przyciski radiowe i wyświetlać listę elementów pola. Przykład: "Wybierz wszystkie elementy na liście"

### <a name="text-formatting"></a>Formatowanie tekstu
 Domyślne formatowania tekstu w programie Visual Studio 2013 jest kontrolowana przez [czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa pomaga zapewnić wygląd czcionki spójne w całym środowisku IDE (zintegrowanym środowiskiem programistycznym), a musi być on zagwarantować spójne środowisko dla użytkowników.

 Domyślny rozmiar używany przez usługi Visual Studio czcionki pochodzi z Windows i jest wyświetlany jako 9 (czas pacyficzny).

 Można zastosować formatowanie do czcionka środowiska. W tym temacie opisano, jak i gdzie można stosować style. Aby uzyskać informacje o implementacji, zapoznaj się [czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tekst pogrubiony
 Tekst pogrubiony jest rzadko używana w programie Visual Studio i powinna być zarezerwowana dla:

- etykiety pytanie w kreatorach

- Wyznaczanie aktywny projekt w Eksploratorze rozwiązań

- zastąpić wartości w oknie narzędzia właściwości

- Niektóre zdarzenia w list rozwijanych w Edytorze Visual Basic

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

- Używając koloru w nagłówkach, musisz spełnić [Windows kolor wytycznych](/windows/desktop/uxguide/vis-color), w tym współczynnik kontrastu i inne zagadnienia dotyczące ułatwień dostępu.

### <a name="font-size"></a>Rozmiar czcionki
 Visual Studio UI projektu funkcji jaśniejszy wygląd więcej białymi znakami. Jeśli to możliwe, chrome i paska tytułu zostały obniżone lub usunięte. Gdy gęstość informacji jest wymagane w programie Visual Studio, typografii jest nadal ważny, z naciskiem na bardziej otwarty i ustawić odmianą rozmiary czcionek i wagi.

 W poniższych tabelach zawiera szczegóły projektu oraz przykłady visual display czcionek używane w programie Visual Studio. Warianty czcionki wyświetlania mają rozmiar i wagi, takie jak Semilight lub światła, kodowane do ich występowania.

 Fragmenty kodu wdrożenia dla wszystkich czcionek wyświetlania można znaleźć w [formatowanie odwołania (skalowanie/pogrubienie)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + światła

|||
|-|-|
|**Sposób użycia:** Rzadkie. Unikatowe marki tylko interfejs użytkownika.<br /><br /> **Należy wykonać:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika inne niż podpisu interfejsu użytkownika, takie jak strona początkowa<br />-Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 34 pt Segoe UI Light<br /><br /> **Przykład Visual:**<br /><br /> *Obecnie nieużywane. Mogą być używane w Visual Studio 2017 strony początkowej.*|

#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + światła

::: moniker range="vs-2017"

|||
|-|-|
|**Sposób użycia:**<br /><br /> — Większa nagłówka w oknach dialogowych podpisu<br />— Nagłówek raport główny<br /><br /> **Należy wykonać:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika inne niż podpisu interfejsu użytkownika, takie jak strona początkowa<br />-Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 28 pt Segoe UI Light<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionka środowiska 310% &#43; światła nagłówek](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Sposób użycia:**<br /><br /> — Większa nagłówka w oknach dialogowych podpisu<br />— Nagłówek raport główny<br /><br /> **Należy wykonać:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika inne niż podpisu interfejsu użytkownika<br />-Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 28 pt Segoe UI Light<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionka środowiska 310% &#43; światła nagłówek](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>Czcionka środowiska 200% + Semilight

|||
|-|-|
|**Sposób użycia:**<br /><br /> -Podpozycji<br />-Tytuły w małych i średnich okien dialogowych<br /><br /> **Należy wykonać:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj Semilight wagi<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 18 pkt Segoe UI Semillight<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionka środowiska 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|

#### <a name="155-environment-font"></a>Czcionka środowiska 155%

|||
|-|-|
|**Sposób użycia:**<br /><br /> -Section nagłówków w dokumencie dobrze interfejsu użytkownika<br />— Raporty<br /><br /> **Należy wykonać:** Stosuj wielkość liter<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 14 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład 155% środowiska czcionki nagłówka](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|

#### <a name="133-environment-font"></a>Czcionka środowiska 133%

|||
|-|-|
|**Sposób użycia:**<br /><br /> — Mniejsze podpozycji w oknach dialogowych podpisu<br />— Mniejsze podpozycji w dokumencie dobrze interfejsu użytkownika<br /><br /> **Należy wykonać:** Stosuj wielkość liter<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 12 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład 133% środowiska czcionki nagłówka](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|

#### <a name="122-environment-font"></a>Czcionka środowiska 122%

|||
|-|-|
|**Sposób użycia:**<br /><br /> -Section nagłówków w oknach dialogowych podpisu<br />-Najważniejsze węzły w widoku drzewa<br />-Pionowej karcie nawigacji<br /><br /> **Należy wykonać:** Stosuj wielkość liter<br /><br /> **Nie:**<br /><br /> -Pogrubienie, kursywę lub pogrubienie, kursywa<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Wygląda następująco:** 11 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład 122% środowiska czcionki nagłówka](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|

#### <a name="environment-font--bold"></a>Czcionka środowiska + pogrubienia

|||
|-|-|
|**Sposób użycia:**<br /><br /> -Etykiet oraz nagłówki w oknach dialogowych podpisu<br />-Etykiet oraz nagłówki w raportach<br />-Etykiet i podnagłówkami w dokumencie dobrze interfejsu użytkownika<br /><br /> **Należy wykonać:**<br /><br /> -Użyj zdaniu<br />-Użyj wagi pogrubienia<br /><br /> **Nie:**<br /><br /> -Kursywa kursywą lub pogrubienia<br />-Na użytek tekst podstawowy<br />— Użyj w formantów standardowych programu Visual Studio<br />— Użyj w oknach narzędzi|**Pojawia się jako:** pogrubiony 9 (czas pacyficzny) Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionka środowiska &#43; pogrubiony nagłówek](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|

#### <a name="environment-font"></a>Czcionka środowiska

|||
|-|-|
|**Sposób użycia:** Inny tekst<br /><br /> **Należy wykonać:** Stosuj wielkość liter<br /><br /> **Nie:** Krojów z kursywą lub pogrubienie, kursywa|**Wygląda następująco:** 9 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionka środowiska](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|

### <a name="padding-and-spacing"></a>Wypełnienie i odstępy
 Nagłówki wymagają ilość wolnego miejsca wokół je, aby dać im odpowiednią wyróżnienia. Miejsce to różni się zależnie od rozmiaru punktów i co jeszcze jest bliski nagłówka, takich jak linii poziomej lub wiersza tekstu w czcionce środowiska.

- Idealne uzupełnienie nagłówek samodzielnie powinna być 90% miejsca wysokość kapitałowych znaków. Na przykład nagłówek Segoe UI Light 28 (czas pacyficzny) ma limit wysokości 26 (czas pacyficzny) i uzupełnienie należy około 23 (czas pacyficzny) lub około 31 pikseli.

- Minimalna ilość miejsca wokół nagłówek powinien wynosić 50% kapitałowych wielkość czcionki. Może być używany mniej miejsca, jeżeli nagłówek towarzyszy regułę lub inny element ściśle dopasowane.

- Pogrubiony tekst czcionka środowiska powinien być zgodny z domyślną interlinia wysokość i uzupełniania.

## <a name="see-also"></a>Zobacz także

- [MSDN: Czcionki (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Tekst interfejsu użytkownika (Windows)](/windows/desktop/uxguide/text-ui)
