---
title: Scalanie kodu XML w manifestach funkcji i pakietów | Microsoft Docs
description: Umożliwia scalanie kodu XML generowanego przez projektanta i dodanego przez użytkownika w funkcjach i manifestach pakietów programu SharePoint. Poznaj funkcje i elementy manifestu pakietu oraz Scalaj wyjątki.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 16305ed63f48d9f14e35aeb8d37e35f23f40be25
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304239"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Scalanie kodu XML w manifestach funkcji i pakietów
  Funkcje i pakiety są definiowane przez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki manifestu. Te spakowane manifesty są kombinacją danych wygenerowanych przez projektantów i niestandardowych [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] wprowadzonych w szablonie manifestu przez użytkowników. W czasie pakowania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scala [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcje niestandardowe z udostępnionym projektantem, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Aby utworzyć spakowany [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] plik manifestu. Podobne elementy, z wyjątkami zanotowanymi w dalszej części wyjątków scalania, są scalane w celu uniknięcia [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] błędów walidacji po wdrożeniu plików w programie SharePoint i zwiększenia wydajności plików manifestu.

## <a name="modify-the-manifests"></a>Modyfikowanie manifestów
 Nie można bezpośrednio modyfikować spakowanych plików manifestu, dopóki nie zostanie wyłączona funkcja lub projektanci pakietu. Można jednak ręcznie dodać [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy niestandardowe do szablonu manifestu za pomocą funkcji i projektantów pakietu albo [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] edytora. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) i [instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Proces scalania manifestu funkcji i pakietów
 Podczas łączenia elementów niestandardowych wraz z elementami udostępnionymi przez projektanta program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa następującego procesu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sprawdza, czy każdy element ma unikatową wartość klucza. Jeśli element nie ma unikatowej wartości klucza, jest dołączany do spakowanego pliku manifestu. Podobnie elementy, które mają wiele kluczy, nie mogą być scalane. W związku z tym są one dołączane do pliku manifestu.

 Jeśli element ma unikatowy klucz, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] porównuje wartości projektanta i kluczy niestandardowych. Jeśli wartości są zgodne, scalane w jedną wartość. Jeśli wartości są różne, wartość klucza projektanta zostanie odrzucona i zostanie użyta wartość klucza niestandardowego. Kolekcje są również scalane. Na przykład jeśli wygenerowane przez projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] i niestandardowe elementy [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zawierają kolekcję zestawów, spakowany manifest zawiera tylko jedną kolekcję zestawów.

## <a name="merge-exceptions"></a>Scalanie wyjątków
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scala większość elementów projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] wraz z podobnymi elementami niestandardowymi, o ile [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] mają jeden unikatowy atrybut identyfikujący. Jednak niektóre elementy nie wymagają unikatowego identyfikatora wymaganego do [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] scalenia. Te elementy są nazywane *wyjątkami scalania*. W takich przypadkach program nie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scala [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów niestandardowych razem z elementami udostępnionymi przez projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , ale zamiast tego dołącza je do spakowanego pliku manifestu.

 Poniżej znajduje się Lista wyjątków scalania dla [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] plików manifestów funkcji i pakietów.

|Projektant|Element XML|
|--------------|-----------------|
|Projektant funkcji|ActivationDependency|
|Projektant funkcji|UpgradeAction|
|Projektant pakietów|SafeControl|
|Projektant pakietów|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementy manifestu funkcji
 Poniższa tabela zawiera listę wszystkich elementów manifestu funkcji, które mogą być scalone i ich unikatowy klucz używany do dopasowywania.

|Nazwa elementu|Klucz unikatowy|
|------------------|----------------|
|Funkcja (wszystkie atrybuty)|*Nazwa atrybutu* (każda nazwa atrybutu elementu funkcji jest unikatowym kluczem).|
|Elementu|Lokalizacja|
|ElementManifests/ElementManifest|Lokalizacja|
|Właściwości/Właściwość|Klucz|
|CustomUpgradeAction|Nazwa|
|CustomUpgradeActionParameter|Nazwa|

> [!NOTE]
> Ponieważ jedynym sposobem modyfikacji elementu CustomUpgradeAction jest w edytorze niestandardowym [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , efekt niescalania jest niski.

## <a name="package-manifest-elements"></a>Elementy manifestu pakietu
 Poniższa tabela zawiera listę wszystkich elementów manifestu pakietu, które mogą zostać scalone i ich unikatowy klucz, który jest używany do dopasowywania.

|Nazwa elementu|Klucz unikatowy|
|------------------|----------------|
|Rozwiązanie (wszystkie atrybuty)|*Nazwa atrybutu* (Nazwa każdego atrybutu elementu rozwiązania jest unikatowym kluczem).|
|ApplicationResourceFiles/ApplicationResourceFile|Lokalizacja|
|Zestawy/zestaw|Lokalizacja|
|ClassResources/ClassResource|Lokalizacja|
|DwpFiles/DwpFile|Lokalizacja|
|FeatureManifests/FeatureManifest|Lokalizacja|
|Zasoby/zasób|Lokalizacja|
|RootFiles/RootFile|Lokalizacja|
|SiteDefinitionManifests/SiteDefinitionManifest|Lokalizacja|
|WebTempFile|Lokalizacja|
|TemplateFiles/TemplateFile|Lokalizacja|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Ręczne dodawanie wdrożonych plików
 Niektóre elementy manifestu, takie jak ApplicationResourceFile i DwpFiles, określają lokalizację, która zawiera nazwę pliku. Jednak dodanie wpisu nazwy pliku do szablonu manifestu nie powoduje dodania pliku bazowego do pakietu. Należy dodać plik do projektu, aby uwzględnić go w pakiecie i ustawić odpowiednio jego właściwość typu wdrożenia.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
