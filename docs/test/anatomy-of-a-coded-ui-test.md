---
title: Anatomia kodowanego testu interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8181b1682f94e8f5d8a6f1b56ded5f1703111e1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918552"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomia kodowanego testu interfejsu użytkownika

Po utworzeniu kodowanego testu interfejsu użytkownika w projekcie kodowanego testu interfejsu użytkownika do rozwiązania dodawane są kilka plików. Ten artykuł zawiera informacje o plikach.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Zawartość kodowanego testu interfejsu użytkownika

W przypadku tworzenia kodowanego testu interfejsu użytkownika **Konstruktor kodowanego testu interfejsu** użytkownika tworzy mapę testowanego interfejsu użytkownika, a także metod testowych, parametrów i potwierdzeń dla wszystkich testów. Tworzy również plik klasy dla każdego testu.

|Plik|Spis treści|Modyfikować?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sekcja deklaracji](#UIMapDesignerFile)<br /><br /> [Klasa UIMap](#UIMapClass) (częściowa, wygenerowana automatycznie)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Właściwości](#UIMapProperties)|Nie|
|[UIMap.cs](#UIMapCS)|[Klasa UIMap](#UIMapCS) uwzględnieni|Tak|
|[CodedUITest1.cs](#CodedUITestCS)|[Klasa CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Właściwości](#CodedUITestProperties)|Tak|
|[UIMap.uitest](#UIMapuitest)|Mapa XML interfejsu użytkownika dla testu.|Nie|

### <a name="UIMapDesignerFile"></a> UIMap.Designer.cs
Ten plik zawiera kod, który jest automatycznie tworzony przez **konstruktora kodowanego testu interfejsu użytkownika** podczas tworzenia testu. Ten plik jest ponownie tworzony za każdym razem, gdy test ulegnie zmianie, tak że nie jest to plik, w którym można dodać lub zmodyfikować kod.

#### <a name="declarations-section"></a>Sekcja deklaracji
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

<xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> Przestrzeń nazw jest dołączona do interfejsu użytkownika systemu Windows. W przypadku interfejsu użytkownika strony sieci Web przestrzeń nazw może <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>być dla interfejsu użytkownika <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>Windows Presentation Foundation.

#### <a name="UIMapClass"></a>Klasa UIMap
Następna sekcja pliku jest klasą [UIMap](/previous-versions/dd580454(v=vs.140)) .

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Kod klasy zaczyna się od <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atrybutu, który jest stosowany do klasy, która jest zadeklarowana jako Klasa częściowa. Należy zauważyć, że atrybut jest również stosowany do każdej klasy w tym pliku. Innym plikiem, który może zawierać więcej kodu dla tej klasy, jest *UIMap.cs*, który został omówiony później.

Wygenerowana `UIMap` Klasa zawiera kod dla każdej metody, która została określona podczas rejestrowania testu.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Ta część klasy [UIMap](/previous-versions/dd580454(v=vs.140)) obejmuje również wygenerowany kod dla każdej właściwości, która jest wymagana przez metody.

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

##### <a name="UIMapMethods"></a>Metody UIMap
Każda metoda ma strukturę przypominającą `AddItems()` metodę. Wyjaśniono to bardziej szczegółowo w kodzie, który jest prezentowany wraz z podziałami wierszy w celu dodania przejrzystości.

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

Komentarz podsumowania dla każdej definicji metody wskazuje klasę, która ma być używana dla wartości parametrów dla tej metody. W tym przypadku jest `AddItemsParams` to Klasa, która jest zdefiniowana w dalszej części pliku *UIMap.cs* , a także typ wartości, który `AddItemsParams` jest zwracany przez właściwość.

W górnej części kodu metody jest `Variable Declarations` region, który definiuje zmienne lokalne dla obiektów interfejsu użytkownika, które są używane przez metodę.

W tej metodzie obie `UIItemWindow` i `UIItemEdit` są właściwościami, do których uzyskuje `UICalculatorWindow` się dostęp za pomocą klasy, która jest zdefiniowana w dalszej części pliku *UIMap.cs* .

Następnie są wiersze, które wysyłają tekst z klawiatury do aplikacji Kalkulator przy użyciu właściwości `AddItemsParams` obiektu.

`VerifyTotal()` Metoda ma podobną strukturę i zawiera następujący kod potwierdzenia:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Nazwa pola tekstowego jest wyświetlana jako nieznana, ponieważ Deweloper aplikacji kalkulatora systemu Windows nie dostarczył publicznie dostępnej nazwy dla kontrolki. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> Metoda kończy się niepowodzeniem, gdy rzeczywista wartość nie jest równa oczekiwanej wartości, co może spowodować niepowodzenie testu. Zauważ również, że oczekiwana wartość zawiera punkt dziesiętny, po którym następuje spacja. Jeśli kiedykolwiek zajdzie potrzeba zmodyfikowania funkcjonalności tego konkretnego testu, należy zezwolić na ten punkt dziesiętny oraz miejsce.

##### <a name="UIMapProperties"></a>Właściwości UIMap
Kod dla każdej właściwości jest również standardem w całej klasie. Poniższy kod dla `AddItemsParams` właściwości jest używany `AddItems()` w metodzie.

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

Zauważ, że właściwość używa prywatnej zmiennej lokalnej o nazwie `mAddItemsParams` , aby pomieścić wartość przed jej zwróceniem. Nazwa właściwości i nazwa klasy dla zwracanego obiektu są takie same. Klasa jest zdefiniowana w dalszej części pliku *UIMap.cs* .

Każda Klasa zwracana przez właściwość ma podobną strukturę. Poniżej `AddItemsParams` przedstawiono klasę:

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

Podobnie jak w przypadku wszystkich klas w pliku *UIMap.cs* , ta klasa rozpoczyna <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>się od. W tej małej klasie jest `Fields` region, który definiuje ciągi do użycia jako parametry <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> dla metody `UIMap.AddItems()` , która jest używana w metodzie, która została omówiona wcześniej. Można napisać kod, aby zastąpić wartości w tych polach ciągów przed zastosowaniem metody, w której te parametry są używane.

### <a name="UIMapCS"></a> UIMap.cs
Domyślnie ten plik zawiera klasę częściową `UIMap` , która nie ma metod lub właściwości.

#### <a name="uimap-class"></a>Klasa UIMap
Jest to miejsce, w którym można utworzyć niestandardowy kod, aby zwiększyć funkcjonalność klasy [UIMap](/previous-versions/dd580454(v=vs.140)) . Kod utworzony w tym pliku nie jest zastępowany przez **konstruktora kodowanego testu interfejsu użytkownika** za każdym razem, gdy test jest modyfikowany.

Wszystkie części [UIMap](/previous-versions/dd580454(v=vs.140)) mogą używać metod i właściwości z dowolnej innej części klasy [UIMap](/previous-versions/dd580454(v=vs.140)) .

### <a name="CodedUITestCS"></a>CodedUITest1.cs
Ten plik jest generowany przez **konstruktora kodowanego testu interfejsu użytkownika**, ale nie jest ponownie tworzony za każdym razem, gdy test jest modyfikowany, dzięki czemu można zmodyfikować kod w tym pliku. Nazwa pliku jest generowana na podstawie nazwy, która została określona dla testu podczas jego tworzenia.

#### <a name="codeduitest1-class"></a>Klasa CodedUITest1

Domyślnie ten plik zawiera definicję tylko jednej klasy.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) jest automatycznie stosowana do klasy, co pozwala platformie testowej rozpoznać ją jako rozszerzenie testowania. Zwróć również uwagę, że nie jest to Klasa częściowa. Wszystkie kody klasy są zawarte w tym pliku.

##### <a name="CodedUITestProperties"></a>Właściwości CodedUITest1

Klasa zawiera dwie domyślne właściwości, które znajdują się w dolnej części pliku. Nie należy ich modyfikować.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="CodedUITestMethods"></a>Metody CodedUITest1
Domyślnie Klasa zawiera tylko jedną metodę.

```csharp
public void CodedUITestMethod1()
```

Ta metoda wywołuje każdą `UIMap` metodę, która została określona podczas rejestrowania testu, która jest opisana w sekcji w [klasie UIMap](#UIMapClass).

Region, który jest zatytułowany `Additional test attributes`, w przypadku braku komentarza, zawiera dwie opcjonalne metody.

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

`MyTestInitialize()` Metoda<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> ma zastosowana do niej, która informuje platformę testowania do wywołania tej metody przed wszelkimi innymi metodami testowymi. `MyTestCleanup()` Podobnie Metoda<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> ma zastosowanie do niej, która informuje platformę testowania do wywołania tej metody po wywołaniu wszystkich innych metod testowych. Korzystanie z tych metod jest opcjonalne. Dla `UIMap.LaunchCalculator()` tego testu można wywołać metodę z `UIMap.CloseCalculator()` `MyTestInitialize()` i metodę można wywołać od `MyTestCleanup()` zamiast z `CodedUITest1Method1()`.

Jeśli dodasz więcej metod do tej klasy przy użyciu [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), Platforma testowa wywołuje każdą metodę jako część testu.

### <a name="UIMapuitest"></a> UIMap.uitest
Jest to plik XML, który reprezentuje strukturę rejestrowania kodowanego testu interfejsu użytkownika i jego części. Obejmują one akcje i klasy, a także metody i właściwości tych klas. Plik [UIMap.Designer.cs](#UIMapDesignerFile) zawiera kod generowany przez kodowany Konstruktor interfejsu użytkownika do odtwarzania struktury testu i zapewnia połączenie z platformą testowania.

Plik *UIMap. UITest* nie jest bezpośrednio edytowalny. Można jednak użyć kodowanego konstruktora interfejsu użytkownika, aby zmodyfikować test, który automatycznie modyfikuje plik *UIMap. UITest* i plik [*UIMap.Designer.cs*](#UIMapDesignerFile) .

## <a name="see-also"></a>Zobacz także

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)