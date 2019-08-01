---
title: MSBuild. Pliki docelowe | Microsoft Docs
ms.date: 02/24/2017
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bacc58184d0ea78a5e54d7cc7b0b93df107b3300
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681412"
---
# <a name="msbuild-targets-files"></a>MSBuild. targets — pliki
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]zawiera kilka plików *. targets* , które zawierają elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plików projektu, aby uprościć konserwację i czytelność.

 Projekty zwykle importują jeden lub więcej plików *. targets* , aby zdefiniować ich proces kompilacji. Na przykład projekt [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] utworzony przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spowoduje zaimportowanie elementu *Microsoft. CSharp. targets* , który importuje element *Microsoft. Common. targets*. Sam projekt zdefiniuje elementy i właściwości specyficzne dla tego projektu, ale standardowe reguły kompilacji [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dla projektu są zdefiniowane w importowanych plikach *. targets* . [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

 Wartość określa ścieżkę tych wspólnych plików *. targets.* `$(MSBuildToolsPath)` Jeśli wartość `ToolsVersion` to 4,0, pliki znajdują się w następującej lokalizacji: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Aby uzyskać informacje o sposobach tworzenia własnych obiektów docelowych, Zobacz [targets](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobach używania `Import` elementu do wstawiania pliku projektu do innego pliku projektu, zobacz [Importowanie elementu (MSBuild)](../msbuild/import-element-msbuild.md) i [instrukcje: Użyj tego samego elementu docelowego w wielu plikach](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)projektu.

## <a name="common-targets-files"></a>Common. targets — pliki

| plik *. targets* | Opis |
|---------------------------------| - |
| *Microsoft. Common. targets* | Definiuje kroki w standardowym procesie kompilacji dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów i. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]<br /><br /> Zaimportowany przez pliki *Microsoft. CSharp. targets* i *Microsoft. VisualBasic. targets* , które obejmują następujące instrukcje:`<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów wizualnych C# .<br /><br /> Zaimportowane przez C# pliki projektu wizualnego ( *. csproj*), które obejmują następującą instrukcję:`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft. VisualBasic. targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów Visual Basic.<br /><br /> Zaimportowane przez Visual Basic pliki projektu ( *. vbproj*), które obejmują następującą instrukcję:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Katalog. Build. targets
*Katalog. Build. targets* to plik zdefiniowany przez użytkownika, który udostępnia dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft. Common. targets* , chyba że właściwość **ImportDirectoryBuildTargets** ma **wartość false**. Aby uzyskać więcej informacji, [Dostosuj kompilację](customize-your-build.md).

## <a name="see-also"></a>Zobacz także
- [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
