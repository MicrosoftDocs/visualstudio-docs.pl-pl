---
title: Używanie wielu procesorów w projektach kompilacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1732343d160b5c80363999830a41cdb66618b45c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933404"
---
# <a name="use-multiple-processors-to-build-projects"></a>Użycie wielu procesorów w projektach kompilacji
Program MSBuild potrafi optymalnie wykorzystywać komputery z wieloma procesorami lub procesorami wielordzeniowymi. Dla każdego dostępnego procesora jest tworzony oddzielny proces kompilacji. Jeśli na przykład system ma cztery procesory, powstają cztery procesy kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może przetwarzać te kompilacje równocześnie, a w związku z tym, całkowity czas kompilacji jest krótszy. Jednak kompilowanie równoległe wprowadza pewne zmiany w przebiegu procesów kompilacji. Omówiono je w tym temacie.  
  
## <a name="project-to-project-references"></a>Odwołania projektu do projektu  
 Gdy [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] napotka odwołanie projektu do projektu (P2P) podczas równoległego kompilacji, aby skompilować projekt, tworzy on odwołanie tylko jeden raz. Jeśli dwa projekty mają to samo odwołanie P2P, nie będzie ono kompilowane osobno dla każdego projektu. Zamiast tego aparat kompilacji zwraca to samo odwołanie P2P do obu projektów, które go używają. Na przyszłe żądania o ten sam element docelowy w trakcie jednej sesji jest podawane to samo odwołanie P2P.  
  
## <a name="cycle-detection"></a>Wykrywanie cyklu  
 Wykrywanie cyklu działa tak samo jak w programie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, poza tym, że teraz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może zgłaszać wykrycie cyklu w innym czasie lub podczas kompilacji.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Błędy i wyjątki podczas kompilacji równoległych  
 W kompilacjach równoległych błędy i wyjątki mogą się wydarzyć o innym czasie niż podczas kompilacji nierównoległej i gdy jeden projekt nie jest kompilowany, druga kompilacja trwa dalej. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie powoduje wstrzymania każda kompilacja projektu, który tworzy równolegle z jednego, który uległ awarii. Inne projekty w dalszym ciągu kompilacji, aż się zakończą sukcesem lub niepowodzeniem. Jednak jeśli włączono opcję <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, kompilacje nie będą zatrzymywane nawet mimo wystąpienia błędów.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Projekt Visual C++ (.vcproj) i pliki rozwiązania (.sln)  
 Zarówno [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów (*.vcproj*) i rozwiązanie (*.sln*) pliki mogą być przekazywane do [zadanie MSBuild](../msbuild/msbuild-task.md). Dla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów jest wywoływany obiekt VCWrapperProject, a następnie wewnętrzny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zostanie utworzony. Dla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] rozwiązania, zostanie utworzony SolutionWrapperProject, a następnie wewnętrzny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zostanie utworzony. W obu przypadkach powstały projekt jest traktowany tak samo jak każdy inny projekt programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="multi-process-execution"></a>Wykonanie etapu wieloprocesowego  
 Prawie wszystkie czynności dotyczące kompilacji wymagają, aby bieżący katalog pozostał bez zmian przez cały proces kompilacji, ponieważ zapobiega to błędom związanym ze ścieżką. W związku z tym projektów nie można uruchamiać w różnych wątkach programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], ponieważ spowodowałoby to utworzenie wielu katalogów.  
  
 Aby zabiec temu problemowi, ale nadal umożliwiać kompilowanie na wielu procesorach, program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stosuje „izolację procesów”. Za pomocą tego mechanizmu program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może utworzyć maksymalnie `n` procesów, gdzie `n` odpowiada liczbie procesorów dostępnych w komputerze. Jeśli na przykład program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kompiluje rozwiązanie na komputerze, który ma dwa procesory, zostaną utworzone tylko dwa procesy kompilacji. Procesy te są wykonywane wielokrotnie w celu skompilowania wszystkich projektów w rozwiązaniu.  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie wielu projektów wykonywane równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Zadania](../msbuild/msbuild-tasks.md)