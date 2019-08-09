---
title: Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c97ee2d05609ee6802da3503e9f514fdc07a4b85
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871658"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Formant może być łatwiej przetestowany w przypadku zaimplementowania obsługi kodowanego środowiska testowania interfejsu użytkownika. Można zwiększyć przyrostowy poziom wsparcia. Można zacząć od obsługi rekordu i odtwarzania oraz walidacji właściwości. Można ją skompilować, aby zezwolić konstruktorowi kodowanego testu interfejsu użytkownika na rozpoznawanie niestandardowych właściwości kontrolki i udostępnianie klas niestandardowych w celu uzyskania dostępu do tych właściwości z wygenerowanego kodu. Można także ułatwić zamierzone działanie funkcji przechwytywania konstruktora testów interfejsu użytkownika w sposób zbliżony do zamiaru rejestrowania akcji.

 **W tym temacie:**

1. [Obsługa rejestrowania i odtwarzania oraz walidacji właściwości przez implementację ułatwień dostępu](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Obsługa walidacji właściwości niestandardowych przez implementację dostawcy właściwości](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Obsługa generowania kodu przez implementację klasy w celu uzyskania dostępu do właściwości niestandardowych](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Obsługa akcji opartych na intencjach przez implementację filtru akcji](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")

## <a name="recordandplayback"></a>Obsługa rejestrowania i odtwarzania oraz walidacji właściwości przez implementację ułatwień dostępu
 Konstruktor kodowanego testu interfejsu użytkownika przechwytuje informacje o kontrolkach napotkanych podczas rejestrowania, a następnie generuje kod umożliwiający odtworzenie tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, wówczas Konstruktor kodowanego testu interfejsu użytkownika będzie przechwytywać akcje (na przykład kliknięcia myszą) przy użyciu współrzędnych ekranu. Gdy test zostanie odtworzony, wygenerowany kod wyda te kliknięcia myszą w tych samych współrzędnych ekranu. Jeśli kontrolka pojawia się w innym miejscu na ekranie, gdy test zostanie odtworzony, wygenerowany kod nie będzie mógł wykonać tej akcji na formancie. Może to powodować błędy, jeśli test zostanie odtworzony w różnych konfiguracjach ekranu, w różnych środowiskach lub po zmianie układu interfejsu użytkownika.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Jeśli zaimplementowano ułatwienia dostępu, Konstruktor kodowanego testu interfejsu użytkownika będzie używać go do przechwytywania informacji o kontrolce podczas rejestrowania testu i generowania kodu. Następnie po uruchomieniu testu wygenerowany kod będzie powtarzał te zdarzenia względem formantu, nawet jeśli znajduje się on w innym miejscu w interfejsie użytkownika. Autorzy testów mogą również tworzyć potwierdzenia przy użyciu podstawowych właściwości formantu.

 ![CUIT&#95;Record](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Aby obsługiwać nagrywanie i odtwarzanie, sprawdzanie poprawności właściwości i nawigację dla kontrolki formularzy systemu Windows
 Zaimplementuj ułatwienia dostępu dla kontrolki zgodnie z poniższą procedurą i szczegółowo <xref:System.Windows.Forms.AccessibleObject>wyjaśnioną w temacie.

 ![CUIT&#95;Accessible](../test/media/cuit-accessible.png "CUIT_Accessible")

1. Zaimplementuj klasę, która pochodzi <xref:System.Windows.Forms.Control.ControlAccessibleObject>z i <xref:System.Windows.Forms.Control.AccessibilityObject%2A> Przesłoń właściwość w celu zwrócenia obiektu klasy.

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

2. Zastąp <xref:System.Windows.Forms.AccessibleObject.Role%2A>dostępne obiekty <xref:System.Windows.Forms.AccessibleObject.State%2A> <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> , i<xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> właściwości i metody.

3. Zaimplementuj inny obiekt ułatwień dostępu dla formantu podrzędnego i Przesłoń <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwość kontrolki podrzędnej w celu zwrócenia tego obiektu ułatwień dostępu.

4. <xref:System.Windows.Forms.AccessibleObject.Name%2A> Zastąp<xref:System.Windows.Forms.AccessibleObject.Parent%2A>właściwości ,,<xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A> ,i<xref:System.Windows.Forms.AccessibleObject.Select%2A> i metody dla obiektu ułatwienia dostępu formantu podrzędnego. <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>

> [!NOTE]
> Ten temat rozpoczyna się od przykładu dostępności <xref:System.Windows.Forms.AccessibleObject> w ramach tej procedury, a następnie kompiluje go w ramach pozostałych procedur. Jeśli chcesz utworzyć działającą wersję przykładu dostępności, Utwórz aplikację konsolową, a następnie zastąp kod w Program.cs z przykładowym kodem. Należy dodać odwołania do funkcji ułatwień dostępu, system. Drawing i system. Windows. Forms. Aby wyeliminować ostrzeżenie kompilacji, należy zmienić **typy** międzyoperacyjności osadzania dla ułatwienia dostępu na **wartość false** . Możesz zmienić typ danych wyjściowych projektu na z **aplikacji konsolowej** na **aplikację systemu Windows** , aby okno konsoli nie było wyświetlane podczas uruchamiania aplikacji.

## <a name="customproprties"></a>Obsługa walidacji właściwości niestandardowych przez implementację dostawcy właściwości
 Po zaimplementowaniu podstawowej obsługi rejestrowania i odtwarzania oraz weryfikacji właściwości można sprawić, aby właściwości niestandardowe kontrolki były dostępne dla kodowanych testów interfejsu użytkownika przez implementację <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczki. Na przykład poniższa procedura umożliwia utworzenie dostawcy właściwości, który umożliwia kodowanym testom interfejsu użytkownika dostęp do właściwości State formantów podrzędnych CurveLegend formantu wykresu.

 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Aby zapewnić obsługę walidacji właściwości niestandardowych
 ![CUIT&#95;Props](../test/media/cuit-props.png "CUIT_Props")

1. Przesłoń <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwość obiektu dostępnego legendy krzywej, aby przekazać wartości właściwości rozbudowanych w ciągu opisu, rozdzielając je od głównego opisu (i nawzajem w przypadku implementowania wielu właściwości) za pomocą średników (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Utwórz pakiet rozszerzenia testu interfejsu użytkownika dla kontrolki, tworząc projekt biblioteki klas i Dodaj odwołania do elementu Accessibility, Microsoft. VisualStudio. TestTools. UITesting, Microsoft. VisualStudio. TestTools. UITest. Common i Microsoft. VisualStudio. TestTools. Extension. Zmień **typy** międzyoperacyjności osadzania, aby uzyskać dostęp do **wartości false**.

3. Dodaj klasę dostawcy właściwości, która pochodzi od <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.

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

4. Zaimplementuj dostawcę właściwości, umieszczając nazwy właściwości i deskryptory właściwości w <xref:System.Collections.Generic.Dictionary%602>.

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Przesłoń <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> , aby wskazać, że zestaw zapewnia obsługę specyficzną dla kontrolek i jej elementów podrzędnych.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. Zastąp pozostałe metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>abstrakcyjne.

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. Dodaj klasę pakietu rozszerzenia, która pochodzi od <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. `UITestExtensionPackage` Zdefiniuj atrybut zestawu.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. W klasie pakietu rozszerzenia Przesłoń <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> , aby zwrócić klasę dostawcy właściwości, gdy zażądano dostawcy właściwości.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. Zastąp pozostałe metody abstrakcyjne i właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. Kompiluj pliki binarne i skopiuj je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Ten pakiet rozszerzenia zostanie zastosowany do każdej kontrolki typu "text". Jeśli testujesz wiele kontrolek tego samego typu, musisz przetestować je oddzielnie i zarządzać pakietami rozszerzeń wdrożonymi po zarejestrowaniu testów.

## <a name="codegeneration"></a>Obsługa generowania kodu przez implementację klasy w celu uzyskania dostępu do właściwości niestandardowych
 Gdy Konstruktor kodowanego testu interfejsu użytkownika generuje kod na podstawie nagrania sesji, używa <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> klasy w celu uzyskania dostępu do kontrolek.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Jeśli dostawca właściwości został wdrożony w celu zapewnienia dostępu do niestandardowych właściwości kontrolki, można dodać wyspecjalizowaną klasę, która jest używana do uzyskiwania dostępu do tych właściwości, aby uprościć generowanie kodu.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać wyspecjalizowaną klasę do uzyskiwania dostępu do kontrolki
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. Zaimplementuj klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i Dodaj typ kontrolki do kolekcji właściwości wyszukiwania w konstruktorze.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Zaimplementuj niestandardowe właściwości kontrolki jako właściwości klasy.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Zastąp <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę dostawcy właściwości, aby zwracała typ nowej klasy dla formantów podrzędnych legendy krzywej.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Zastąp <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę dostawcy właściwości, aby zwracała typ metody "PropertyName" nowej klasy.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="intentawareactions"></a>Obsługa akcji opartych na intencjach przez implementację filtru akcji
 Gdy program Visual Studio rejestruje test, przechwytuje każde zdarzenie myszy i klawiatury. Jednak w niektórych przypadkach cel akcji może zostać utracony w serii zdarzeń myszy i klawiatury. Na przykład, jeśli formant obsługuje Autouzupełnianie, ten sam zestaw zdarzeń myszy i klawiatury może spowodować inną wartość, gdy test zostanie odtworzony w innym środowisku. Można dodać wtyczkę filtru akcji, która zastępuje serię zdarzeń klawiatury i myszy z pojedynczą akcją. W ten sposób można zamienić serię zdarzeń myszy i klawiatury w wyniku zaznaczenia wartości z pojedynczą akcją, która ustawia wartość. Zapewnia to ochronę kodowanych testów interfejsu użytkownika z różnic w funkcji Autouzupełnianie z jednego środowiska do innego.

### <a name="to-support-intent-aware-actions"></a>Aby obsługiwać akcje obsługujące intencje
 ![CUIT&#95;Actions](../test/media/cuit-actions.png "CUIT_Actions")

1. Zaimplementuj klasę filtru akcji, która pochodzi od [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), zastępując właściwości [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) i [name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. Zastąpienie `UITestActionFilter.ProcessRule`. W tym przykładzie zastępują akcję dwukrotnego kliknięcia akcją pojedynczego kliknięcia.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Dodaj filtr akcji do <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metody pakietu rozszerzenia.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. Kompiluj pliki binarne i skopiuj je do programu%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Filtr akcji nie zależy od implementacji dostępności lub dostawcy właściwości.

## <a name="debug-your-property-provider-or-action-filter"></a>Debuguj dostawcę właściwości lub filtr akcji
 Dostawca właściwości i filtr akcji są zaimplementowane w pakiecie rozszerzenia, który jest ładowany i uruchamiany przez konstruktora kodowanego testu interfejsu użytkownika w ramach procesu niezależnego od aplikacji.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować dostawcę właściwości lub filtr akcji

1. Kompiluj wersję debugowania pakietu rozszerzenia Skopiuj pliki. dll i. pdb do pliku%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2. Uruchom aplikację (nie w debugerze).

3. Uruchom konstruktora kodowanego testu interfejsu użytkownika.

     `codedUITestBuilder.exe  /standalone`

4. Dołącz debuger do procesu codedUITestBuilder.

5. Ustaw punkty przerwania w kodzie.

6. W konstruktorze kodowanego testu interfejsu użytkownika utwórz potwierdzenia do korzystania z dostawcy właściwości i zarejestruj akcje, aby wykonać filtry akcji.

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
 [Testowanie ciągłego dostarczania przy użyciu programu Visual Studio 2012 — Rozdział 2: Testowanie jednostkowe: Testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.AccessibleObject>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
