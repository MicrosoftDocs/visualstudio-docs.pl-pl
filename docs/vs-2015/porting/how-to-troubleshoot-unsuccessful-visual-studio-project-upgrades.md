---
title: 'Porady: Rozwiązywanie problemów z uaktualnieniami niepomyślnych projektu | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 16232a72cd37f8d1d68760f032b6050e0bdf74c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300354"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Porady: rozwiązywanie problemów z nieudanymi aktualizacjami projektu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami program Visual Studio nie może w pełni skonwertować projektu ze starszej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jeśli porady w poniższych sekcjach nie rozwiązują określonego problemu, może być możliwe znalezienie dodatkowych informacji na stronie TechNet [wiki: Portal dla deweloperów](https://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt nie działa, ponieważ pliki nie zostaną znalezione
 Plik projektu zawiera zakodowane ścieżki plików, których [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa do uruchamiania projektu po naciśnięciu klawisza F5. Te ścieżki mogą obejmować lokalizacja devenv.exe i inne wymagane pliki. W uaktualnionej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ścieżki tych plików mogły zostać zmienione.

#### <a name="to-resolve-incorrect-file-paths"></a>Aby rozwiązać niepoprawny plik ścieżki

1. Otwórz plik projektu w edytorze tekstów.

2. Skanuj w poszukiwaniu ścieżek plików, które mogą być nieprawidłowe, zwłaszcza tych, które zawierają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] numer wersji.

3. Tak, aby wskazać nowe obiekty docelowe, należy zmodyfikować ścieżki niepoprawny plik.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt nie kompiluje się, ponieważ odwołania są nieprawidłowe
 W przypadku uaktualniania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]można również uaktualnić wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Jeśli projekt zawiera odwołania, które są wycofane w nowszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], mogą one nie zostać poprawnie rozwiązane. Jest to szczególnie przydatne w przypadku odwołań zawierających numery wersji, na przykład `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Jeśli kod zawiera wiele nieprawidłowych odwołań, najprostszym rozwiązaniem może być użycie funkcji wielowartościowego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby docelowa była wcześniejsza wersja [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Aby rozwiązać niepoprawne odwołania

1. Otwórz plik projektu w edytorze tekstów.

2. Otwórz właściwości projektu.

3. Wybierz poprawną wartość **platformy docelowej** . Alternatywnie można zmodyfikować wartość `<TargetFrameworkVersion>` elementu bezpośrednio w pliku projektu.

   Jeśli chcesz, aby projekt był uruchamiany w uaktualnionej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], musisz zaktualizować odwołania do projektu, a także zaktualizować wszelkie instrukcje `Imports` lub `Using`, które wywołują odwołania. Jeśli projekt jest ładowany w IDE, można zaktualizować odwołania przy użyciu **Eksplorator rozwiązań** lub okna dialogowego **Menedżer odwołań** .

## <a name="see-also"></a>Zobacz też
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [konwertowanie na ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
