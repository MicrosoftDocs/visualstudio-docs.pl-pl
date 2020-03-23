---
title: MSBuild .targets Pliki | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633359"
---
# <a name="msbuild-targets-files"></a>Pliki MSBuild .targets

MSBuild zawiera kilka plików *.targets,* które zawierają elementy, właściwości, obiekty docelowe i zadania dla typowych scenariuszy. Pliki te są automatycznie importowane do większości plików projektu programu Visual Studio, aby uprościć konserwację i czytelność.

 Projekty zazwyczaj importują jeden lub więcej plików *obiektów .targets w* celu zdefiniowania procesu kompilacji. Na przykład projekt języka C# utworzony przez program Visual Studio zaimportuje *plik Microsoft.CSharp.targets,* który importuje *witrynę Microsoft.Common.targets.* Sam projekt języka C# zdefiniuje elementy i właściwości specyficzne dla tego projektu, ale standardowe reguły kompilacji dla projektu Języka C# są zdefiniowane w zaimportowanych plikach *.targets.*

 Wartość `$(MSBuildToolsPath)` określa ścieżkę tych typowych plików *.targets.* Jeśli `ToolsVersion` jest 4.0, pliki znajdują się w następującej lokalizacji: * \<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\ *

> [!NOTE]
> Aby uzyskać informacje na temat tworzenia własnych celów, zobacz [Cele](../msbuild/msbuild-targets.md). Aby uzyskać informacje dotyczące `Import` sposobu używania tego elementu do wstawiania pliku projektu do innego pliku projektu, zobacz [Importuj element (MSBuild)](../msbuild/import-element-msbuild.md) i [Jak: Użyj tego samego obiektu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Typowe pliki .targets

| *.targets* plik | Opis |
|---------------------------------| - |
| *Microsoft.common.targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów języka Visual Basic i C#.<br /><br /> Importowane przez *pliki Microsoft.CSharp.targets* i *Microsoft.VisualBasic.targets,* które zawierają następującą instrukcję:`<Import Project="Microsoft.Common.targets" />` |
| *Obiekty docelowe firmy Microsoft.CSharp.targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów visual c#.<br /><br /> Importowane przez pliki projektu Visual C# (*.csproj*), które zawierają następującą instrukcję:`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Witryna Microsoft.VisualBasic.targets* | Definiuje kroki w standardowym procesie kompilacji dla projektów języka Visual Basic.<br /><br /> Importowane przez pliki projektu języka Visual Basic (*.vbproj*), które zawierają następującą instrukcję:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* to plik zdefiniowany przez użytkownika, który zapewnia dostosowania projektów w katalogu. Ten plik jest automatycznie importowany z *witryny Microsoft.Common.targets,* chyba że właściwość **ImportDirectoryBuildTargets** jest **ustawiona**na false . Aby uzyskać więcej informacji, [dostosuj kompilację](customize-your-build.md).

## <a name="see-also"></a>Zobacz też

- [Importuj element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
