---
title: Używanie MSBuild.exe do kompilowania określonych obiektów docelowych w rozwiązaniach
description: Dowiedz się, jak używać wiersza polecenia MSBuild.exe, aby tworzyć konkretne cele konkretnych projektów w rozwiązaniach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fcd9e1ed16b86caf65b9c7fab44ba4f93b7a7a
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572905"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Instrukcje: kompilowanie określonych obiektów docelowych w rozwiązaniach za pomocą MSBuild.exe

Za pomocą *MSBuild.exe* można tworzyć określone cele konkretnych projektów w rozwiązaniu.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby utworzyć konkretny obiekt docelowy określonego projektu w rozwiązaniu

1. W wierszu polecenia wpisz `MSBuild.exe <SolutionName>.sln` , gdzie `<SolutionName>` odpowiada nazwie pliku rozwiązania zawierającego obiekt docelowy, który chcesz wykonać.

2. Określ element docelowy po `-target:` przełączniku w formacie \<ProjectName> : \<TargetName> . Jeśli nazwa projektu zawiera dowolne znaki,,,,,,, `%` `$` `@` `;` `.` `(` `)` lub `'` , zastąp je znakiem `_` w określonej nazwie docelowej.

## <a name="example"></a>Przykład

 W poniższym przykładzie wykonywana jest wartość `Rebuild` docelowa `NotInSlnFolder` projektu, a następnie wykonywana `Clean` jest wartość docelowa `InSolutionFolder` projektu, który znajduje się w folderze rozwiązania *nowyfolder* .

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby zapoznać się z opcjami dostępnymi dla Ciebie, można to zrobić za pomocą opcji debugowania dostarczonej przez program MSBuild. Ustaw zmienną środowiskową `MSBUILDEMITSOLUTION=1` i skompiluj rozwiązanie. Spowoduje to utworzenie pliku programu MSBuild o nazwie *\<SolutionName> . sln. DBPROJ* , który pokazuje wewnętrzny widok programu MSBuild w czasie kompilacji. Możesz sprawdzić ten widok, aby określić, jakie cele są dostępne do skompilowania.

Nie Kompiluj z tym zestawem zmiennych środowiskowych, chyba że potrzebny jest ten widok wewnętrzny. To ustawienie może spowodować problemy podczas kompilowania projektów w rozwiązaniu. Zamiast tego Sprawdź w [dzienniku binarnym](obtaining-build-logs-with-msbuild.md#save-a-binary-log) .

## <a name="see-also"></a>Zobacz też

- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
