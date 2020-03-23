---
title: Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: feb7785678be4b6f2c26bbcff93bf7d3e6632116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589620"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz kodowane testowanie formantów interfejsu użytkownika

Zaimplementuj obsługę struktury testowania kodowanych interfejsu użytkownika, aby formant był bardziej sprawdzalny. Przyrostowo można dodawać rosnące poziomy wsparcia. Zacznij od obsługi rekordu i odtwarzania oraz sprawdzania poprawności właściwości. Następnie należy oprzeć się na tym, aby włączyć konstruktora testów kodowanych interfejsu użytkownika do rozpoznawania właściwości niestandardowych formantu. Podaj niestandardowe klasy, aby uzyskać dostęp do tych właściwości z wygenerowanego kodu. Można również pomóc kodowane kreatora testów interfejsu użytkownika przechwytywania akcji w sposób, który jest bliżej intencji akcji rejestrowane.

![CUIT&#95;Pełny](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Obsługa rekordów i odtwarzania oraz sprawdzania poprawności właściwości przez wdrożenie ułatwień dostępu

Konstruktor testów kodowanych interfejsu użytkownika przechwytuje informacje o formantach, które napotka podczas nagrywania, a następnie generuje kod do odtworzenia tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, konstruktor kodowanych testów interfejsu użytkownika przechwytuje akcje (takie jak kliknięcia myszą) przy użyciu współrzędnych ekranu. Podczas odtwarzania testu wygenerowany kod wystawia akcje we współrzędnych tego samego ekranu. Jeśli formant pojawia się w innym miejscu na ekranie podczas odtwarzania testu, wygenerowany kod nie wykona akcji. Nie implementując ułatwień dostępu dla formantu, mogą pojawić się błędy testu, jeśli test jest odtwarzany w różnych konfiguracjach ekranu, w różnych środowiskach lub po zmianie układu interfejsu użytkownika.

![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Jeśli zaimplementujesz ułatwienia dostępu, konstruktor testów kodowanych interfejsu użytkownika używa tego do przechwytywania informacji o formancie podczas rejestrowania testu. Następnie po uruchomieniu testu wygenerowany kod będzie odtwarzać te zdarzenia względem formantu, nawet jeśli znajduje się w innym miejscu w interfejsie użytkownika. Autorzy testów można również utworzyć potwierdzenia przy użyciu podstawowych właściwości formantu.

![Rekord cuit&#95;](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Do obsługi rekordów i odtwarzania, sprawdzania poprawności właściwości i nawigacji dla formantu Windows Forms
Zaimplementuj dostępność dla formantu, jak opisano <xref:System.Windows.Forms.AccessibleObject>w poniższej procedurze i wyjaśniono szczegółowo w .

![CUIT&#95;dostępne](../test/media/cuit_accessible.png)

1. Zaimplementuj <xref:System.Windows.Forms.Control.ControlAccessibleObject>klasę, która wywodzi się z , i zastąpić <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwość, aby zwrócić obiekt klasy.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Zastądeń obiekt <xref:System.Windows.Forms.AccessibleObject.Role%2A>dostępowy <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> oraz <xref:System.Windows.Forms.AccessibleObject.State%2A>właściwości i metody.

3. Zaimplementuj inny obiekt ułatwień dostępu dla <xref:System.Windows.Forms.Control.AccessibilityObject%2A> formantu podrzędnego i zastąży właściwość formantu podrzędnego, aby zwrócić obiekt ułatwień dostępu.

4. Zastądnie <xref:System.Windows.Forms.AccessibleObject.Name%2A> <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A> <xref:System.Windows.Forms.AccessibleObject.Bounds%2A> <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, <xref:System.Windows.Forms.AccessibleObject.Select%2A> , i właściwości i metody dla obiektu ułatwień dostępu formantu podrzędnego.

> [!NOTE]
> Ten temat rozpoczyna się od <xref:System.Windows.Forms.AccessibleObject>przykładu ułatwień dostępu w programie , a następnie opiera się na tym przykładzie w pozostałych procedurach. Jeśli chcesz utworzyć roboczą wersję przykładu ułatwień dostępu, utwórz aplikację konsoli, a następnie zastąp kod w *Program.cs* przykładowym kodem. Dodaj odwołania do aplikacji Accessibility, System.Drawing i System.Windows.Forms. Zmień **osadzanie typów międzyop dla** ułatwień dostępu do **false,** aby wyeliminować ostrzeżenie kompilacji. Typ danych wyjściowych projektu można zmienić z **aplikacji konsoli** na aplikację **systemu Windows,** tak aby okno konsoli nie było wyświetlane po uruchomieniu aplikacji.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Obsługa sprawdzania poprawności właściwości niestandardowej przez implementowanie dostawcy właściwości

Po zaimplementowanie podstawowej obsługi rekordów i odtwarzania i sprawdzania poprawności właściwości, można udostępnić właściwości <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> niestandardowe formantu do kodowanych testów interfejsu użytkownika, implementując wtyczkę. Na przykład poniższa procedura tworzy dostawcę właściwości, który umożliwia kodowane testy interfejsu użytkownika, aby uzyskać dostęp do właściwości State formantów podrzędnych CurveLegend formantu curvelegend:

![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Aby obsługiwać sprawdzanie poprawności właściwości niestandardowych

![Rekwizyty&#95;CUIT](../test/media/cuit_props.png)

1. Zastąp <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwość obiektu dostępnego do legendy krzywej, aby przekazać wartości właściwości rich w ciągu opisu. Oddziel wiele wartości średnikami (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Utwórz pakiet rozszerzenia testu interfejsu użytkownika dla formantu, tworząc projekt biblioteki klas. Dodaj odwołania do accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common i Microsoft.VisualStudio.TestTools.Extension. Zmień **typy osadzania międzyop dla** ułatwień dostępu na **False**.

1. Dodaj klasę dostawcy właściwości, która <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>pochodzi od:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Zaimplementuj dostawcę właściwości, umieszczając <xref:System.Collections.Generic.Dictionary%602>nazwy właściwości i deskryptory właściwości w pliku .

1. Zastąd, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> aby wskazać, że zestaw zapewnia obsługę specyficzne dla kontroli dla formantu i jego śmiga.

1. Zastądić pozostałe abstrakcyjne metody<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Dodaj klasę pakietu rozszerzenia, która <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>pochodzi od programu .

1. Zdefiniuj `UITestExtensionPackage` atrybut dla zestawu.

1. W klasie pakietu rozszerzenia, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> zastąpić, aby zwrócić klasę dostawcy właściwości, gdy dostawca właściwości jest wymagane.

1. Zastąd w pozostałych abstrakcyjnych <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>metodach i właściwościach pliku .

1. Tworzenie plików binarnych i kopiowanie ich do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Ten pakiet rozszerzeń jest stosowany do dowolnego formantu, który jest typu "Tekst". Jeśli testujesz wiele formantów tego samego typu, przetestuj je oddzielnie, dzięki czemu można zarządzać, które pakiety rozszerzenia są wdrażane podczas rejestrowania testów.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Obsługa generowania kodu przez implementowanie klasy w celu uzyskania dostępu do właściwości niestandardowych

Gdy konstruktor testów kodowanych interfejsu użytkownika generuje kod z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> nagrania sesji, używa klasy, aby uzyskać dostęp do formantów.

Jeśli zaimplementowano dostawcę właściwości, aby zapewnić dostęp do właściwości niestandardowych formantu, można dodać wyspecjalizowaną klasę, która jest używana do uzyskiwania dostępu do tych właściwości. Dodawanie wyspecjalizowanej klasy upraszcza wygenerowany kod.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać wyspecjalizowaną klasę, aby uzyskać dostęp do kontroli

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Zaimplementuj klasę, <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> która pochodzi od i dodać typ formantu do kolekcji właściwości wyszukiwania w konstruktorze.

1. Zaimplementuj właściwości niestandardowe formantu jako właściwości klasy.

1. Zastąpuj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę dostawcy właściwości, aby zwrócić typ nowej klasy dla formantów podrzędnych legendy krzywej.

1. Zastąpuj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę dostawcy właściwości, aby zwrócić typ metody PropertyNames nowej klasy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Obsługa akcji z uwzględnieniem intencji przez implementowanie filtru akcji

Gdy program Visual Studio rejestruje test, przechwytuje każde zdarzenie myszy i klawiatury. Jednak w niektórych przypadkach intencji akcji mogą zostać utracone w serii zdarzeń myszy i klawiatury. Na przykład jeśli formant obsługuje autouzupełnianiu, ten sam zestaw zdarzeń myszy i klawiatury może spowodować inną wartość, gdy test jest odtwarzany w innym środowisku. Można dodać wtyczkę filtru akcji, która zastępuje serię zdarzeń klawiatury i myszy jedną akcją. W ten sposób można zastąpić serię zdarzeń myszy i klawiatury, które wybierają wartość, pojedynczą akcją ustawianą wartość. W ten sposób chroni kodowane testy interfejsu użytkownika przed różnicami w autouzupełnianiu z jednego środowiska do drugiego.

### <a name="to-support-intent-aware-actions"></a>Aby wspierać działania z uwzględnieniem intencji

![Działania&#95;CUIT](../test/media/cuit_actions.png)

1. Zaimplementuj klasę filtru akcji, która pochodzi z [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), zastępując właściwości [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) i [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Zastąrpuj [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). Przykład w tym miejscu zastępuje akcję dwukrotnego kliknięcia akcją pojedynczego kliknięcia.

1. Dodaj filtr akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> do metody pakietu rozszerzeń.

1. Tworzenie plików binarnych i kopiowanie ich do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akcji nie zależy od implementacji ułatwień dostępu ani od dostawcy właściwości.

## <a name="debug-your-property-provider-or-action-filter"></a>Debugowanie dostawcy właściwości lub filtru akcji

Dostawca właściwości i filtr akcji są implementowane w pakiecie rozszerzenia. Konstruktor testów uruchamia pakiet rozszerzenia w oddzielnym procesie od aplikacji.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować dostawcę właściwości lub filtr akcji

1. Tworzenie wersji debugowania pakietu rozszerzeń kopiuje pliki *.dll* i *pdb* do *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Uruchom aplikację (nie w debugerze).

3. Uruchom konstruktora testów interfejsu użytkownika.

     `codedUITestBuilder.exe  /standalone`

4. Dołącz debuger do procesu codedUITestBuilder.

5. Ustaw punkty przerwania w kodzie.

6. W konstruktorze testów kodowanych interfejsu użytkownika utwórz potwierdzenia, aby wykonywać dostawcę właściwości i rejestrować akcje, aby wykonywać filtry akcji.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.AccessibleObject>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
