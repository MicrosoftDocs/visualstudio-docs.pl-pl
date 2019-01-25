---
title: 'Instrukcje: Rozwiązywanie problemów z uaktualnieniami niepomyślnych projektu | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 7d5c30c9b61707f9ac4a32d49613b46416a8d881
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804266"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Instrukcje: Rozwiązywanie problemów z uaktualnieniami projektu powiodło się programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami program Visual Studio w pełni nie można przekonwertować projekt z wcześniejszej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jeśli porady w poniższych sekcjach umożliwiają rozwiązania określonego problemu, można znaleźć więcej informacji na temat TechNet [witryny typu Wiki: Portal programowania](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Projekt nie działa, ponieważ pliki nie zostaną znalezione
 Plik projektu zawiera ścieżki do plików ustalonych, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa, aby uruchomić projekt, po naciśnięciu klawisza F5. Te ścieżki mogą obejmować lokalizacja devenv.exe i inne wymagane pliki. W uaktualnionej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ścieżki te pliki zostały zmienione.

#### <a name="to-resolve-incorrect-file-paths"></a>Aby rozwiązać niepoprawny plik ścieżki

1.  Otwórz plik projektu w edytorze tekstów.

2.  Skanuj w poszukiwaniu ścieżki plików, które mogą być niepoprawne, zwłaszcza tych, które zawierają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] numer wersji.

3.  Tak, aby wskazać nowe obiekty docelowe, należy zmodyfikować ścieżki niepoprawny plik.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Projekt nie kompiluje się, ponieważ odwołania są nieprawidłowe
 Po uaktualnieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], może również być uaktualniania [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji. Jeśli projekt zawiera odwołania, które są anulowane w nowszego [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, ich mogą nie być rozpoznawane poprawnie. Jest to bardzo prawdopodobne, odwołań, które zawierają numery wersji, na przykład `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Jeśli kod ma wiele nieprawidłowe odwołania, najprostszym rozwiązaniu może być funkcja wielowersyjności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pod kątem starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Aby rozwiązać niepoprawne odwołania

1. Otwórz plik projektu w edytorze tekstów.

2. Otwórz właściwości projektu.

3. Wybierz poprawnego **platformę docelową** wartość. Alternatywnie, można zmodyfikować wartości `<TargetFrameworkVersion>` elementu bezpośrednio w pliku projektu.

   Jeśli chcesz, aby projekt do uruchamiania w uaktualnionego [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji, należy zaktualizować odwołania do projektu, a także aktualizacji `Imports` lub `Using` instrukcji, które wywołują odwołania. Jeśli projekt ładuje się w środowisku IDE, można zaktualizować odwołania przy użyciu **Eksploratora rozwiązań** lub **Menadżer odwołań** okno dialogowe.

## <a name="see-also"></a>Zobacz też
 [/ Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [konwertowanie na platformie ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
