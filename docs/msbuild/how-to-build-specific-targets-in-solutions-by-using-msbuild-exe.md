---
title: Użyj MSBuild.exe, aby kompilacja określonych obiektów docelowych w rozwiązaniach
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34c04d12ccc17424a2f938c04751d4e3d4c9f05f
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263789"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Instrukcje: Kompilacja określonych obiektów docelowych, w przypadku rozwiązań przy użyciu MSBuild.exe
Możesz użyć *MSBuild.exe* do kompilacja określonych obiektów docelowych określonych projektów w rozwiązaniu.

#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Tworzenie konkretnego celu określonego projektu w rozwiązaniu

1. W wierszu polecenia wpisz polecenie `MSBuild.exe <SolutionName>.sln`, gdzie `<SolutionName>` odnosi się do nazwy pliku rozwiązania, który zawiera element docelowy, który chcesz wykonać.

2. Określ element docelowy po `-target:` przełącznika w formacie \<nazwa_projektu >:\<TargetName >. Jeśli nazwa projektu zawiera którykolwiek ze znaków `%`, `$`, `@`, `;`, `.`, `(`, `)`, lub `'`, zastąp je za pomocą `_` w określonym Nazwa docelowego.

## <a name="example"></a>Przykład
 Poniższy przykład wykonuje `Rebuild` celem `NotInSlnFolder` projektu, a następnie wykonuje `Clean` celem `InSolutionFolder` projektu, który znajduje się w *Nowyfolder* folderu rozwiązania.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli chcesz sprawdzić dostępne opcje, można użyć opcji debugowania, dostarczane przez program MSBuild, aby to zrobić. Ustaw zmienną środowiskową `MSBUILDEMITSOLUTION=1` i Skompiluj rozwiązanie. Dzięki temu można osiągnąć plik MSBuild o nazwie  *\<SolutionName >. sln.metaproj* pokazujący wewnętrzny widok rozwiązania firmy MSBuild podczas kompilacji. Można sprawdzić ten widok, aby ustalić, jakie obiekty docelowe są dostępne dla kompilacji.

Nie są kompilowane przy użyciu tej zmiennej środowiskowej, ustawić, chyba że potrzebne w tym widoku wewnętrznego. To ustawienie może spowodować problemy kompilowanie projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także
- [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
