---
title: 'Porady: Rozwiązywanie problemów z uaktualnieniami niepomyślnych projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6b50bbaaf7e5b018709f3cf0dece3c0ae38410f8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064799"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Porady: rozwiązywanie problemów z nieudanymi aktualizacjami projektu Visual Studio
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
