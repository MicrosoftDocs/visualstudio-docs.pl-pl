---
title: Analiza kodu dla języka C-C + + — Omówienie | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77275358"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla C/C++ — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie do analizy kodu C/C++ zawiera informacje dla deweloperów o możliwych defektach w kodzie źródłowym języka C/C++. Typowe błędy kodowania zgłoszone przez narzędzie obejmują przepełnienia buforów, niezainicjowaną pamięć, odwołania wskaźnika NULL oraz przecieki pamięci i zasobów.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)  
 Aby ułatwić deweloperom korzystanie z narzędzia do analizy, jest w pełni zintegrowane w środowisku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. W trakcie procesu kompilacji wszystkie ostrzeżenia wygenerowane dla kodu źródłowego pojawiają się w Lista błędów. Możesz przejść do kodu źródłowego, który spowodował ostrzeżenie, i można wyświetlić dodatkowe informacje o przyczynie problemu oraz ewentualnych rozwiązaniach.  
  
## <a name="pragma-support"></a>Obsługa #pragma  
 Deweloperzy mogą używać `#pragma` dyrektywy do traktowania ostrzeżeń jako błędów, włączania lub wyłączania ostrzeżeń oraz pomijania ostrzeżeń dla poszczególnych wierszy kodu. Aby uzyskać więcej informacji, zobacz [How to: Enable and disable Code Analysis dla określonych ostrzeżeń C/C++](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Obsługa adnotacji  
 Adnotacje poprawiają dokładność analizy kodu. Adnotacje zawierają dodatkowe informacje na temat parametrów funkcji i typów zwracanych. Aby uzyskać więcej informacji, zobacz [How to: Określanie dodatkowych informacji o kodzie przy użyciu __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom Narzędzie analizy jako część zasad ewidencjonowania  
 Można wymagać, aby wszystkie operacje ewidencjonowania kodu źródłowego spełniały określone zasady. W szczególności chcesz upewnić się, że analiza została uruchomiona jako krok ostatniej kompilacji lokalnej. Aby uzyskać więcej informacji na temat włączania zasad zaewidencjonowania analizy kodu, zobacz [Tworzenie zasad ewidencjonowania analizy kodu i korzystanie](../code-quality/creating-and-using-code-analysis-check-in-policies.md) z nich  
  
## <a name="team-build-integration"></a>Integracja kompilacji zespołowej  
 Możesz użyć zintegrowanych funkcji systemu kompilacji, aby uruchomić Narzędzie analizy kodu jako krok [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji](/azure/devops/pipelines/index).  
  
## <a name="command-line-support"></a>Obsługa wiersza polecenia  
 Oprócz pełnej integracji w środowisku programistycznym deweloperzy mogą również używać narzędzia do analizy z wiersza polecenia, jak pokazano w następującym przykładzie:  
  
 `C:\>cl /analyze Sample.cpp`
