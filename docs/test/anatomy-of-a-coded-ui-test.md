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
ms.openlocfilehash: 18a2da2ad79a91ca90a749471765970cfd7a1cbd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911523"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomia kodowanego testu interfejsu użytkownika

Podczas tworzenia kodowanych testów interfejsu użytkownika w projekt kodowanego testu interfejsu użytkownika kilka plików są dodawane do rozwiązania. Ten artykuł zawiera informacje o plikach.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Zawartość kodowanego testu interfejsu użytkownika

Podczas tworzenia kodowanych testów interfejsu użytkownika, **Konstruktor kodowanego testu IU** tworzy mapę interfejsu użytkownika w ramach testu i również metody testowe, parametry i potwierdzenia dla wszystkich testów. Tworzy również plik klasy dla każdego testu.

|Plik|Spis treści|Można edytować?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sekcja deklaracji](#UIMapDesignerFile)<br /><br /> [Klasa UIMap](#UIMapClass) (częściowych, wygenerowany automatycznie)<br /><br /> [Metody](#UIMapMethods)<br /><br /> [Właściwości](#UIMapProperties)|Nie|
|[UIMap.cs](#UIMapCS)|[Klasa UIMap](#UIMapCS) (częściowa)|Tak|
|[CodedUITest1.cs](#CodedUITestCS)|[Klasa CodedUITest1](#CodedUITestCS)<br /><br /> [Metody](#CodedUITestMethods)<br /><br /> [Właściwości](#CodedUITestProperties)|Tak|
|[UIMap.uitest](#UIMapuitest)|Mapa XML w interfejsie użytkownika dla testu.|Nie|

###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs
 Ten plik zawiera kod, który jest automatycznie tworzona przez **Konstruktor kodowanego testu IU** po utworzeniu testu. Ten plik jest tworzony ilekroć dany test zmieni się, ponownie, tak aby nie jest plikiem, w którym można dodać lub zmodyfikować kod.

#### <a name="declarations-section"></a>Sekcja deklaracji
 Ta sekcja zawiera następujące deklaracje dla interfejsu użytkownika Windows.

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

 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> Przestrzeń nazw jest uwzględniane dla Windows interfejsu użytkownika (UI). Dla strony sieci web interfejsu użytkownika będzie przestrzeń nazw <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; Windows Presentation Foundation interfejsu użytkownika, przestrzeń nazw będzie <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.

####  <a name="UIMapClass"></a> Klasa UIMap
 Następna sekcja pliku <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy.

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Zaczyna się kod klasy <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atrybut, który jest stosowany do klasy, która jest zadeklarowana jako klasy częściowej. Należy zauważyć, że jest również stosowany do każdej klasy, w tym pliku. Plik, który może zawierać więcej kodu dla tej klasy jest *UIMap.cs*, które omówiono w dalszej części.

Wygenerowany `UIMap` klasy zawiera kod dla każdej metody, która została określona podczas testu została zarejestrowana.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Ta część <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasa zawiera także wygenerowanego kodu dla każdej właściwości, która jest wymagana przez metody.

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

#####  <a name="UIMapMethods"></a> Metody do UIMap
 Każda metoda charakteryzuje się podobną strukturę `AddItems()` metody. Jest to wyjaśnione bardziej szczegółowo w ramach kodu, które są prezentowane wraz z podziałów wiersza, aby dodać przejrzystości.

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

Podsumowanie komentarz dla każdej definicji metody informuje klasy wartości parametrów dla tej metody. W tym przypadku jest to `AddItemsParams` klasy, która jest zdefiniowana później w *UIMap.cs* plików i który jest także typ wartości, który jest zwracany przez `AddItemsParams` właściwości.

 W górnej części metody kod jest `Variable Declarations` region, który definiuje zmiennych lokalnych dla interfejsu użytkownika obiekty, które są używane przez metodę.

 W przypadku tej metody zarówno `UIItemWindow` i `UIItemEdit` są właściwościami, które są dostępne przy użyciu `UICalculatorWindow` klasy, która jest zdefiniowana później w *UIMap.cs* pliku.

 Następnie są wiersze, które przesyłają tekstu przy użyciu klawiatury aplikacja Kalkulator przy użyciu właściwości `AddItemsParams` obiektu.

 `VerifyTotal()` Metoda ma podobną strukturę i zawiera następujący kod potwierdzenia:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

 Nazwa pola tekstowego jest wyświetlany jako nieznane, ponieważ dla deweloperów aplikacji Windows Kalkulator nie dostarczył publicznie dostępnych nazwę kontrolki. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> Metoda nie powiedzie się, gdy rzeczywista wartość nie jest równa oczekiwanej wartości, które mogłyby spowodować niepowodzenie testu. Zwróć również uwagę, że oczekiwana wartość zawiera punktu dziesiętnego, który następuje spacja. Będzie trzeba zmodyfikować funkcje tego określonego testu, muszą zezwalać na dla tego punktu dziesiętnego i miejsca.

#####  <a name="UIMapProperties"></a> Właściwości UIMap
 Kod dla każdej właściwości jest również standardowego w całej klasy. Poniższy kod dla `AddItemsParams` właściwość jest używana w `AddItems()` metody.

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

 Zwróć uwagę, że właściwość używa prywatnej zmiennej lokalnej, która nosi nazwę `mAddItemsParams` zawierającą wartość parametru przed jego zwracaniem. Nazwa właściwości i nazwa klasy dla obiektu, który zwraca są takie same. Klasa jest zdefiniowana później w *UIMap.cs* pliku.

 Każda klasa, która jest zwracana przez właściwość podobnie mają strukturę. Poniżej przedstawiono `AddItemsParams` klasy:

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

Podobnie jak w przypadku wszystkich klas *UIMap.cs* pliku, ta klasa zaczyna się od <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. W tej klasie małych jest `Fields` region, który definiuje ciągów do użycia jako parametry dla <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> metodę, która jest używana w `UIMap.AddItems()` metodę, która została omówiony wcześniej. Można napisać kod, aby zastąpić wartości w polach ciągu przed wywołaniem metody, w którym są używane te parametry.

###  <a name="UIMapCS"></a> UIMap.cs
 Domyślnie ten plik zawiera częściowym `UIMap` klasę, która nie ma metody lub właściwości.

#### <a name="uimap-class"></a>Klasa UIMap
 Jest to, gdzie możesz utworzyć niestandardowy kod, aby rozszerzyć funkcjonalność <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy. Kod, który zostanie utworzony w tym pliku nie zostanie zastąpiona **Konstruktor kodowanego testu IU** ilekroć dany test zostanie zmodyfikowany.

 Wszystkie części <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> można użyć metod i właściwości z inną częścią <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy.

###  <a name="CodedUITestCS"></a> CodedUITest1.cs
 Ten plik jest generowany przez **Konstruktor kodowanego testu IU**, ale nie zostanie ponownie utworzone ilekroć dany test został zmodyfikowany, dzięki czemu można zmodyfikować kod, w tym pliku. Nazwa pliku jest generowany na podstawie nazwy, która określonych dla testu, podczas jego tworzenia.

#### <a name="codeduitest1-class"></a>Klasa CodedUITest1

Domyślnie ten plik zawiera definicję dla tylko jedną klasę.

```csharp
[CodedUITest]
public class CodedUITest1
```

<xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute> Jest automatycznie stosowany do klasy, która umożliwia struktura testowania, rozpoznawał ją jako rozszerzenia testowania. Także zauważyć, że nie jest klasy częściowej. Cały kod klasy znajduje się w tym pliku.

#####  <a name="CodedUITestProperties"></a> Właściwości CodedUITest1

Klasa zawiera dwa domyślne właściwości, które znajdują się w dolnej części pliku. Nie należy modyfikować je.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

#####  <a name="CodedUITestMethods"></a> Metody CodedUITest1
 Domyślnie klasa zawiera tylko jedną metodę.

```csharp
public void CodedUITestMethod1()
```

 Ta metoda wywołuje każdą `UIMap` metody, który określiłeś, których zarejestrowano test, który został opisany w sekcji na [klasy UIMap](#UIMapClass).

 Region, który jest zatytułowana `Additional test attributes`, jeśli odkomentowana, zawiera dwie metody opcjonalne.

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

 `MyTestInitialize()` Metoda ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> zastosowano, która informuje o tym struktura testowania, aby wywołać tę metodę, zanim innych metod testowych. Podobnie `MyTestCleanup()` metoda ma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> zastosowano, informuje, struktura testowania, aby wywołać tę metodę, gdy wszystkie inne metody testowe zostały wywołane. Korzystanie z tych metod jest opcjonalne. W tym teście `UIMap.LaunchCalculator()` metoda może być wywoływana ze `MyTestInitialize()` i `UIMap.CloseCalculator()` metoda może być wywoływana ze `MyTestCleanup()` zamiast z `CodedUITest1Method1()`.

 Jeśli dodasz więcej metod do tej klasy przy użyciu <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, struktura testowania wywołuje każdą z tych metod jako część testu.

###  <a name="UIMapuitest"></a> UIMap.uitest
 Jest to plik XML, reprezentuje strukturę coded UI przetestować rejestrowania i jego części. Obejmują one akcje i klas, oprócz tych metod i właściwości tych klas. [UIMap.Designer.cs](#UIMapDesignerFile) plik zawiera kod, który został wygenerowany przez konstruktora kodowanego interfejsu użytkownika, aby odtworzyć strukturę testu i udostępnia połączenie struktura testowania.

 *UIMap.uitest* plik nie jest edytowalny bezpośrednio. Jednak można użyć konstruktora kodowanego interfejsu użytkownika do modyfikowania testu, który automatycznie zmienia *UIMap.uitest* pliku i [ *UIMap.Designer.cs* ](#UIMapDesignerFile) pliku.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)