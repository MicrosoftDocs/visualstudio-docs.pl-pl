---
title: MSBuild. targets — pliki | Microsoft Docs
description: Dowiedz się więcej na temat plików MSBuild. targets zawierających elementy, właściwości, cele i zadania dla typowych scenariuszy.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee685fc3deada1a3ac36082fa916b50986900f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971248"
---
# <a name="msbuild-targets-files"></a>MSBuild — pliki targets

Program MSBuild zawiera kilka plików *. targets* , które zawierają elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości plików projektu programu Visual Studio, aby uprościć konserwację i czytelność.

 Projekty zwykle importują jeden lub więcej plików *. targets* , aby zdefiniować ich proces kompilacji. Na przykład projekt C# utworzony przez program Visual Studio spowoduje zaimportowanie *Microsoft. CSharp. targets* , które importuje *Microsoft. Common. targets*. Projekt C# określi elementy i właściwości specyficzne dla tego projektu, ale standardowe reguły kompilacji dla projektu C# są zdefiniowane w zaimportowanych plikach *. targets* .

 `$(MSBuildToolsPath)`Wartość określa ścieżkę tych wspólnych plików *. targets* . Jeśli wartość `ToolsVersion` to 4,0, pliki znajdują się w następującej lokalizacji: *\<WindowsInstallationPath> \Microsoft.NET\Framework\v4.0.30319 \\*

> [!NOTE]
> Aby uzyskać informacje o sposobach tworzenia własnych obiektów docelowych, zobacz [targets](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobach używania `Import` elementu do wstawiania pliku projektu do innego pliku projektu, zobacz [Importowanie elementu (MSBuild)](../msbuild/import-element-msbuild.md) i [instrukcje: Użyj tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Common. targets — pliki

| plik *. targets* | Opis |
|---------------------------------| - |
| *Microsoft. Common. targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów Visual Basic i C#.<br /><br /> Zaimportowany przez pliki *Microsoft. CSharp. targets* i *Microsoft. VisualBasic. targets* , które obejmują następujące instrukcje: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft. CSharp. targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów Visual C#.<br /><br /> Zaimportowane przez pliki projektu Visual C# (*. csproj*), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft. VisualBasic. targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów Visual Basic.<br /><br /> Zaimportowane przez Visual Basic pliki projektu (*. vbproj*), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Katalog. Build. targets

*Katalog. Build. targets* to plik zdefiniowany przez użytkownika, który udostępnia dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft. Common. targets* , chyba że właściwość **ImportDirectoryBuildTargets** ma **wartość false**. Aby uzyskać więcej informacji, [Dostosuj kompilację](customize-your-build.md).

## <a name="see-also"></a>Zobacz też

- [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
