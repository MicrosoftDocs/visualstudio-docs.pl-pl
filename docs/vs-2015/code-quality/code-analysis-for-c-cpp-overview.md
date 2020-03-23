---
title: Analiza kodu dla przeglądu C-C++ | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77275358"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla C/C++ — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie Do analizy kodu języka C/C++ zawiera informacje dla deweloperów o możliwych wadach kodu źródłowego języka C/C++. Typowe błędy kodowania zgłaszane przez narzędzie obejmują przekroczenia buforu, nie zainicjowaną pamięć, wyłuskinie wskaźnika null oraz przecieki pamięci i zasobów.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)  
 Aby ułatwić deweloperom korzystanie z narzędzia analitycznego, jest [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ono w pełni zintegrowane z IDE. Podczas procesu kompilacji wszystkie ostrzeżenia wygenerowane dla kodu źródłowego są wyświetlane na liście błędów. Można przejść do kodu źródłowego, który spowodował ostrzeżenie i można wyświetlić dodatkowe informacje o przyczynie i możliwych rozwiązań problemu.  
  
## <a name="pragma-support"></a>Pomoc #pragma  
 Deweloperzy mogą `#pragma` używać dyrektywy do traktowania ostrzeżeń jako błędów; włączyć lub wyłączyć ostrzeżenia i pominąć ostrzeżenia dla poszczególnych wierszy kodu. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie i wyłączanie analizy kodu dla określonych ostrzeżeń C/C++.](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a)  
  
## <a name="annotation-support"></a>Obsługa adnotacji  
 Adnotacje poprawić dokładność analizy kodu. Adnotacje zawierają dodatkowe informacje o warunkach przed- i post-na parametry funkcji i typy zwracane. Aby uzyskać więcej informacji, zobacz [Jak: Określanie dodatkowych informacji o kodzie przy użyciu __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchamianie narzędzia analitycznego w ramach zasad zaewidencjonowania  
 Można wymagać, aby wszystkie zaewidencjonowania kodu źródłowego spełniały określone zasady. W szczególności chcesz upewnić się, że analiza została przeprowadzona jako krok najnowszej kompilacji lokalnej. Aby uzyskać więcej informacji na temat włączania zasad zaewidencjonowania analizy kodu, zobacz [Tworzenie i używanie zasad zaewidencjonowania analizy kodu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integracja budowania zespołu  
 Można użyć zintegrowanych funkcji systemu kompilacji do uruchomienia narzędzia [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] do analizy kodu jako krok procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji](/azure/devops/pipelines/index).  
  
## <a name="command-line-support"></a>Obsługa wiersza polecenia  
 Oprócz pełnej integracji w środowisku programistycznym deweloperzy mogą również używać narzędzia analitycznego z wiersza polecenia, jak pokazano w poniższym przykładzie:  
  
 `C:\>cl /analyze Sample.cpp`
