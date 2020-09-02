---
title: MSBuild. Pliki docelowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811139"
---
# <a name="msbuild-targets-files"></a>MSBuild — Pliki .Targets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera kilka plików. targets, które zawierają elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plików projektu, aby uprościć konserwację i czytelność.  
  
 Projekty zwykle importują jeden lub więcej plików. targets, aby zdefiniować ich proces kompilacji. Na przykład [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt utworzony przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spowoduje zaimportowanie elementu Microsoft. CSharp. targets, który importuje element Microsoft. Common. targets. [!INCLUDE[csprcs](../includes/csprcs-md.md)]Sam projekt zdefiniuje elementy i właściwości specyficzne dla tego projektu, ale standardowe reguły kompilacji dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektu są zdefiniowane w importowanych plikach. targets.  
  
 `$(MSBuildToolsPath)`Wartość określa ścieżkę tych wspólnych plików. targets. Jeśli wartość `ToolsVersion` to 4,0, pliki znajdują się w następującej lokalizacji: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Aby uzyskać informacje o sposobach tworzenia własnych obiektów docelowych, zobacz [targets](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobach używania `Import` elementu do wstawiania pliku projektu do innego pliku projektu, zobacz [Importowanie elementu (MSBuild)](../msbuild/import-element-msbuild.md) i [instrukcje: Użyj tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Wspólna. Pliki docelowe  
  
|. Plik docelowy|Opis|  
|-------------------|-----------------|  
|Microsoft. Common. targets|Definiuje kroki w standardowym procesie kompilacji dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów i [!INCLUDE[csprcs](../includes/csprcs-md.md)] .<br /><br /> Zaimportowany przez pliki Microsoft. CSharp. targets i Microsoft. VisualBasic. targets, które obejmują następujące instrukcje: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft. CSharp. targets|Definiuje kroki w standardowym procesie kompilacji dla projektów Visual C#.<br /><br /> Zaimportowane przez pliki projektu Visual C# (. csproj), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft. VisualBasic. targets|Definiuje kroki w standardowym procesie kompilacji dla projektów Visual Basic.<br /><br /> Zaimportowane przez Visual Basic pliki projektu (. vbproj), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Zobacz też  
 [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
