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
ms.openlocfilehash: bd377318d92989f7e1341d166b2ca3d3978a148d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595244"
---
# <a name="use-multiple-processors-to-build-projects"></a>Używanie wielu procesorów do kompilowania projektów
Program MSBuild potrafi optymalnie wykorzystywać komputery z wieloma procesorami lub procesorami wielordzeniowymi. Dla każdego dostępnego procesora jest tworzony oddzielny proces kompilacji. Jeśli na przykład system ma cztery procesory, powstają cztery procesy kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mogą przetwarzać te kompilacje jednocześnie, a w związku z tym łączny czas kompilacji jest zmniejszany. Jednak kompilowanie równoległe wprowadza pewne zmiany w przebiegu procesów kompilacji. Omówiono je w tym temacie.

## <a name="project-to-project-references"></a>Odwołania projektu do projektu
 Gdy [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] napotka odwołanie projekt-do-Project (P2P), gdy używa kompilacji równoległych do kompilowania projektu, kompiluje tylko jeden raz. Jeśli dwa projekty mają to samo odwołanie P2P, nie będzie ono kompilowane osobno dla każdego projektu. Zamiast tego aparat kompilacji zwraca to samo odwołanie P2P do obu projektów, które go używają. Na przyszłe żądania o ten sam element docelowy w trakcie jednej sesji jest podawane to samo odwołanie P2P.

## <a name="cycle-detection"></a>Wykrywanie cyklu
 Funkcja wykrywania cyklu działa tak samo jak w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0, z tą różnicą, że teraz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może zgłosić wykrycie cyklu w innym czasie lub w kompilacji.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Błędy i wyjątki podczas kompilacji równoległych
 W kompilacjach równoległych błędy i wyjątki mogą się wydarzyć o innym czasie niż podczas kompilacji nierównoległej i gdy jeden projekt nie jest kompilowany, druga kompilacja trwa dalej. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie zatrzyma żadnej kompilacji projektu, która jest tworzona równolegle z tą, która się nie powiodła. Inne projekty kontynuują kompilację do momentu pomyślnego lub niepowodzenia. Jednak jeśli włączono opcję <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, kompilacje nie będą zatrzymywane nawet mimo wystąpienia błędów.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++pliki projektu (. vcxproj) i rozwiązania (. sln)
 Do [zadania programu MSBuild](../msbuild/msbuild-task.md)można przesłać zarówno pliki projektów programu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] ( *. vcxproj*), jak i rozwiązania ( *. sln*). W przypadku projektów [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jest wywoływana VCWrapperProject, a następnie tworzony jest projekt wewnętrzny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. W przypadku rozwiązań [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jest tworzony SolutionWrapperProject, a następnie projekt wewnętrzny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zostanie utworzony. W obu przypadkach powstały projekt jest traktowany tak samo jak każdy inny projekt programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="multi-process-execution"></a>Wykonywanie przez wiele procesów
 Prawie wszystkie czynności dotyczące kompilacji wymagają, aby bieżący katalog pozostał bez zmian przez cały proces kompilacji, ponieważ zapobiega to błędom związanym ze ścieżką. W związku z tym projektów nie można uruchamiać w różnych wątkach programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], ponieważ spowodowałoby to utworzenie wielu katalogów.

 Aby zabiec temu problemowi, ale nadal umożliwiać kompilowanie na wielu procesorach, program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stosuje „izolację procesów”. Za pomocą tego mechanizmu program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może utworzyć maksymalnie `n` procesów, gdzie `n` odpowiada liczbie procesorów dostępnych w komputerze. Jeśli na przykład program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kompiluje rozwiązanie na komputerze, który ma dwa procesory, zostaną utworzone tylko dwa procesy kompilacji. Procesy te są wykonywane wielokrotnie w celu skompilowania wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także
- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Zadania](../msbuild/msbuild-tasks.md)
