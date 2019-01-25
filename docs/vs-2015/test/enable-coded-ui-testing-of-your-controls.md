---
title: Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1e24e9e405dfeab18ca0e55a617857d73ba4234e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766974"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Włącz testowanie kodowanego interfejsu użytkownika dla Twoich kontrolek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontrolki można łatwo przetestować w przypadku zastosowania pomocy technicznej dla kodowanych testów interfejsu użytkownika. Zwiększa poziom obsługi można dodać przyrostowo. Możesz rozpocząć dzięki obsłudze rekordu i odtwarzania oraz właściwości sprawdzania poprawności. Możesz rozwijać to umożliwienie konstruktora kodowanego testu interfejsu użytkownika, rozpoznawał właściwości niestandardowych kontroli nad i dostarczają niestandardowej klasy dostęp do tych właściwości z wygenerowanego kodu. Może również pomóc kodowanego interfejsu użytkownika testu konstruktora przechwytywania akcje w sposób, który jest bliżej celem akcji rejestrowane.  
  
 **W tym temacie:**  
  
1. [Obsługuje rekordu i odtwarzania oraz właściwości sprawdzania poprawności poprzez implementację ułatwień dostępu](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2. [Obsługuje sprawdzanie poprawności właściwości niestandardowe poprzez implementację dostawcy właściwości](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3. [Obsługuje generowanie kodu poprzez implementację klasę umożliwiającą dostęp do właściwości niestandardowe](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4. [Obsługuje świadomie akcji przez zaimplementowanie filtr akcji](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a> Obsługuje rekordu i odtwarzania oraz właściwości sprawdzania poprawności poprzez implementację ułatwień dostępu  
 Konstruktor kodowanego testu interfejsu użytkownika przechwytuje informacji na temat formantów napotka podczas rejestrowania i następnie generuje kod w celu odtworzenia tej sesji. Jeśli formant nie obsługuje ułatwień dostępu, kodowanego testu interfejsu użytkownika będzie przechwytywać akcje (takie jak kliknięcia myszą), za pomocą współrzędnych ekranu. Podczas odtwarzania testu wygenerowany kod będzie wystawiać tych kliknięć myszą, w tym samym współrzędne ekranu. Jeśli formant znajduje się w innym miejscu na ekranie, podczas odtwarzania testu, wygenerowany kod nie będzie można wykonać tę akcję dla formantu. Może to spowodować błędy, jeśli test jest odtwarzany na ekranach o różnych konfiguracjach, w różnych środowiskach lub po została zmieniona na układ interfejsu użytkownika.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")  
  
 W przypadku zastosowania ułatwień dostępu, jednak kodowanego testu interfejsu użytkownika będzie używać, aby przechwytywania informacji na temat kontrolki, gdy rejestruje testu i generuje kod. Następnie po uruchomieniu testu, wygenerowany kod będzie oparte na metodzie powtórzeń tych zdarzeń dla formantu, nawet jeśli jest on gdzieś w interfejsie użytkownika. Autorzy testu będzie można utworzyć potwierdza przy użyciu podstawowe właściwości formantu.  
  
 ![CUIT&#95;Record](../test/media/cuit-record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Do obsługi rekord i odtwarzania, właściwości sprawdzania poprawności i nawigacji dla kontrolki formularzy Windows forms  
 Implementowanie ułatwień dostępu dla kontrolki, co zostało opisane w poniższej procedurze, a omówiona szczegółowo w <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit-accessible.png "CUIT_Accessible")  
  
1.  Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Forms.Control.ControlAccessibleObject>i zastępowania <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwości, aby zwrócić obiekt klasy.  
  
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
  
2.  Zastąp dostępnego obiektu <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> i <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> właściwości i metody.  
  
3.  Implementowanie innego obiektu ułatwień dostępu dla kontrolki podrzędnej i przesłonić kontrolki podrzędnej <xref:System.Windows.Forms.Control.AccessibilityObject%2A> właściwości, aby przywrócić ten obiekt ułatwień dostępu.  
  
4.  Zastąp <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, i <xref:System.Windows.Forms.AccessibleObject.Select%2A> właściwości i metody dla obiektu ułatwień dostępu kontrolki podrzędnej.  
  
> [!NOTE]
>  W tym temacie, który rozpoczyna się od przykładu ułatwień dostępu w <xref:System.Windows.Forms.AccessibleObject> w tej procedury i następnie kompilacje na tym pozostałe procedur. Jeśli chcesz utworzyć działającą wersją próbki ułatwień dostępu, Utwórz aplikację konsolową i następnie Zastąp kod w pliku Program.cs z przykładowym kodem. Należy dodać odwołania do ułatwień dostępu, System.Drawing i przestrzeń nazw System.Windows.Forms. Należy zmienić **Osadź typy współdziałania** ułatwień dostępu do **False** , aby wyeliminować ostrzeżenia kompilacji. Można zmienić typu danych wyjściowych projektu na z **aplikację Konsolową** do **aplikacji Windows** okno konsoli nie będą wyświetlane po uruchomieniu aplikacji.  
  
##  <a name="customproprties"></a> Obsługuje sprawdzanie poprawności właściwości niestandardowe poprzez implementację dostawcy właściwości  
 Po zastało zaimplementowane podstawowa pomoc techniczna dla rekordu i odtwarzania oraz właściwości sprawdzania poprawności, można udostępnić kontroli nad właściwości niestandardowych do zakodowanych testów interfejsu użytkownika poprzez implementację <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> wtyczki. Na przykład poniższa procedura tworzy dostawcy właściwości, który umożliwia kodowane testy interfejsu użytkownika do dostępu do właściwości stanu formantów podrzędnych CurveLegend formantu wykresu.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>Do obsługi sprawdzania poprawności właściwości niestandardowej  
 ![CUIT&#95;Props](../test/media/cuit-props.png "CUIT_Props")  
  
1.  Zastąpienie krzywej legendy dostępne obiektu <xref:System.Windows.Forms.AccessibleObject.Description%2A> właściwości, aby przekazać wartości właściwości sformatowanego ciągu opisu oddzielona od opis elementu głównego (i siebie nawzajem w przypadku wdrażania wielu właściwości) średnikami (;).  
  
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
  
2.  Utwórz pakiet rozszerzenia testów interfejsu użytkownika dla kontrolki przez tworzenie projektu biblioteki klas i dodaj odwołania do ułatwień dostępu, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common, i Microsoft.VisualStudio.TestTools.Extension. Zmiana **Osadź typy współdziałania** ułatwień dostępu do **False**.  
  
3.  Dodaj klasę dostawcy właściwość, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
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
  
4.  Implementowanie dostawcy właściwości przez umieszczenie nazwy i właściwości deskryptorów właściwości w <xref:System.Collections.Generic.Dictionary%602>.  
  
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
  
5.  Zastąp <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> do wskazania, że zestaw obsługuje specyficznej dla kontroli formantu i jego elementy podrzędne.  
  
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
  
6.  Zastąp pozostałe metody abstrakcyjne klasy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
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
  
7.  Dodaj klasę pakietu rozszerzenia, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
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
  
8.  Zdefiniuj `UITestExtensionPackage` atrybutu dla zestawu.  
  
    ```csharp  
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
                    "ChartControlExtensionPackage",  
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]  
    namespace ChartControlExtensionPackage  
    {  
       …  
    ```  
  
9. W klasie pakietu rozszerzenia, należy zastąpić <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> do zwrócenia klasa dostawcy właściwości, gdy dostawca właściwości.  
  
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
  
10. Zastąp pozostałe metody abstrakcyjne i właściwości działania <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
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
  
11. Tworzenie plików binarnych i skopiować je do **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  
  
> [!NOTE]
>  Ten pakiet rozszerzenia zostaną zastosowane do żadnego formantu, który jest typu "Text". Jeśli testujesz wielu formantów tego samego typu, należy przetestować je oddzielnie i zarządzać pakietów rozszerzeń, które są wdrażane po zarejestrowaniu testów.  
  
##  <a name="codegeneration"></a> Obsługuje generowanie kodu poprzez implementację klasę umożliwiającą dostęp do właściwości niestandardowe  
 Gdy kodowanego testu interfejsu użytkownika generuje kod z nagrania sesji, używa <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> klasy, aby dostęp do kontrolek.  
  
```csharp  
  
      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());  
```  
  
 Jeśli zastało zaimplementowane Dostawca właściwości w celu zapewnienia dostępu do właściwości niestandardowych kontroli nad, można dodać klas wyspecjalizowanych, która umożliwia uzyskiwanie dostępu do tych właściwości, tak że wygenerowany kod jest uproszczony.  
  
```csharp  
  
      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;  
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);  
```  
  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>Aby dodać klas wyspecjalizowanych do usługi kontroli dostępu  
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")  
  
1.  Implementuje klasę, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> i dodać do kolekcji właściwości wyszukiwania w Konstruktorze typ formantu.  
  
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
  
2.  Implementuje właściwości niestandardowe kontroli nad jako właściwości klasy.  
  
    ```csharp  
    public virtual string State  
    {  
        get  
        {  
            return (string)GetProperty("State");  
        }  
    }  
    ```  
  
3.  Twój dostawca właściwości zastąpienia <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> metodę, aby zwracany typ nową klasę dla krzywej z formantów podrzędnych legendy.  
  
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
  
4.  Twój dostawca właściwości zastąpienia <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> metodę, aby zwracany typ metody PropertyNames nowej klasy.  
  
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
  
##  <a name="intentawareactions"></a> Obsługuje świadomie akcji przez zaimplementowanie filtr akcji  
 Visual Studio zapisuje testu, umożliwia przechwytywanie każdego zdarzenia myszy i klawiatury. Jednak w niektórych przypadkach celem akcji mogą zostać utracone w serii zdarzeń klawiatury oraz myszy. Na przykład jeśli formant obsługuje autouzupełniania, ten sam zestaw zdarzeń klawiatury oraz myszy może spowodować naliczenie inną wartość, gdy test jest odtwarzany w innym środowisku. Możesz dodać filtr akcji z wtyczki zastępuje serii zdarzeń klawiatury oraz myszy przy użyciu jednej akcji. W ten sposób można zastąpić serii zdarzeń klawiatury oraz myszy skutkuje wybór wartości za pomocą jednej akcji, która ustawia wartości. Tą operacją chroni kodowane testy interfejsu użytkownika z różnic w funkcji autouzupełniania z jednego środowiska do innego.  
  
### <a name="to-support-intent-aware-actions"></a>Aby obsługiwać świadomie akcje  
 ![CUIT&#95;Actions](../test/media/cuit-actions.png "CUIT_Actions")  
  
1.  Implementowanie klasy filtru akcji, która jest pochodną <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, zastępowanie właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
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
  
2.  Zastąp <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. Przykład tutaj realpces akcji kliknij dwukrotnie plik, za pomocą pojedynczej, kliknij akcję.  
  
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
  
3.  Dodawanie filtru akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> metoda pakietu rozszerzenia.  
  
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
  
4.  Tworzenie plików binarnych, a następnie skopiuj je do %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
> [!NOTE]
>  Filtr akcji zależy od implementacji dostępności lub Dostawca właściwości.  
  
## <a name="debug-your-property-provider-or-action-filter"></a>Debuguj z usługodawcą właściwości lub filtr akcji  
 Właściwości filtru akcji i dostawcy są implementowane w pakiecie rozszerzenia, który jest ładowany i uruchamiane przez konstruktora kodowanego testu interfejsu użytkownika w ramach procesu niezależnie od aplikacji.  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>Aby debugować filtru akcji lub dostawcy właściwości  
  
1.  Tworzenie wersji debugowania kopii pakietu rozszerzenia pliku .dll i pliki .pdb katalog na %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.  
  
2.  Uruchom aplikację (nie w debugerze).  
  
3.  Uruchamianie kodowanego testu interfejsu użytkownika.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Dołącz debuger do procesu codedUITestBuilder.  
  
5.  Ustaw punkty przerwania w kodzie.  
  
6.  Konstruktor kodowanego testu interfejsu użytkownika tworzenia potwierdza wykonywania dostawcy właściwości i Rejestruj akcje do wykonywania filtrów akcji.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
