---
title: Użyj MSTest w testach jednostkowych
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 759eaded70c3e95b76123062e00072aced4ecdfa
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810539"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Używanie struktury MSTest w testach jednostkowych

Środowisko [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) Framework obsługuje testy jednostkowe w programie Visual Studio. Używaj klas i elementów członkowskich w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw podczas kodowania testów jednostkowych. Można ich również użyć podczas rafinacji testu jednostkowego, który został wygenerowany z kodu.

## <a name="framework-members"></a>Elementy członkowskie struktury

Aby zapewnić bardziej przejrzyste Omówienie struktury testów jednostkowych, ta sekcja organizuje elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw w grupach powiązanych funkcji.

> [!NOTE]
> Elementy atrybutu, których nazwy kończą się znakiem "Attribute", mogą być używane z lub bez atrybutu "Attribute" na końcu. Na przykład następujące dwa przykłady kodu działają identycznie:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Elementy członkowskie używane do testowania opartego na danych

Aby skonfigurować testy jednostkowe oparte na danych, należy użyć następujących elementów. Aby uzyskać więcej informacji, zobacz [Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md) i [użycie pliku konfiguracji w celu zdefiniowania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używane do ustanowienia kolejności wywoływania

Element kodu z jednym z następujących atrybutów jest wywoływany w określonym momencie. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Atrybuty dla zestawów

Atrybutem AssemblyInitialize i atrybutem assemblycleanup są wywoływane bezpośrednio po załadowaniu zestawu i po prawej stronie przed odładowaniem zestawu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atrybuty klas

ClassInitialize i ClassCleanup są wywoływane bezpośrednio po załadowaniu klasy i po prawej stronie przed odładowaniem klasy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atrybuty metod testowych

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty używane do identyfikowania klas i metod testowych

Każda Klasa testowa musi mieć `TestClass` atrybut, a każda metoda testowa musi mieć `TestMethod` atrybut. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Klasy Assert i powiązane wyjątki

Testy jednostkowe mogą weryfikować określone zachowanie aplikacji przy użyciu różnych rodzajów potwierdzeń, wyjątków i atrybutów. Aby uzyskać więcej informacji, zobacz [Korzystanie z klas potwierdzeń](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Klasa TestContext

Następujące atrybuty i przypisane do nich wartości są wyświetlane w okno Właściwości programu Visual Studio dla konkretnej metody testowej. Te atrybuty nie są przeznaczone do dostępu za pomocą kodu testu jednostkowego. Zamiast tego wpływają na sposób, w jaki testy jednostkowe są używane lub uruchamiane, przez środowisko IDE programu Visual Studio lub przez aparat testowy programu Visual Studio. Na przykład niektóre z tych atrybutów są wyświetlane jako kolumny w oknie **Test Manager** i **wyniki testów** , co oznacza, że można ich użyć do grupowania i sortowania testów i wyników testów. Ten atrybut jest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> używany do dodawania dowolnych metadanych do testów jednostkowych. Na przykład można go użyć do przechowywania nazwy przebiegu testu, który obejmuje ten test, poprzez oznaczenie testu jednostkowego za pomocą `[TestProperty("TestPass", "Accessibility")]` . Lub można go użyć do przechowywania wskaźnika rodzaju testowego `[TestProperty("TestKind", "Localization")]` . Właściwość tworzona przy użyciu tego atrybutu i wartość właściwości, którą można przypisać, są wyświetlane w oknie **Właściwości** programu Visual Studio pod **konkretnym testem**nagłówka.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Klasy konfiguracji testu

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atrybuty używane do generowania raportów

Atrybuty w tej sekcji odnoszą się do metody testowej, która dekorować do jednostek w hierarchii projektu Team Foundation Server projektu zespołowego.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy używane z prywatnymi dostępem

Można wygenerować test jednostkowy dla metody prywatnej. Ta generacja powoduje utworzenie prywatnej klasy dostępu, która tworzy wystąpienie obiektu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> klasy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>Klasa jest klasą otoki, która używa odbicia w ramach procesu prywatnego dostępu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>Klasa jest podobna, ale jest używana do wywoływania prywatnych metod statycznych zamiast wywoływania prywatnych metod wystąpień.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Dokumentacja referencyjna