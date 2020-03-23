---
title: Używanie wielu procesorów do tworzenia projektów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631305"
---
# <a name="use-multiple-processors-to-build-projects"></a>Tworzenie projektów za pomocą wielu procesorów

Program MSBuild potrafi optymalnie wykorzystywać komputery z wieloma procesorami lub procesorami wielordzeniowymi. Dla każdego dostępnego procesora jest tworzony oddzielny proces kompilacji. Jeśli na przykład system ma cztery procesory, powstają cztery procesy kompilacji. MSBuild może przetwarzać te kompilacje jednocześnie, a zatem całkowity czas kompilacji jest zmniejszona. Jednak kompilowanie równoległe wprowadza pewne zmiany w przebiegu procesów kompilacji. Omówiono je w tym temacie.

## <a name="project-to-project-references"></a>Odwołania do projektu

 Gdy aparat kompilacji firmy Microsoft napotka odwołanie do projektu do projektu (P2P), podczas gdy używa kompilacji równoległych do tworzenia projektu, tworzy odwołanie tylko jeden raz. Jeśli dwa projekty mają to samo odwołanie P2P, nie będzie ono kompilowane osobno dla każdego projektu. Zamiast tego aparat kompilacji zwraca to samo odwołanie P2P do obu projektów, które go używają. Na przyszłe żądania o ten sam element docelowy w trakcie jednej sesji jest podawane to samo odwołanie P2P.

## <a name="cycle-detection"></a>Wykrywanie cyklu

 Funkcje wykrywania cyklu takie same jak w MSBuild 2.0, z tą różnicą, że teraz MSBuild może zgłosić wykrywanie cyklu w innym czasie lub w kompilacji.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Błędy i wyjątki podczas kompilacji równoległych

 W kompilacjach równoległych błędy i wyjątki mogą się wydarzyć o innym czasie niż podczas kompilacji nierównoległej i gdy jeden projekt nie jest kompilowany, druga kompilacja trwa dalej. MSBuild nie zatrzyma kompilacji projektu, który jest budowany równolegle z tym, który nie powiodło się. Inne projekty nadal budować, dopóki nie powiedzie się lub nie. Jednak jeśli włączono opcję <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, kompilacje nie będą zatrzymywane nawet mimo wystąpienia błędów.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Pliki projektu c++ (.vcxproj) i rozwiązania (.sln)

 Pliki w języku C++ (*.vcxproj)* i solution (*.sln*) mogą być przekazywane do [zadania MSBuild.](../msbuild/msbuild-task.md) Dla projektów Języka C++ wywoływany jest projekt VCWrapperProject, a następnie tworzony jest wewnętrzny projekt MSBuild. Dla rozwiązań Języka C++ solutionWrapperProject jest tworzony, a następnie tworzony jest wewnętrzny projekt MSBuild. W obu przypadkach wynikowy projekt jest traktowany tak samo jak każdy inny projekt MSBuild.

## <a name="multi-process-execution"></a>Wykonywanie wielu procesów

 Prawie wszystkie czynności dotyczące kompilacji wymagają, aby bieżący katalog pozostał bez zmian przez cały proces kompilacji, ponieważ zapobiega to błędom związanym ze ścieżką. W związku z tym projekty nie można uruchomić na różnych wątków w MSBuild, ponieważ mogłyby one spowodować wiele katalogów do utworzenia.

 Aby uniknąć tego problemu, ale nadal włączyć kompilacje wieloprocesorowe, MSBuild używa "izolacji procesu." Za pomocą izolacji procesu, MSBuild `n` można utworzyć `n` maksymalnie procesów, gdzie jest równa liczbie procesorów dostępnych w systemie. Na przykład jeśli MSBuild tworzy rozwiązanie w systemie, który ma dwa procesory, a następnie tylko dwa procesy kompilacji są tworzone. Procesy te są wykonywane wielokrotnie w celu skompilowania wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też

- [Twórz wiele projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Zadania](../msbuild/msbuild-tasks.md)
