---
title: Analiza kodu dla C/C++ — Omówienie
ms.date: 04/28/2018
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 07ba2c64be0af987b82c870b89d3451b5d48d28f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947643"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu C/C++ — Przegląd

Narzędzie do analizy kodu C/C++ zawiera informacje dotyczące możliwych usterek w kodzie źródłowym języka C/C++. Typowe błędy kodowania zgłoszonej przez narzędzie obejmują przepełnienia buforu, niezainicjowanej pamięci, wyłuskania wskaźnika o wartości null i przecieków pamięci i zasobów. Narzędzie można również uruchomić testy względem [podstawowych wytycznych dotyczących języka C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integracja z IDE (zintegrowanym środowiskiem programistycznym)

Narzędzie do analizy kodu jest w pełni zintegrowana w środowisku IDE programu Visual Studio.

Podczas procesu kompilacji wszelkie ostrzeżenia generowane dla kodu źródłowego są wyświetlane na liście błędów. Możesz przejść do kodu źródłowego, który spowodował ostrzeżenie, a można wyświetlić dodatkowe informacje na temat przyczyny oraz możliwe rozwiązania tego problemu.

## <a name="command-line-support"></a>Obsługę wiersza polecenia

Narzędzie do analizy w wierszu polecenia można użyć również, jak pokazano w poniższym przykładzie:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 w wersji 15.7 lub nowszej** można uruchomić narzędzie z wiersza polecenia przy użyciu dowolnego systemu kompilacji, w tym narzędzia CMake.

## <a name="pragma-support"></a>Obsługa #pragma

Możesz użyć `#pragma` dyrektywy Traktuj ostrzeżenia jako błędy; Włącz lub wyłącz ostrzeżenia i pomijanie ostrzeżeń dla pojedynczych wierszy kodu. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie właściwości analizy kodu dla projektów C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Obsługa adnotacji

Adnotacje poprawić analizy kodu. Adnotacje zawierają dodatkowe informacje o warunkach wstępnych oraz po o parametrów funkcji i zwracanych typów. Aby uzyskać więcej informacji, zobacz [jak: Określanie dodatkowych informacji o kodzie za pomocą funkcji __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom narzędzie do analizy jako część zasad ewidencjonowania

Można wymagać, że wszystkie źródła kodu zaewidencjonowania spełniały pewne zasady. W szczególności chcesz upewnić się, że analiza została uruchomiona jako krok najnowszych kompilacji, lokalne. Aby uzyskać więcej informacji na temat włączania zasad analizy kodu ewidencjonowania, zobacz [tworzyć i za pomocą zasad analizy kodu zaewidencjonowania](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integracji kompilacji zespołu

Zintegrowane funkcje systemu kompilacji można użyć, aby uruchomić narzędzie do analizy kodu jako krok z [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] procesu kompilacji. Aby uzyskać więcej informacji, zobacz [potoki Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Zobacz także

- [Szybki start: Analiza kodu C/c++](quick-start-code-analysis-for-c-cpp.md)
- [Przewodnik: Analizowanie kodu C/C++ pod względem wad](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Analiza kodu C/C++ — ostrzeżenia](code-analysis-for-c-cpp-warnings.md)
- [Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++](using-the-cpp-core-guidelines-checkers.md)
- [W języku C++ podstawowych wytycznych dotyczących sprawdzania odwołania](code-analysis-for-cpp-corecheck.md)
- [Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizowanie jakości sterowników za pomocą narzędzi analizy kodu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analiza kodu dla sterowników ostrzeżenia](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
