---
title: Używanie wielu procesorów do kompilowania projektów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631305"
---
# <a name="use-multiple-processors-to-build-projects"></a>Używanie wielu procesorów do kompilowania projektów

Program MSBuild potrafi optymalnie wykorzystywać komputery z wieloma procesorami lub procesorami wielordzeniowymi. Dla każdego dostępnego procesora jest tworzony oddzielny proces kompilacji. Jeśli na przykład system ma cztery procesory, powstają cztery procesy kompilacji. Program MSBuild może przetwarzać te kompilacje jednocześnie, a w związku z tym łączny czas kompilacji jest zmniejszany. Jednak kompilowanie równoległe wprowadza pewne zmiany w przebiegu procesów kompilacji. Omówiono je w tym temacie.

## <a name="project-to-project-references"></a>Odwołania projektu do projektu

 Gdy Microsoft Build Engine napotka odwołanie projekt-do-Project (P2P), gdy używa kompilacji równoległych do kompilowania projektu, kompiluje tylko jeden raz. Jeśli dwa projekty mają to samo odwołanie P2P, nie będzie ono kompilowane osobno dla każdego projektu. Zamiast tego aparat kompilacji zwraca to samo odwołanie P2P do obu projektów, które go używają. Na przyszłe żądania o ten sam element docelowy w trakcie jednej sesji jest podawane to samo odwołanie P2P.

## <a name="cycle-detection"></a>Wykrywanie cyklu

 Funkcja wykrywania cyklu działa tak samo, jak w programie MSBuild 2,0, z tą różnicą, że teraz program MSBuild może zgłosić wykrycie cyklu w innym czasie lub w kompilacji.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Błędy i wyjątki podczas kompilacji równoległych

 W kompilacjach równoległych błędy i wyjątki mogą się wydarzyć o innym czasie niż podczas kompilacji nierównoległej i gdy jeden projekt nie jest kompilowany, druga kompilacja trwa dalej. Program MSBuild nie zatrzyma żadnej kompilacji projektu, która jest tworzona równolegle z tą, która się nie powiodła. Inne projekty kontynuują kompilację do momentu pomyślnego lub niepowodzenia. Jednak jeśli włączono opcję <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, kompilacje nie będą zatrzymywane nawet mimo wystąpienia błędów.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Pliki projektu C++ (. vcxproj) i rozwiązania (. sln)

 Do [zadania programu MSBuild](../msbuild/msbuild-task.md)można przesłać zarówno pliki projektów C++ (*. vcxproj*), jak i rozwiązania (*. sln*). W przypadku projektów C++ wywoływana jest VCWrapperProject, a następnie tworzony jest wewnętrzny projekt MSBuild. W przypadku rozwiązań C++ tworzony jest SolutionWrapperProject, a następnie tworzony jest wewnętrzny projekt MSBuild. W obu przypadkach projekt, który jest traktowany, jest traktowane tak samo jak każdy inny projekt MSBuild.

## <a name="multi-process-execution"></a>Wykonywanie przez wiele procesów

 Prawie wszystkie czynności dotyczące kompilacji wymagają, aby bieżący katalog pozostał bez zmian przez cały proces kompilacji, ponieważ zapobiega to błędom związanym ze ścieżką. W związku z tym projekty nie mogą być uruchamiane w różnych wątkach programu MSBuild, ponieważ spowodują utworzenie wielu katalogów.

 Aby uniknąć tego problemu, ale nadal Włącz kompilacje wieloprocesorowe, MSBuild używa "izolacji procesów". Korzystając z izolacji procesów, program MSBuild może utworzyć maksymalnie `n` procesy, gdzie `n` jest równa liczbie procesorów dostępnych w systemie. Na przykład, jeśli MSBuild kompiluje rozwiązanie w systemie, który ma dwa procesory, tworzone są tylko dwa procesy kompilacji. Procesy te są wykonywane wielokrotnie w celu skompilowania wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też

- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Zadania](../msbuild/msbuild-tasks.md)
