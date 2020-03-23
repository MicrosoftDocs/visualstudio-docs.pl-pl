---
title: Anatomia kodowanego testu interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7100c6bb5c1dfb4c7d336ec110cf532f1f998d4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591206"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomia zakodowany test interfejsu użytkownika

Podczas tworzenia kodowany test interfejsu użytkownika w projekcie testu interfejsu użytkownika kodowane, kilka plików są dodawane do rozwiązania. Ten artykuł zawiera informacje o plikach.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Zawartość zakodowany test interfejsu użytkownika

Podczas tworzenia kodowany test interfejsu użytkownika, **Coded UI Test Builder** tworzy mapę interfejsu użytkownika w ramach testu, a także metody testowe, parametry i potwierdzenia dla wszystkich testów. Tworzy również plik klasy dla każdego testu.

|Plik|Spis treści|Edytowalne?|
|-|-|-|
|[Uimap.designer.cs](#UIMapDesignerFile)|[Sekcja Deklaracje](#UIMapDesignerFile)<br /><br /> [Klasa UIMap](#UIMapClass) (częściowa, automatycznie generowana)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Właściwości](#UIMapProperties)|Nie|
|[Uimap.cs](#UIMapCS)|[UIMap klasa](#UIMapCS) (częściowa)|Tak|
|[CodedUITest1.cs](#CodedUITestCS)|[Klasa CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Właściwości](#CodedUITestProperties)|Tak|
|[Uimap.uitest](#UIMapuitest)|Mapa XML interfejsu użytkownika dla testu.|Nie|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a>Uimap.designer.cs
Ten plik zawiera kod, który jest automatycznie tworzony przez **Konstruktora testów kodowanych interfejsu użytkownika** podczas tworzenia testu. Ten plik jest tworzony ponownie za każdym razem, gdy test się zmienia, tak aby nie był to plik, w którym można dodawać lub modyfikować kod.

#### <a name="declarations-section"></a>Sekcja Deklaracje
Ta sekcja zawiera następujące deklaracje dla interfejsu użytkownika systemu Windows.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

Obszar <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> nazw jest dołączony do interfejsu użytkownika systemu Windows (UI). W przypadku interfejsu użytkownika strony sieci <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>Web obszar nazw będzie ; dla interfejsu użytkownika programu Windows Presentation Foundation <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>obszar nazw będzie .

#### <a name="uimap-class"></a><a name="UIMapClass"></a>Klasa UIMap
Następną sekcją pliku jest klasa [UIMap.](/previous-versions/dd580454(v=vs.140))

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Kod klasy rozpoczyna się <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> od atrybutu, który jest stosowany do klasy, który jest zadeklarowany jako klasa częściowa. Należy zauważyć, że atrybut jest również stosowany do każdej klasy w tym pliku. Inny plik, który może zawierać więcej kodu dla tej klasy jest *UIMap.cs*, który jest omówiony później.

Wygenerowana `UIMap` klasa zawiera kod dla każdej metody, która została określona podczas rejestrowania testu.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Ta część [UIMap](/previous-versions/dd580454(v=vs.140)) klasy zawiera również wygenerowany kod dla każdej właściwości, która jest wymagana przez metody.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a>UIMap metody
Każda metoda ma strukturę, `AddItems()` która przypomina metodę. Jest to wyjaśnione bardziej szczegółowo w ramach kodu, który jest przedstawiony wraz z podziałami wierszy, aby dodać jasności.

```csharp
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

Komentarz podsumowujący dla każdej definicji metody mówi, która klasa ma być używana dla wartości parametrów dla tej metody. W takim przypadku jest `AddItemsParams` to klasa, która jest zdefiniowana w dalszej części pliku *UIMap.cs* i `AddItemsParams` która jest również typem wartości zwracany przez właściwość.

W górnej części kodu metody `Variable Declarations` jest region, który definiuje zmienne lokalne dla obiektów interfejsu użytkownika, które są używane przez metodę.

W tej `UIItemWindow` metodzie `UIItemEdit` zarówno i są właściwości, `UICalculatorWindow` które są dostępne przy użyciu klasy, która jest zdefiniowana w dalszej części *pliku UIMap.cs.*

Dalej są wiersze, które wysyłają tekst z klawiatury do `AddItemsParams` aplikacji Kalkulator przy użyciu właściwości obiektu.

Metoda `VerifyTotal()` ma podobną strukturę i zawiera następujący kod potwierdzenia:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Nazwa pola tekstowego jest wyświetlana jako nieznana, ponieważ twórca aplikacji Kalkulator systemu Windows nie podał publicznie dostępnej nazwy formantu. Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> kończy się niepowodzeniem, gdy wartość rzeczywista nie jest równa oczekiwanej wartości, co spowodowałoby niepowodzenie testu. Należy również zauważyć, że oczekiwana wartość zawiera punkt dziesiętny, po którym następuje spacja. Jeśli kiedykolwiek trzeba zmodyfikować funkcjonalność tego konkretnego testu, należy zezwolić na ten punkt dziesiętny i spacji.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a>Właściwości UIMap
Kod dla każdej właściwości jest również standardem w całej klasie. Poniższy kod `AddItemsParams` właściwości jest używany `AddItems()` w metodzie.

```csharp
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

Należy zauważyć, że właściwość używa prywatnej zmiennej lokalnej, która ma nazwę `mAddItemsParams` do przechowywania wartości, zanim ją zwróci. Nazwa właściwości i nazwa klasy dla zwracaego obiektu są takie same. Klasa jest zdefiniowana w dalszej części pliku *UIMap.cs.*

Każda klasa, która jest zwracana przez właściwość jest skonstruowana w podobny sposób. Poniżej dalsza `AddItemsParams` jest klasa:

```csharp
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

Podobnie jak w odniesieniu do wszystkich klas w pliku <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> *UIMap.cs,* ta klasa rozpoczyna się od . W tej małej `Fields` klasie jest region, który definiuje ciągi <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> do użycia jako `UIMap.AddItems()` parametry dla metody, która jest używana w metodzie, która została omówiona wcześniej. Można napisać kod, aby zastąpić wartości w tych polach ciągu, zanim metoda, w której te parametry są używane jest wywoływana.

### <a name="uimapcs"></a><a name="UIMapCS"></a>Uimap.cs
Domyślnie ten plik zawiera `UIMap` klasę częściową, która nie ma żadnych metod ani właściwości.

#### <a name="uimap-class"></a>Klasa UIMap
W tym miejscu można utworzyć kod niestandardowy, aby rozszerzyć funkcjonalność klasy [UIMap.](/previous-versions/dd580454(v=vs.140)) Kod utworzony w tym pliku nie jest zastępowany przez **konstruktora testów kodowanych interfejsu użytkownika** za każdym razem, gdy test jest modyfikowany.

Wszystkie części [UIMap](/previous-versions/dd580454(v=vs.140)) można użyć metod i właściwości z dowolnej innej części [UIMap](/previous-versions/dd580454(v=vs.140)) klasy.

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a>CodedUITest1.cs
Ten plik jest generowany przez **Coded UI Test Builder**, ale nie jest tworzony ponownie za każdym razem, gdy test jest modyfikowany, dzięki czemu można zmodyfikować kod w tym pliku. Nazwa pliku jest generowana na podstawie nazwy określonej dla testu podczas jego tworzenia.

#### <a name="codeduitest1-class"></a>Klasa CodedUITest1

Domyślnie ten plik zawiera definicję tylko dla jednej klasy.

```csharp
[CodedUITest]
public class CodedUITest1
```

[Atrybut CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) jest automatycznie stosowany do klasy, co umożliwia platformie testowej rozpoznawanie go jako rozszerzenia testowania. Należy również zauważyć, że nie jest to klasa częściowa. Cały kod klasy znajduje się w tym pliku.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a>Właściwości CodedUITest1

Klasa zawiera dwie domyślne właściwości, które znajdują się w dolnej części pliku. Nie należy ich modyfikować.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a>Metody CodedUITest1
Domyślnie klasa zawiera tylko jedną metodę.

```csharp
public void CodedUITestMethod1()
```

Ta metoda `UIMap` wywołuje każdą metodę określoną podczas rejestrowania testu, która jest opisana w sekcji [klasy UIMap](#UIMapClass).

Region, który jest `Additional test attributes`zatytułowany , jeśli niekomentowane, zawiera dwie metody opcjonalne.

```csharp
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

Metoda `MyTestInitialize()` ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> zastosowane do niego, który informuje platformę testowania wywołać tę metodę przed innymi metodami testowymi. Podobnie `MyTestCleanup()` metoda ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> zastosowane do niego, który informuje platformę testowania wywołać tę metodę po wywołaniu wszystkich innych metod testowych. Korzystanie z tych metod jest opcjonalne. W przypadku tego `UIMap.LaunchCalculator()` testu można `MyTestInitialize()` wywołać `UIMap.CloseCalculator()` metodę, a `MyTestCleanup()` metodę można `CodedUITest1Method1()`wywołać z zamiast od .

Jeśli dodasz więcej metod do tej klasy przy użyciu [Atrybutu CodedUITestAttribute,](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))struktura testowania wywołuje każdą metodę jako część testu.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a>Uimap.uitest
Jest to plik XML, który reprezentuje strukturę zakodowane nagrywania testu interfejsu użytkownika i wszystkie jego części. Należą do nich akcje i klasy oprócz metod i właściwości tych klas. Plik [UIMap.Designer.cs](#UIMapDesignerFile) zawiera kod, który jest generowany przez Coded UI Builder do odtworzenia struktury testu i zapewnia połączenie z platformą testowania.

Plik *UIMap.uitest* nie jest bezpośrednio edytowalny. Można jednak użyć Konstruktora kodowanych interfejsu użytkownika, aby zmodyfikować test, który automatycznie modyfikuje plik *UIMap.uitest* i plik [*UIMap.Designer.cs.*](#UIMapDesignerFile)

## <a name="see-also"></a>Zobacz też

- [Uimap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [Atrybut CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
