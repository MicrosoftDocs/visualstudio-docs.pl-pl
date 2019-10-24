---
title: Korzystanie z programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c199df38f2cd51307861462af49f58996fe84fe4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722167"
---
# <a name="using-msbuild"></a>Korzystanie z programu MSBuild
Program MSBuild udostępnia dobrze zdefiniowany, rozszerzalny format XML służący do tworzenia plików projektu, które w pełni opisują elementy projektu do skompilowania, tworzenia zadań i konfiguracji kompilacji.

## <a name="general-msbuild-considerations"></a>Ogólne zagadnienia dotyczące programu MSBuild
 Pliki projektów programu MSBuild, na przykład [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. csproj i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. vbproj, zawierają dane, które są używane w czasie kompilacji, ale również mogą zawierać dane, które są używane w czasie projektowania. Dane czasu kompilacji są przechowywane przy użyciu prymitywów MSBuild, w tym [elementu Item (MSBuild)](../../msbuild/item-element-msbuild.md) i [elementu Property (MSBuild)](../../msbuild/property-element-msbuild.md). Dane czasu projektowania, czyli dane specyficzne dla typu projektu i wszystkie powiązane podtypy projektu, są przechowywane w postaci kodu XML, który jest zarezerwowany.

 Program MSBuild nie ma natywnej obsługi obiektów konfiguracji, ale udostępnia atrybuty warunkowe do określania danych specyficznych dla konfiguracji. Na przykład:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Aby uzyskać więcej informacji na temat atrybutów warunkowych, zobacz [konstrukcje warunkowe](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Rozszerzanie programu MSBuild dla typu projektu
 Interfejsy programu MSBuild i interfejsy API mogą ulec zmianie w przyszłych wersjach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W związku z tym należy ostrożnie używać klas struktury zarządzanego pakietu (MPF), ponieważ zapewniają osłonę przed zmianami.

 Struktura pakietów zarządzanych dla projektów (MPFProj) zapewnia klasy pomocników do tworzenia nowego systemu projektu i zarządzania nim. Kod źródłowy i instrukcje kompilacji można znaleźć pod adresem [MPF for projects — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Klasy MPF specyficzne dla projektu są następujące:

|Class|Implementacja|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 Klasa `Microsoft.VisualStudio.Package.ProjectElement` jest otoką dla elementów MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatory pojedynczych plików a zadania programu MSBuild
 Generatory pojedynczych plików są dostępne tylko w czasie projektowania, ale zadania programu MSBuild mogą być używane w czasie projektowania i w czasie kompilacji. Aby zapewnić maksymalną elastyczność, należy użyć zadań programu MSBuild do przekształcania i generowania kodu. Aby uzyskać więcej informacji, zobacz [narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Zobacz także
- [Odwołanie do narzędzia MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md)