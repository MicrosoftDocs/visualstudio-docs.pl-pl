---
title: Korzystanie z usługi MSBuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704290"
---
# <a name="using-msbuild"></a>Korzystanie z programu MSBuild
MSBuild dostarcza dobrze zdefiniowany, rozszerzalny format XML do tworzenia plików projektu, które w pełni opisują elementy projektu, które mają zostać zbudowane, tworzenie zadań i tworzenie konfiguracji.

## <a name="general-msbuild-considerations"></a>Ogólne zagadnienia dotyczące budowania budynków
 Pliki projektu MSBuild, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] na przykład pliki [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] csproj i .vbproj, zawierają dane, które są używane w czasie kompilacji, ale mogą również zawierać dane używane w czasie projektowania. Dane w czasie kompilacji są przechowywane przy użyciu elementów pierwotnych MSBuild, w tym [elementu elementu (MSBuild)](../../msbuild/item-element-msbuild.md) i [elementu właściwości (MSBuild).](../../msbuild/property-element-msbuild.md) Dane w czasie projektowania, które są danymi specyficznymi dla typu projektu i wszelkich powiązanych podtypów projektu, są przechowywane w dowolnym formacie XML zarezerwowanym dla niego.

 MSBuild nie ma natywnej obsługi obiektów konfiguracji, ale udostępnia atrybuty warunkowe do określania danych specyficznych dla konfiguracji. Przykład:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Aby uzyskać więcej informacji na temat atrybutów [warunkowych, zobacz Konstrukcje warunkowe](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Rozszerzanie budynku MSBuild dla typu projektu
 Interfejsy MSBuild i interfejsy API mogą ulec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zmianie w przyszłych wersjach programu . W związku z tym zaleca się użycie klas struktury pakietu zarządzanego (MPF), ponieważ zapewniają one ochronę przed zmianami.

 Struktura pakietu zarządzanego dla projektów (MPFProj) zapewnia klasy pomocnicze do tworzenia i zarządzania nowym systemem projektów. Kod źródłowy i instrukcje kompilacji można znaleźć w [mpf dla projektów — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Klasy MPF specyficzne dla projektu są następujące:

|Klasa|Wdrażanie|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`klasa jest otoką dla elementów MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatory pojedynczych plików a zadania MSBuild
 Generatory pojedynczych plików są dostępne tylko w czasie projektowania, ale zadania MSBuild mogą być używane w czasie projektowania i kompilacji. Aby uzyskać maksymalną elastyczność, w związku z tym użyj msbuild zadań do przekształcania i generowania kodu. Aby uzyskać więcej informacji, zobacz [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Zobacz też
- [Odwołanie do narzędzia MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md)
