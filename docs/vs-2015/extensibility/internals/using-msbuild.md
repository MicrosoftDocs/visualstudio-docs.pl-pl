---
title: Korzystanie z programu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297671"
---
# <a name="using-msbuild"></a>Korzystanie z programu MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program MSBuild udostępnia dobrze zdefiniowany, rozszerzalny format XML służący do tworzenia plików projektu, które w pełni opisują elementy projektu do skompilowania, tworzenia zadań i konfiguracji kompilacji.  
  
 Aby zapoznać się z kompleksowym przykładem systemu projektu języka opartego na narzędziu MSBuild, zobacz IronPython przykład głębokie szczegółowe w[próbkach VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Ogólne zagadnienia dotyczące programu MSBuild  
 Pliki projektów programu MSBuild, na przykład [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. csproj i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. vbproj, zawierają dane, które są używane w czasie kompilacji, ale również mogą zawierać dane, które są używane w czasie projektowania. Dane czasu kompilacji są przechowywane przy użyciu prymitywów MSBuild, w tym [elementu Item (MSBuild)](../../msbuild/item-element-msbuild.md) i [elementu Property (MSBuild)](../../msbuild/property-element-msbuild.md). Dane czasu projektowania, czyli dane specyficzne dla typu projektu i wszystkie powiązane podtypy projektu, są przechowywane w postaci kodu XML, który jest zarezerwowany.  
  
 Program MSBuild nie ma natywnej obsługi obiektów konfiguracji, ale udostępnia atrybuty warunkowe do określania danych specyficznych dla konfiguracji. Na przykład:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Aby uzyskać więcej informacji na temat atrybutów warunkowych, zobacz [konstrukcje warunkowe](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Rozszerzanie programu MSBuild dla typu projektu  
 Interfejsy programu MSBuild i interfejsy API mogą ulec zmianie w przyszłych wersjach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. W związku z tym należy ostrożnie używać klas struktury zarządzanego pakietu (MPF), ponieważ zapewniają osłonę przed zmianami.  
  
 Struktura pakietów zarządzanych dla projektów (MPFProj) zapewnia klasy pomocników do tworzenia nowego systemu projektu i zarządzania nim. Kod źródłowy i instrukcje kompilacji można znaleźć pod adresem [MPF for projects — Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Klasy MPF specyficzne dla projektu są następujące:  
  
|Klasa|Implementacja|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 Klasa `Microsoft.VisualStudio.Package.ProjectElement` jest otoką dla elementów MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generatory pojedynczych plików a zadania programu MSBuild  
 Generatory pojedynczych plików są dostępne tylko w czasie projektowania, ale zadania programu MSBuild mogą być używane w czasie projektowania i w czasie kompilacji. Aby zapewnić maksymalną elastyczność, należy użyć zadań programu MSBuild do przekształcania i generowania kodu. Aby uzyskać więcej informacji, zobacz [narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje referencyjne programu MSBuild](../../msbuild/msbuild-reference.md)   
   [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)  
 [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md)
