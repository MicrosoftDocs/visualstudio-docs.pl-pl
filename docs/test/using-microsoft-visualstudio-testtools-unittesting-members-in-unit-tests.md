---
title: Użyj Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych
ms.date: 03/02/2018
ms.topic: reference
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f3f488d021be59538eac36a19a66970b9fc01463
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432228"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Użyj struktury MSTest w testach jednostkowych

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) framework obsługuje testowanie jednostek w programie Visual Studio. Użyć klas i składowych w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzenią nazw, gdy kodują testów jednostkowych. Umożliwia także je uściślając test jednostkowy, który został wygenerowany z kodu.

## <a name="framework-members"></a>Elementy członkowskie Framework

Aby zapewnić bardziej zrozumiały omówienie testowania jednostkowego, w tej sekcji służy do organizowania elementów członkowskich <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw w grupach pokrewne funkcje.

> [!NOTE]
> Atrybut elementów, których nazwy kończą się ciągiem "Attribute", można z lub bez "Atrybutu" na końcu. Na przykład poniższe dwa przykłady kodu działać tak samo:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Elementy członkowskie do testowania opartego na danych

Konfigurowanie testów jednostkowych opartych na danych za pomocą następujących elementów. Aby uzyskać więcej informacji, zobacz [tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md) i [przy użyciu pliku konfiguracji do określania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używany do ustanawiania kolejności wywołań

Element kodu dekorowane za pomocą jednej z następujących atrybutów jest wywoływana w tej chwili, które określisz. Aby uzyskać więcej informacji, zobacz [anatomia test jednostkowy](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atrybuty dla zestawów

AssemblyInitialize i AssemblyCleanup są nazywane prawo po załadowaniu zestawu i po prawej stronie przed zestawu jest zwalniana.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atrybuty klasy

ClassInitialize i ClassCleanup są nazywane po prawej stronie po załadowaniu klasy i w prawo przed klasy jest zwalniana.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atrybuty dla metod testowych

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty stosowane do identyfikowania, badania klasy i metody

Każda klasa testu musi mieć `TestClass` musi mieć atrybut i każdej metody testowej `TestMethod` atrybutu. Aby uzyskać więcej informacji, zobacz [anatomia test jednostkowy](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Asercja klasy i powiązanych wyjątków

Testy jednostkowe można sprawdzić zachowanie określonej aplikacji, ich użycie różnych rodzajów atrybutów, wyjątki i potwierdzenia. Aby uzyskać więcej informacji, zobacz [korzystanie z klas potwierdzeń](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Klasa TestContext

Następujące atrybuty i wartości przypisane do nich są wyświetlane w oknie właściwości usługi Visual Studio dla konkretnej metody testów. Te atrybuty nie mają być dostępne za pośrednictwem kodu testu jednostkowego. Zamiast tego wpływają na sposób test jednostkowy jest używany lub uruchamiania przez użytkownika za pośrednictwem środowiska IDE programu Visual Studio lub przez silnik testowy programu Visual Studio. Na przykład, niektóre z tych atrybutów są wyświetlane jako kolumny w **Test Manager** okna i **wyników testu** okno, które oznacza, że za ich pomocą grupowanie i sortowanie testów i wyników testów. Jest jeden taki atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, którego używasz, aby dodać dowolne metadanych do testów jednostkowych. Na przykład użytkownik może służyć do przechowywania nazwę przebiegu testu, który obejmuje ten test, przez oznaczenie testów jednostkowych za pomocą `[TestProperty("TestPass", "Accessibility")]`. Lub można go użyć do przechowywania wskazuje rodzaj testu w przypadku `[TestProperty("TestKind", "Localization")]`. Właściwości tworzenia przy użyciu tego atrybutu, a wartość właściwości, możesz przypisać zarówno wyświetlanych w programie Visual Studio **właściwości** okna pod pozycją **konkretnego testu**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Klas konfiguracji testu

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atrybuty używane do generowania raportów

Atrybuty w tej sekcji odnoszą się metodę testową, która ich dekoracji do jednostek w hierarchii projektu dla projektu zespołowego Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy stosowane przy użyciu prywatnych metod dostępu

Można wygenerować testu jednostkowego dla metody prywatnej. Ta generacja tworzy klasie prywatnego akcesora, który tworzy wystąpienie obiektu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> klasy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> Klasa jest klasą otoki, która używa odbicia w ramach procesu prywatnego akcesora. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> Klasy jest podobna, ale jest używany do wywoływania prywatnej metody statyczne, zamiast wywoływania metod wystąpieniem prywatnym.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Dokumentacja referencyjna
