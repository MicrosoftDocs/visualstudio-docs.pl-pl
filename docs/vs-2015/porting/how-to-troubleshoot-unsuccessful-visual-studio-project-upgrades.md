---
title: 'Instrukcje: Rozwiązywanie problemów z aktualizacjami projektów zakończonych niepowodzeniem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844447"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Porady: rozwiązywanie problemów z nieudanymi aktualizacjami projektu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami program Visual Studio nie może w pełni skonwertować projektu ze starszej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jeśli porady w poniższych sekcjach nie rozwiązują określonego problemu, może być możliwe znalezienie dodatkowych informacji na stronie TechNet [wiki: Portal dla deweloperów](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt nie działa, ponieważ nie znaleziono plików
 Plik projektu zawiera zakodowane ścieżki plików, które są [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używane do uruchamiania projektu po naciśnięciu klawisza F5. Ścieżki te mogą obejmować lokalizację devenv.exe i innych wymaganych plików. W uaktualnionej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ścieżki tych plików mogły zostać zmienione.

#### <a name="to-resolve-incorrect-file-paths"></a>Aby rozwiązać niepoprawne ścieżki plików

1. Otwórz plik projektu w edytorze tekstu.

2. Skanuj w poszukiwaniu ścieżek plików, które mogą być nieprawidłowe, zwłaszcza tych, które zawierają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] numer wersji.

3. Zmodyfikuj niepoprawne ścieżki plików, aby wskazywały na nowe obiekty docelowe.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt nie kompiluje się, ponieważ odwołania są nieprawidłowe
 Podczas uaktualniania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można również uaktualnić [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersję. Jeśli projekt zawiera odwołania, które są wycofane w nowszej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, mogą one nie zostać poprawnie rozwiązane. Jest to szczególnie przydatne w przypadku odwołań zawierających numery wersji, na przykład `Microsoft.VisualStudio.Shell.Interop.8.0` .

 Jeśli kod zawiera wiele nieprawidłowych odwołań, najprostszym rozwiązaniem może być użycie funkcji wielu elementów docelowych programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w celu uzyskania wcześniejszej wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

#### <a name="to-resolve-incorrect-references"></a>Aby rozwiązać nieprawidłowe odwołania

1. Otwórz plik projektu w edytorze tekstu.

2. Otwórz właściwości projektu.

3. Wybierz poprawną wartość **platformy docelowej** . Alternatywnie można zmodyfikować wartość `<TargetFrameworkVersion>` elementu bezpośrednio w pliku projektu.

   Jeśli chcesz, aby projekt był uruchamiany w uaktualnionej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, musisz zaktualizować odwołania do projektu, a także zaktualizować wszelkie `Imports` `Using` instrukcje, które wywołują odwołania. Jeśli projekt jest ładowany w IDE, można zaktualizować odwołania przy użyciu **Eksplorator rozwiązań** lub okna dialogowego **Menedżer odwołań** .

## <a name="see-also"></a>Zobacz też
 [/Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [konwertowanie na ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
