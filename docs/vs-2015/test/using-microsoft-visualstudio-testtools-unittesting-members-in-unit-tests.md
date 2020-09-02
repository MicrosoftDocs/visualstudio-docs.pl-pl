---
title: Używanie elementów członkowskich Microsoft. VisualStudio. TestTools. UnitTesting w testach jednostkowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e8b3ea10b96a63bd18098030dc884ac3f3383353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657185"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Korzystanie z członków Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Architektura testowania jednostkowego obsługuje testy jednostkowe w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Używaj klas i elementów członkowskich w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw podczas kodowania testów jednostkowych. Można ich użyć, gdy użytkownik zapisał test jednostkowy od podstaw lub zawęża test jednostkowy, który został wygenerowany na podstawie testowanego kodu.

## <a name="groups-of-elements"></a>Grupy elementów
 Aby zapewnić bardziej przejrzyste Omówienie struktury testów jednostkowych, ta sekcja organizuje elementy przestrzeni nazw UnitTesting w grupach powiązanych funkcji.

> [!NOTE]
> Elementy atrybutu, których nazwy kończą się atrybutem String, mogą być używane z atrybutem String lub bez niego. Na przykład następujące dwa przykłady kodu działają identycznie:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Elementy używane do testowania opartego na danych
 Aby skonfigurować testy jednostkowe oparte na danych, należy użyć następujących elementów. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md) i [Przewodnik: korzystanie z pliku konfiguracji w celu zdefiniowania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używane do ustanowienia kolejności wywoływania
 Element kodu z jednym z następujących atrybutów jest wywoływany w określonym momencie. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Dla zestawów
 Atrybutem AssemblyInitialize i atrybutem assemblycleanup są wywoływane bezpośrednio po załadowaniu zestawu i po prawej stronie przed odładowaniem zestawu.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Dla klas
 ClassInitialize i ClassCleanup są wywoływane bezpośrednio po załadowaniu klasy i po prawej stronie przed odładowaniem klasy.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Dla metod testowych

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty używane do identyfikowania klas i metod testowych
 Każda Klasa testowa musi mieć atrybut TestClass, a każda metoda testowa musi mieć atrybut TestMethod. Aby uzyskać więcej informacji, zobacz [Anatomia testu jednostkowego](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Klasy Assert i powiązane wyjątki
 Testy jednostkowe mogą weryfikować określone zachowanie aplikacji przy użyciu różnych rodzajów instrukcji Assert, wyjątków i atrybutów. Aby uzyskać więcej informacji, zobacz [Korzystanie z klas potwierdzeń](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Klasa TestContext
 Następujące atrybuty i przypisane do nich wartości są wyświetlane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno właściwości dla konkretnej metody testowej. Te atrybuty nie są przeznaczone do dostępu za pomocą kodu testu jednostkowego. Zamiast tego wpływają na sposób, w jaki testy jednostkowe są używane lub uruchamiane, przez środowisko IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aparat testowy. Na przykład niektóre z tych atrybutów są wyświetlane jako kolumny w oknie Test Manager i Wyniki testów, co oznacza, że można ich użyć do grupowania i sortowania testów i wyników testów. Jeden taki atrybut to TestPropertyAttribute, który służy do dodawania dowolnych metadanych do testów jednostkowych. Na przykład można go użyć do przechowywania nazwy przebiegu testu, który obejmuje ten test, poprzez oznaczenie testu jednostkowego za pomocą `[TestProperty("TestPass", "Accessibility")]` . Lub można go użyć do przechowywania wskaźnika rodzaju testu: `[TestProperty("TestKind", "Localization")]` . Właściwość tworzona przy użyciu tego atrybutu i wartość właściwości, którą można przypisać, są wyświetlane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno właściwości pod **konkretnym testem**nagłówka.

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

## <a name="attributes-used-for-generating-reports"></a>Atrybuty używane do generowania raportów
 Atrybuty w tej sekcji odnoszą się do metody testowej, która dekorować do jednostek w hierarchii projektu [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] projektu zespołowego.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy używane z prywatnymi dostępem
 Zgodnie z opisem w temacie [using InPrivate by utworzyć prywatny akcesor](https://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb), można wygenerować test jednostkowy dla metody prywatnej. Ta generacja powoduje utworzenie prywatnej klasy dostępu, która tworzy wystąpienie obiektu klasy PrivateObject. Klasa PrivateObject jest klasą otoki, która używa odbicia w ramach procesu prywatnego dostępu. Klasa PrivateType jest podobna, ale jest używana do wywoływania prywatnych metod statycznych zamiast wywoływania prywatnych metod wystąpień.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>