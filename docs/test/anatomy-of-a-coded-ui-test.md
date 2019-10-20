---
title: Anatomia kodowanego testu interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c1757c687ea48ee1f2770fa320a18da5662f43e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665308"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomia kodowanego testu interfejsu użytkownika

Po utworzeniu kodowanego testu interfejsu użytkownika w projekcie kodowanego testu interfejsu użytkownika do rozwiązania dodawane są kilka plików. Ten artykuł zawiera informacje o plikach.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Zawartość kodowanego testu interfejsu użytkownika

W przypadku tworzenia kodowanego testu interfejsu użytkownika **Konstruktor kodowanego testu interfejsu** użytkownika tworzy mapę testowanego interfejsu użytkownika, a także metod testowych, parametrów i potwierdzeń dla wszystkich testów. Tworzy również plik klasy dla każdego testu.

|Plik|Spis treści|Modyfikować?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sekcja deklaracji](#UIMapDesignerFile)<br /><br /> [Klasa UIMap](#UIMapClass) (częściowa, wygenerowana automatycznie)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Właściwości](#UIMapProperties)|Nie|
|[UIMap.cs](#UIMapCS)|[Klasa UIMap](#UIMapCS) (częściowa)|Tak|
|[CodedUITest1.cs](#CodedUITestCS)|[Klasa CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Właściwości](#CodedUITestProperties)|Tak|
|[UIMap. UITest](#UIMapuitest)|Mapa XML interfejsu użytkownika dla testu.|Nie|

### <a name="UIMapDesignerFile"></a>UIMap.Designer.cs
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

Przestrzeń nazw <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> jest dołączona do interfejsu użytkownika systemu Windows. W przypadku interfejsu użytkownika strony sieci Web przestrzeń nazw byłaby <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; w przypadku interfejsu użytkownika Windows Presentation Foundation przestrzeń nazw byłaby <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.

#### <a name="UIMapClass"></a>Klasa UIMap
Następna sekcja pliku jest klasą [UIMap](/previous-versions/dd580454(v=vs.140)) .

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Kod klasy zaczyna się od atrybutu <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>, który jest stosowany do klasy, która jest zadeklarowana jako Klasa częściowa. Należy zauważyć, że atrybut jest również stosowany do każdej klasy w tym pliku. Innym plikiem, który może zawierać więcej kodu dla tej klasy, jest *UIMap.cs*, który został omówiony później.

Wygenerowana Klasa `UIMap` obejmuje kod dla każdej metody, która została określona podczas rejestrowania testu.

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
Każda metoda ma strukturę przypominającą metodę `AddItems()`. Wyjaśniono to bardziej szczegółowo w kodzie, który jest prezentowany wraz z podziałami wierszy w celu dodania przejrzystości.

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

Komentarz podsumowania dla każdej definicji metody wskazuje klasę, która ma być używana dla wartości parametrów dla tej metody. W tym przypadku jest to Klasa `AddItemsParams`, która jest zdefiniowana w dalszej części pliku *UIMap.cs* , a także typ wartości, który jest zwracany przez właściwość `AddItemsParams`.

W górnej części kodu metody jest region `Variable Declarations`, który definiuje zmienne lokalne dla obiektów interfejsu użytkownika, które są używane przez metodę.

W tej metodzie zarówno `UIItemWindow`, jak i `UIItemEdit` są właściwościami, do których uzyskuje się dostęp przy użyciu klasy `UICalculatorWindow`, która jest zdefiniowana w dalszej części pliku *UIMap.cs* .

Następnie są wiersze, które wysyłają tekst z klawiatury do aplikacji Kalkulator przy użyciu właściwości obiektu `AddItemsParams`.

Metoda `VerifyTotal()` ma podobną strukturę i zawiera następujący kod potwierdzenia:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Nazwa pola tekstowego jest wyświetlana jako nieznana, ponieważ Deweloper aplikacji kalkulatora systemu Windows nie dostarczył publicznie dostępnej nazwy dla kontrolki. Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> kończy się niepowodzeniem, gdy rzeczywista wartość nie jest równa oczekiwanej wartości, co może spowodować niepowodzenie testu. Zauważ również, że oczekiwana wartość zawiera punkt dziesiętny, po którym następuje spacja. Jeśli kiedykolwiek zajdzie potrzeba zmodyfikowania funkcjonalności tego konkretnego testu, należy zezwolić na ten punkt dziesiętny oraz miejsce.

##### <a name="UIMapProperties"></a>Właściwości UIMap
Kod dla każdej właściwości jest również standardem w całej klasie. Poniższy kod dla właściwości `AddItemsParams` jest używany w `AddItems()` metodzie.

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

Należy zauważyć, że właściwość używa prywatnej zmiennej lokalnej o nazwie `mAddItemsParams`, aby pomieścić wartość przed jej zwróceniem. Nazwa właściwości i nazwa klasy dla zwracanego obiektu są takie same. Klasa jest zdefiniowana w dalszej części pliku *UIMap.cs* .

Każda Klasa zwracana przez właściwość ma podobną strukturę. Poniżej znajduje się Klasa `AddItemsParams`:

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

Podobnie jak w przypadku wszystkich klas w pliku *UIMap.cs* , ta klasa rozpoczyna się od <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. W tej małej klasie jest `Fields` region, który definiuje ciągi do użycia jako parametry metody <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>, która jest używana w metodzie `UIMap.AddItems()`, która została omówiona wcześniej. Można napisać kod, aby zastąpić wartości w tych polach ciągów przed zastosowaniem metody, w której te parametry są używane.

### <a name="UIMapCS"></a>UIMap.cs
Domyślnie ten plik zawiera częściową klasę `UIMap`, która nie ma metod lub właściwości.

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

Ta metoda wywołuje każdą metodę `UIMap` określoną podczas rejestrowania testu, która jest opisana w sekcji w [klasie UIMap](#UIMapClass).

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

Do metody `MyTestInitialize()` zastosowano <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>, która informuje platformę testową, aby wywołać tę metodę przed wszelkimi innymi metodami testowymi. Analogicznie, Metoda `MyTestCleanup()` ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> zastosowana do niej, co informuje platformę testowania do wywołania tej metody po wywołaniu wszystkich innych metod testowych. Korzystanie z tych metod jest opcjonalne. Dla tego testu Metoda `UIMap.LaunchCalculator()` może zostać wywołana z `MyTestInitialize()`, a metoda `UIMap.CloseCalculator()` może zostać wywołana z `MyTestCleanup()` zamiast z `CodedUITest1Method1()`.

Jeśli dodasz więcej metod do tej klasy przy użyciu [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), Platforma testowa wywołuje każdą metodę jako część testu.

### <a name="UIMapuitest"></a>UIMap. UITest
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
- [Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)