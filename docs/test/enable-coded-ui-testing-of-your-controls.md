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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589620"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek

Zaimplementuj obsługę kodowanego środowiska testowania interfejsu użytkownika, aby formant był bardziej weryfikowalne. Można zwiększyć przyrostowy poziom wsparcia. Zacznij od obsługi rekordu i odtwarzania oraz walidacji właściwości. Następnie Skompiluj, aby włączyć konstruktora kodowanego testu interfejsu użytkownika w celu rozpoznania niestandardowych właściwości kontrolki. Zapewnianie klas niestandardowych do uzyskiwania dostępu do tych właściwości z wygenerowanego kodu. Można także ułatwić zamierzone działanie funkcji przechwytywania konstruktora testów interfejsu użytkownika w sposób zbliżony do zamiaru rejestrowania akcji.

![CUIT&#95;pełna](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Obsługa rejestrowania i odtwarzania oraz walidacji właściwości przez implementację ułatwień dostępu

Konstruktor kodowanego testu interfejsu użytkownika przechwytuje informacje o kontrolkach napotkanych podczas rejestrowania, a następnie generuje kod umożliwiający odtworzenie tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, wówczas Konstruktor kodowanego testu interfejsu użytkownika przechwytuje akcje (takie jak kliknięcia myszą) przy użyciu współrzędnych ekranu. Gdy test zostanie odtworzony, wygenerowany kod wystawia akcje na tej samej współrzędnej ekranu. Jeśli kontrolka pojawia się w innym miejscu na ekranie, gdy test zostanie odtworzony, wygenerowany kod nie będzie mógł wykonać tej akcji. Nie implementując ułatwienia dostępu dla kontrolki, mogą pojawić się błędy testów, jeśli test zostanie odtworzony w różnych konfiguracjach ekranu, w różnych środowiskach lub w przypadku zmiany układu interfejsu użytkownika.

![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Jeśli zaimplementowano ułatwienia dostępu, Konstruktor kodowanego testu interfejsu użytkownika używa tego do przechwytywania informacji o kontrolce, gdy rejestruje test. Następnie po uruchomieniu testu wygenerowany kod będzie powtarzał te zdarzenia względem formantu, nawet jeśli znajduje się on w innym miejscu w interfejsie użytkownika. Autorzy testów mogą również tworzyć potwierdzenia przy użyciu podstawowych właściwości formantu.

![CUIT&#95;rekord](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Aby obsługiwać nagrywanie i odtwarzanie, sprawdzanie poprawności właściwości i nawigację dla kontrolki Windows Forms
Zaimplementuj ułatwienia dostępu dla kontrolki zgodnie z poniższą procedurą i szczegółowo wyjaśniono w <xref:System.Windows.Forms.AccessibleObject>.

![CUIT&#95;dostępne](../test/media/cuit_accessible.png)

1. Zaimplementuj klasę, która dziedziczy z <xref:System.Windows.Forms.Control.ControlAccessibleObject>, i Zastąp Właściwość <xref:System.Windows.Forms.Control.AccessibilityObject%2A>, aby zwracała obiekt klasy.

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

2. Zastąp <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> i <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> właściwości dostępnego obiektu.

3. Zaimplementuj inny obiekt ułatwień dostępu dla formantu podrzędnego i Przesłoń Właściwość <xref:System.Windows.Forms.Control.AccessibilityObject%2A> formantu podrzędnego, aby zwrócić obiekt ułatwień dostępu.

4. Zastąp <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>i <xref:System.Windows.Forms.AccessibleObject.Select%2A> właściwości oraz metody dla obiektu ułatwienia dostępu formantu podrzędnego.

> [!NOTE]
> Ten temat rozpoczyna się od przykładu dostępności w <xref:System.Windows.Forms.AccessibleObject>, a następnie kompiluje ten przykład w pozostałych procedurach. Jeśli chcesz utworzyć działającą wersję przykładu dostępności, Utwórz aplikację konsolową, a następnie zastąp kod w *program.cs* z przykładowym kodem. Dodaj odwołania do funkcji ułatwień dostępu, system. Drawing i system. Windows. Forms. Aby wyeliminować ostrzeżenie kompilacji, należy zmienić **typy międzyoperacyjności osadzania** dla ułatwienia dostępu na **wartość false** . Można zmienić typ danych wyjściowych projektu z **aplikacji konsolowej** na **aplikację systemu Windows** , aby okno konsoli nie było wyświetlane podczas uruchamiania aplikacji.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Obsługa walidacji właściwości niestandardowych przez implementację dostawcy właściwości

Po zaimplementowaniu podstawowej obsługi rejestrowania i odtwarzania oraz weryfikacji właściwości można sprawić, aby niestandardowe właściwości kontrolki były dostępne dla kodowanych testów interfejsu użytkownika, implementując <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczkę. Na przykład poniższa procedura umożliwia utworzenie dostawcy właściwości, który umożliwia kodowanym testom interfejsu użytkownika dostęp do właściwości State formantów podrzędnych CurveLegend formantu wykresu:

![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Aby zapewnić obsługę walidacji właściwości niestandardowych

![CUIT&#95;props](../test/media/cuit_props.png)

1. Zastąp Właściwość <xref:System.Windows.Forms.AccessibleObject.Description%2A> obiektu dostępnego legendy krzywej, aby przekazać zaawansowane wartości właściwości w ciągu opisu. Rozdziel wiele wartości średnikami (;).

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

1. Utwórz pakiet rozszerzenia testu interfejsu użytkownika dla kontrolki, tworząc projekt biblioteki klas. Dodaj odwołania do funkcji Accessibility, Microsoft. VisualStudio. TestTools. UITesting, Microsoft. VisualStudio. TestTools. UITest. Common oraz Microsoft. VisualStudio. TestTools. Extension. Zmień **typy międzyoperacyjności osadzania** , aby uzyskać dostęp do **wartości false**.

1. Dodaj klasę dostawcy właściwości, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

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

1. Zaimplementuj dostawcę właściwości, umieszczając nazwy właściwości i deskryptory właściwości w <xref:System.Collections.Generic.Dictionary%602>.

1. Zastąp <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>, aby wskazać, że zestaw zapewnia obsługę specyficzną dla kontrolek i jej elementów podrzędnych.

1. Zastąp pozostałe metody abstrakcyjne <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Dodaj klasę pakietu rozszerzenia, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Zdefiniuj atrybut `UITestExtensionPackage` dla zestawu.

1. W klasie pakietu rozszerzenia Przesłoń <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>, aby zwrócić klasę dostawcy właściwości, gdy zażądano dostawcy właściwości.

1. Zastąp pozostałe metody abstrakcyjne i właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Kompiluj pliki binarne i skopiuj je do *%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Ten pakiet rozszerzenia jest stosowany do każdej kontrolki, która jest typu "text". Jeśli testujesz wiele kontrolek tego samego typu, przetestuj je oddzielnie, aby można było zarządzać rozszerzeniami, które są wdrażane po zarejestrowaniu testów.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Obsługa generowania kodu przez implementację klasy w celu uzyskania dostępu do właściwości niestandardowych

Gdy Konstruktor kodowanego testu interfejsu użytkownika generuje kod na podstawie nagrania sesji, używa klasy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, aby uzyskać dostęp do kontrolek.

Jeśli dostawca właściwości został wdrożony w celu zapewnienia dostępu do niestandardowych właściwości kontrolki, można dodać wyspecjalizowaną klasę, która jest używana do uzyskiwania dostępu do tych właściwości. Dodanie wyspecjalizowanej klasy upraszcza wygenerowany kod.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać wyspecjalizowaną klasę do uzyskiwania dostępu do kontrolki

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Zaimplementuj klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i Dodaj typ kontrolki do kolekcji właściwości wyszukiwania w konstruktorze.

1. Zaimplementuj niestandardowe właściwości kontrolki jako właściwości klasy.

1. Przesłoń metodę <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> dostawcy właściwości, aby zwrócić typ nowej klasy dla formantów podrzędnych legendy krzywej.

1. Przesłoń metodę <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> dostawcy właściwości, aby zwrócić typ metody "PropertyName" nowej klasy.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Obsługa akcji opartych na intencjach przez implementację filtru akcji

Gdy program Visual Studio rejestruje test, przechwytuje każde zdarzenie myszy i klawiatury. Jednak w niektórych przypadkach cel akcji może zostać utracony w serii zdarzeń myszy i klawiatury. Na przykład, jeśli formant obsługuje Autouzupełnianie, ten sam zestaw zdarzeń myszy i klawiatury może spowodować inną wartość, gdy test zostanie odtworzony w innym środowisku. Można dodać wtyczkę filtru akcji, która zastępuje serię zdarzeń klawiatury i myszy z pojedynczą akcją. W ten sposób można zastąpić serię zdarzeń myszy i klawiatury, które wybierają wartość z pojedynczą akcją, która ustawia wartość. Zapewnia to ochronę kodowanych testów interfejsu użytkownika z różnic w funkcji Autouzupełnianie z jednego środowiska do innego.

### <a name="to-support-intent-aware-actions"></a>Aby obsługiwać akcje obsługujące intencje

![Akcje&#95;CUIT](../test/media/cuit_actions.png)

1. Zaimplementuj klasę filtru akcji, która pochodzi od [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), zastępując właściwości [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) i [name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Zastąp [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). W tym przykładzie zastępują akcję dwukrotnego kliknięcia akcją pojedynczego kliknięcia.

1. Dodaj filtr akcji do metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> pakietu rozszerzenia.

1. Kompiluj pliki binarne i skopiuj je do programu *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Filtr akcji nie zależy od implementacji dostępności lub dostawcy właściwości.

## <a name="debug-your-property-provider-or-action-filter"></a>Debuguj dostawcę właściwości lub filtr akcji

Dostawca właściwości i filtr akcji są zaimplementowane w pakiecie rozszerzenia. Konstruktor testów uruchamia pakiet rozszerzenia w osobnym procesie z aplikacji.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować dostawcę właściwości lub filtr akcji

1. Kompiluj wersję debugowania pakietu rozszerzenia Skopiuj pliki *. dll* i *. pdb* do pliku *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Uruchom aplikację (nie w debugerze).

3. Uruchom konstruktora kodowanego testu interfejsu użytkownika.

     `codedUITestBuilder.exe  /standalone`

4. Dołącz debuger do procesu codedUITestBuilder.

5. Ustaw punkty przerwania w kodzie.

6. W konstruktorze kodowanego testu interfejsu użytkownika utwórz potwierdzenia do korzystania z dostawcy właściwości i zarejestruj akcje, aby wykonać filtry akcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.AccessibleObject>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
