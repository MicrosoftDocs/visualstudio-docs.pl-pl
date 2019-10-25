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
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 515b9b7eb1b1a4d2dbee6329be782386b8370338
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806312"
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla języka CC++ /przegląd

Narzędzie analityczneC++ c/Code zawiera informacje o możliwych defektach w kodzie źródłowymC++ c/. Typowe błędy kodowania zgłoszone przez narzędzie obejmują przepełnienia buforów, niezainicjowaną pamięć, odnośniki wskaźnika o wartości null oraz przecieki pamięci i zasobów. Narzędzie może również uruchamiać testy w oparciu o [ C++ podstawowe wytyczne](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Narzędzie do analizy kodu jest w pełni zintegrowane w środowisku IDE programu Visual Studio.

W trakcie procesu kompilacji wszystkie ostrzeżenia wygenerowane dla kodu źródłowego pojawiają się w Lista błędów. Możesz przejść do kodu źródłowego, który spowodował ostrzeżenie, i można wyświetlić dodatkowe informacje o przyczynie problemu oraz ewentualnych rozwiązaniach.

## <a name="command-line-support"></a>Obsługa wiersza polecenia

Możesz również użyć narzędzia analizy z wiersza polecenia, jak pokazano w następującym przykładzie:

```cmd
C:\>cl /analyze Sample.cpp
```

**Program Visual Studio 2017 w wersji 15,7 lub nowszej:** Narzędzie można uruchomić z wiersza polecenia z dowolnym systemem kompilacji, w tym CMake.

## <a name="pragma-support"></a>Obsługa #pragma

Aby traktować ostrzeżenia jako błędy, można użyć dyrektywy `#pragma`. Włącza lub wyłącza ostrzeżenia oraz pomija ostrzeżenia dla poszczególnych wierszy kodu. Aby uzyskać więcej informacji, zobacz [dyrektywy pragma i słowo kluczowe __pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Obsługa adnotacji

Adnotacje poprawiają dokładność analizy kodu. Adnotacje zawierają dodatkowe informacje na temat parametrów funkcji i typów zwracanych. Aby uzyskać więcej informacji, zobacz [Używanie adnotacji sal w celuC++ zmniejszenia wad języka C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom Narzędzie analizy jako część zasad ewidencjonowania

Można wymagać, aby wszystkie operacje ewidencjonowania kodu źródłowego spełniały określone zasady. W szczególności chcesz upewnić się, że analiza została uruchomiona jako krok ostatniej kompilacji lokalnej. Aby uzyskać więcej informacji na temat włączania zasad zaewidencjonowania analizy kodu, zobacz [Tworzenie zasad ewidencjonowania analizy kodu i korzystanie](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)z nich.

## <a name="team-build-integration"></a>Integracja kompilacji zespołowej

Możesz użyć zintegrowanych funkcji systemu kompilacji, aby uruchomić Narzędzie analizy kodu jako krok procesu kompilacji [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Analiza kodu dla języka C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Przewodnik: Analizowanie kodu CC++ /Code dla wad](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Analiza kodu C/C++ — ostrzeżenia](code-analysis-for-c-cpp-warnings.md)
- [Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++](using-the-cpp-core-guidelines-checkers.md)
- [C++Informacje dotyczące najważniejszych wskazówek dotyczących sprawdzania](code-analysis-for-cpp-corecheck.md)
- [Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizowanie jakości sterowników przy użyciu narzędzi do analizy kodu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analiza kodu dla ostrzeżeń dotyczących sterowników](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
