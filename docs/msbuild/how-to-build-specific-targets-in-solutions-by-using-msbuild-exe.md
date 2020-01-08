---
title: Tworzenie określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild. exe
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
ms.openlocfilehash: 921b5d2d4aad7cfe48b7f6cc9cb802fde9520e19
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585261"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Instrukcje: kompilowanie określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild. exe
Programu *MSBuild. exe* można użyć do tworzenia określonych elementów docelowych określonych projektów w rozwiązaniu.

#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby utworzyć konkretny obiekt docelowy określonego projektu w rozwiązaniu

1. W wierszu polecenia wpisz `MSBuild.exe <SolutionName>.sln`, gdzie `<SolutionName>` odpowiada nazwie pliku rozwiązania, które zawiera obiekt docelowy, który chcesz wykonać.

2. Określ element docelowy po przełączniku `-target:` w formacie \<ProjectName >:\<TargetName >. Jeśli nazwa projektu zawiera dowolny ze znaków `%`, `$`, `@`, `;`, `.`, `(`, `)`lub `'`, Zamień je na `_` w określonej nazwie docelowej.

## <a name="example"></a>Przykład
 Poniższy przykład wykonuje `Rebuild` cel projektu `NotInSlnFolder`, a następnie wykonuje `Clean` cel projektu `InSolutionFolder`, który znajduje się w folderze rozwiązania *nowyfolder* .

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby zapoznać się z opcjami dostępnymi dla Ciebie, można to zrobić za pomocą opcji debugowania dostarczonej przez program MSBuild. Ustaw zmienną środowiskową `MSBUILDEMITSOLUTION=1` i skompiluj rozwiązanie. Spowoduje to utworzenie pliku programu MSBuild o nazwie *\<solutionname >. sln. DBPROJ* , który pokazuje wewnętrzny widok programu MSBuild w czasie kompilacji. Możesz sprawdzić ten widok, aby określić, jakie cele są dostępne do skompilowania.

Nie Kompiluj z tym zestawem zmiennych środowiskowych, chyba że potrzebny jest ten widok wewnętrzny. To ustawienie może spowodować problemy podczas kompilowania projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także
- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
