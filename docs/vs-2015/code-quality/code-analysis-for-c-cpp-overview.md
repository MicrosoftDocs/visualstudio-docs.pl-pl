---
title: Analiza kodu dla C i C++ — omówienie | Dokumentacja firmy Microsoft
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: fce0fb33f6c536386754b10b11e724a603f0a2a6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698003"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla C/C++ — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie do analizy kodu C/C++ zawiera informacje dla deweloperów o możliwych wady kodu źródłowego języka C/C++. Typowe błędy kodowania zgłoszonej przez narzędzie obejmują przepełnienia buforów i pamięci surowej zainicjowane, wyłuskania wskaźnika o wartości null i przecieków pamięci i zasobów.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja z IDE (zintegrowanym środowiskiem programistycznym)  
 Aby stał się naturalnym deweloperzy mogą korzystać z narzędzia do analizy, jego jest w pełni zintegrowana w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Podczas procesu kompilacji wszelkie ostrzeżenia generowane dla kodu źródłowego są wyświetlane na liście błędów. Możesz przejść do kodu źródłowego, który spowodował ostrzeżenie, a można wyświetlić dodatkowe informacje na temat przyczyny oraz możliwe rozwiązania tego problemu.  
  
## <a name="pragma-support"></a>#pragma pomocy technicznej  
 Deweloperzy mogą używać `#pragma` dyrektywy Traktuj ostrzeżenia jako błędy; Włącz lub wyłącz ostrzeżenia i pomijanie ostrzeżeń dla pojedynczych wierszy kodu. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie analizy kodu dla określonego języka C/C++ — ostrzeżenia](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Obsługa adnotacji  
 Adnotacje poprawić analizy kodu. Adnotacje zawierają dodatkowe informacje o warunkach wstępnych oraz po o parametrów funkcji i zwracanych typów. Aby uzyskać więcej informacji, zobacz [jak: Określanie dodatkowych informacji o kodzie za pomocą funkcji __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom narzędzie do analizy jako część zasad ewidencjonowania  
 Można wymagać, że wszystkie źródła kodu zaewidencjonowania spełniały pewne zasady. W szczególności chcesz upewnić się, że analiza została uruchomiona jako krok najnowszych kompilacji, lokalne. Aby uzyskać więcej informacji na temat włączania zasad analizy kodu ewidencjonowania, zobacz [tworzyć i za pomocą zasad analizy kodu zaewidencjonowania](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integracji kompilacji zespołu  
 Zintegrowane funkcje systemu kompilacji można użyć, aby uruchomić narzędzie do analizy kodu jako krok z [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] procesu kompilacji. Aby uzyskać więcej informacji, zobacz [skompilować aplikację](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Obsługa wiersza polecenia  
 Oprócz pełnej integracji w środowisku deweloperskim deweloperzy można także użyć narzędzia analizy z wiersza polecenia, jak pokazano w poniższym przykładzie:  
  
 `C:\>cl /analyze Sample.cpp`
