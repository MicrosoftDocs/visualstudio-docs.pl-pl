---
title: Użyj microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e45df63f36947b5f6f0aad77bb8eebcab4aca731
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585564"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Użyj struktury MSTest w testach jednostkowych

Struktura [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) obsługuje testowanie jednostek w programie Visual Studio. Użyj klas i członków <xref:Microsoft.VisualStudio.TestTools.UnitTesting> w obszarze nazw podczas kodowania testów jednostkowych. Można ich również użyć podczas udoskonalania testu jednostkowego, który został wygenerowany na podstawie kodu.

## <a name="framework-members"></a>Elementy członkowskie ram

Aby zapewnić bardziej przejrzysty przegląd struktury testowania jednostek, w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> tej sekcji organizuje członków obszaru nazw w grupy powiązanych funkcji.

> [!NOTE]
> Elementy atrybutu, których nazwy kończą się na "Atrybut", mogą być używane z lub bez "Atrybut" na końcu. Na przykład następujące dwa przykłady kodu działają identycznie:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Elementy członkowskie używane do testowania opartego na danych

Poniższe elementy można użyć do skonfigurowania testów jednostkowych opartych na danych. Aby uzyskać więcej informacji, zobacz [Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md) i [definiowanie źródła danych za pomocą pliku konfiguracyjnego.](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używane do ustanawiania kolejności wywołującej

Element kodu ozdobiony jednym z następujących atrybutów jest wywoływana w momencie określonym. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atrybuty dla zestawów

AssemblyInitialize i AssemblyCleanup są wywoływane zaraz po załadowaniu zestawu i tuż przed rozładowaniem zestawu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atrybuty dla klas

ClassInitialize i ClassCleanup są wywoływane zaraz po załadowaniu klasy i tuż przed rozładowaniem klasy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atrybuty metod testowych

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty używane do identyfikowania klas i metod testów

Każda klasa testowa `TestClass` musi mieć atrybut, a `TestMethod` każda metoda testowa musi mieć atrybut. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert klasy i powiązane wyjątki

Testy jednostkowe można zweryfikować zachowanie określonej aplikacji przez ich użycie różnych rodzajów potwierdzeń, wyjątków i atrybutów. Aby uzyskać więcej informacji, zobacz [Korzystanie z assert klasy](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Klasa TestContext

Następujące atrybuty i wartości przypisane do nich pojawiają się w oknie Właściwości programu Visual Studio dla określonej metody testowej. Te atrybuty nie są przeznaczone do uzyskania dostępu za pośrednictwem kodu testu jednostkowego. Zamiast tego wpływają one na sposób, w jaki test jednostkowy jest używany lub uruchamiany przez ciebie za pośrednictwem środowiska IDE programu Visual Studio lub przez aparat testowy programu Visual Studio. Na przykład niektóre z tych atrybutów są wyświetlane jako kolumny w oknie **Menedżer testów** i **wyniki testów,** co oznacza, że można ich używać do grupowania i sortowania testów i wyników testów. Jednym z takich <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>atrybutów jest , którego używasz do dodawania dowolnych metadanych do testów jednostkowych. Na przykład można go użyć do przechowywania nazwy przebiegu testu, który obejmuje `[TestProperty("TestPass", "Accessibility")]`ten test, zaznaczając test jednostkowy za pomocą . Lub, można go użyć do przechowywania wskaźnika tego `[TestProperty("TestKind", "Localization")]`rodzaju testu jest z . Właściwość utworzona przy użyciu tego atrybutu i przypisywana wartość właściwości są wyświetlane w oknie **Właściwości** programu Visual Studio pod nagłówkiem **Test specyficzny.**

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Klasy konfiguracji testu

- [Typy obiektów](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atrybuty używane do generowania raportów

Atrybuty w tej sekcji odnoszą się do metody testowej, które zdobią do jednostek w hierarchii projektu projektu team foundation server zespołu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy używane z prywatnymi akcesorami

Można wygenerować test jednostkowy dla metody prywatnej. Ta generacja tworzy klasę akcesora prywatnego, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> która tworzy wystąpienie obiektu klasy. Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> jest klasą otoki, która używa odbicia jako część procesu prywatnego akcesora. Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> jest podobna, ale służy do wywoływania prywatnych metod statycznych zamiast wywoływania metod wystąpienia prywatnego.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>dokumentacja referencyjna
