---
title: Korzystanie ze składowych Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3b0e7cf2ddc4ada4fe015feba17c5adbcc328d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803270"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Korzystanie z członków Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Framework testów jednostkowych obsługuje testowanie jednostek w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Użyć klas i składowych w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzenią nazw, gdy kodują testów jednostkowych. Można je po napisaniu jednostki testów od podstaw lub są rafinacja test jednostkowy, który został wygenerowany z kodu, które testujesz.

## <a name="groups-of-elements"></a>Grupy elementów
 Aby zapewnić bardziej zrozumiały Omówienie środowiska testów jednostkowych w tej sekcji organizuje elementy przestrzeń nazw UnitTesting w grupy pokrewne funkcje.

> [!NOTE]
> Atrybut elementów, których nazwy zawierają ciąg atrybutu, można z lub bez ciągu atrybutu. Na przykład poniższe dwa przykłady kodu działać tak samo:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Elementy używane do testowania opartego na danych
 Konfigurowanie testów jednostkowych opartych na danych za pomocą następujących elementów. Aby uzyskać więcej informacji, zobacz [How to: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md) i [instruktażu: Korzystanie z pliku konfiguracji do określania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używany do ustanawiania kolejności wywoływania
 Element kodu dekorowane za pomocą jednej z następujących atrybutów jest wywoływana w tej chwili, które określisz. Aby uzyskać więcej informacji, zobacz [anatomia Test jednostkowy](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Dla zestawów
 AssemblyInitialize i AssemblyCleanup są nazywane prawo po załadowaniu zestawu i po prawej stronie przed zestawu jest zwalniana.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Dla klas
 ClassInitialize i ClassCleanup są nazywane po prawej stronie po załadowaniu klasy i w prawo przed klasy jest zwalniana.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Dla metod testowych

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty stosowane do identyfikowania, badania klasy i metody
 Każda klasa testu musi mieć atrybut TestClass i każdej metody testowej musi mieć atrybut TestMethod. Aby uzyskać więcej informacji, zobacz [anatomia Test jednostkowy](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Asercja klasy i powiązanych wyjątków
 Testy jednostkowe można sprawdzić działanie aplikacji przy ich użyciu różnego rodzaju instrukcje Assert, wyjątki i atrybuty. Aby uzyskać więcej informacji, zobacz [przy użyciu klas Asercja](../test/using-the-assert-classes.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Klasa TestContext
 Następujące atrybuty i wartości przypisane do nich są wyświetlane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno właściwości dla konkretnej metody testów. Te atrybuty nie mają być dostępne za pośrednictwem kodu testu jednostkowego. Zamiast tego wpływają na sposób testu jednostkowego lub uruchom następujący skrypt, albo przez użytkownika za pomocą IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aparat testów. Na przykład niektóre z tych atrybutów są wyświetlane jako kolumny w oknie programu Test Manager, a okno wyników testu, które oznacza, że za ich pomocą grupowanie i sortowanie testów i wyników testów. Jeden taki atrybut jest TestPropertyAttribute, którego używasz, aby dodać dowolne metadanych do testów jednostkowych. Na przykład użytkownik może służyć do przechowywania nazwę przebiegu testu, który obejmuje ten test, przez oznaczenie testów jednostkowych za pomocą `[TestProperty("TestPass", "Accessibility")]`. Lub można go użyć do przechowywania wskazuje rodzaj testu jest: `[TestProperty("TestKind", "Localization")]`. Właściwości tworzenia przy użyciu tego atrybutu, a wartość właściwości, możesz przypisać zarówno wyświetlanych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno właściwości pod nagłówkiem **konkretnego testu**.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Klas konfiguracji testu

-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Atrybuty stosowane do generowania raportów
 Atrybuty w tej sekcji dotyczą metodę testową, która ich dekoracji do jednostek w hierarchii projektu [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] projektu zespołowego.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy stosowane przy użyciu prywatnych metod dostępu
 Zgodnie z opisem w [przy użyciu Publicize, aby utworzyć prywatny akcesor](http://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb), można wygenerować testu jednostkowego dla metody prywatnej. Ta generacja tworzy klasie prywatnego akcesora, która tworzy obiekt klasy obiektu PrivateObject. Klasa obiektu PrivateObject jest klasą otoki, która używa odbicia w ramach procesu prywatnego akcesora. Klasa PrivateType są podobne, ale jest używany do wywoływania prywatnej metody statyczne, zamiast wywoływania metod wystąpieniem prywatnym.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>