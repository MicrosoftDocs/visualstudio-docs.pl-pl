---
title: Scalanie XML w funkcji i pakietów manifestach | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8af9386d192c6dd96669dbfada298317cf5fe0e5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646307"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Scalanie XML w funkcji i wykazu manifestów
  Funkcji i pakietów, które są definiowane przez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki manifestu. Te manifesty spakowanych są kombinacją danych generowanych przez projektantów i niestandardowe [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] wprowadzone w szablonie manifestu przez użytkowników. W czasie tworzenia pakietów [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scala niestandardowej [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcje z warunkiem projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] w celu utworzenia spakowanych [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliku manifestu. Podobnych elementów, z wyjątkiem wymienionych w dalszej części scalania wyjątków, są scalane w celu uniknięcia [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] błędy sprawdzania poprawności po wdrażanie plików w programie SharePoint i zapewnienie manifest pliki mniejszy i wydajniejszy.

## <a name="modify-the-manifests"></a>Modyfikowanie manifestów
 Nie można bezpośrednio modyfikować plików manifestu w pakiecie, dopóki nie wyłączysz funkcji i pakietów projektantów. Jednakże, można ręcznie dodawać niestandardowe [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy do manifestu szablonu za pomocą projektantów funkcji i pakietów lub [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] edytora. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) i [jak: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Funkcji i pakietów manifestu procesu scalania
 Podczas łączenia elementów niestandardowych, wraz z elementami dostarczone do projektanta, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przystępuje do następującej procedury. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sprawdza, czy każdy element ma unikatową wartość klucza. Jeśli element nie ma unikatowy klucza wartości, jest ona dołączana do pakowanego pliku manifestu. Podobnie nie można scalić elementy, które mają wiele kluczy. W związku z tym są dołączane do pliku manifestu.

 Jeśli element ma unikatowy klucz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] porównuje wartości wystąpienia projektanta i klucze niestandardowe. Jeśli wartości są zgodne, scalają w jedną wartość. Jeśli wartości są różne, projektanta wartość klucza jest odrzucana i wartość klucza niestandardowego jest używany. Scalane są także kolekcje. Na przykład jeśli wygenerowanym przez projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] i niestandardowej [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zarówno zawiera kolekcję zestawów, pakowanego manifestu zawiera tylko jedna kolekcja zestawów.

## <a name="merge-exceptions"></a>Scal wyjątków
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scala projektanta większość [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów wraz z podobną niestandardową [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tak długo, jak mają pojedynczej unikatowy atrybut identyfikujący elementów. Jednak niektóre elementy nie mają unikatowy identyfikator, które są wymagane dla [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] scalania. Te elementy są nazywane *scalania wyjątki*. W takich przypadkach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scalaj niestandardowej [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów wraz z warunkiem projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów, ale zamiast tego dołącza je do pliku manifestu spakowanych.

 Poniżej przedstawiono listę wyjątków scalania dla funkcji i pakietów [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki manifestu.

|Projektant|XML Element|
|--------------|-----------------|
|Funkcja projektanta|ActivationDependency|
|Funkcja projektanta|UpgradeAction|
|Projektanta pakietów|SafeControl|
|Projektanta pakietów|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementy manifestu funkcji
 Poniższa tabela jest lista wszystkich elementów manifestu funkcji, które mogą zostać scalone ich Unikatowy klucz, który jest używany do dopasowania.

|Nazwa elementu|Unikatowy klucz|
|------------------|----------------|
|Funkcja (wszystkie atrybuty)|*Atrybut nazwy* (każda nazwa atrybutu, elementu funkcji jest unikatowy klucz).|
|Plik elementu|Lokalizacja|
|ElementManifests/manifest elementu|Lokalizacja|
|Właściwości/właściwości|Key|
|CustomUpgradeAction|Nazwa|
|CustomUpgradeActionParameter|Nazwa|

> [!NOTE]
>  Ponieważ jest jedynym sposobem, aby zmodyfikować CustomUpgradeAction element niestandardowej [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] edytora scalania nie powoduje niski.

## <a name="package-manifest-elements"></a>Elementy manifestu pakietu
 Poniższa tabela jest lista wszystkich elementów manifestu pakietu, które mogą zostać scalone ich Unikatowy klucz, który jest używany do dopasowania.

|Nazwa elementu|Unikatowy klucz|
|------------------|----------------|
|Rozwiązanie (wszystkie atrybuty)|*Atrybut nazwy* (każda nazwa atrybutu, elementu rozwiązania jest unikatowy klucz).|
|ApplicationResourceFiles/ApplicationResourceFile|Lokalizacja|
|Zestawy/zestawu|Lokalizacja|
|ClassResources/ClassResource|Lokalizacja|
|DwpFiles/DwpFile|Lokalizacja|
|FeatureManifests/FeatureManifest|Lokalizacja|
|Zasobów/zasobów|Lokalizacja|
|RootFiles/RootFile|Lokalizacja|
|SiteDefinitionManifests/SiteDefinitionManifest|Lokalizacja|
|WebTempFile|Lokalizacja|
|TemplateFiles/TemplateFile|Lokalizacja|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Ręcznego dodawania plików do wdrożenia
 Niektóre elementy manifestu, takie jak ApplicationResourceFile i DwpFiles, określ lokalizację, która zawiera nazwę pliku. Jednak dodanie wpisu nazwa pliku manifestu szablonu nie dodaje podstawowego pliku do pakietu. Należy dodać plik do projektu, aby uwzględnić go w pakiecie i odpowiednio ustawić jego właściwości typu wdrożenia.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
