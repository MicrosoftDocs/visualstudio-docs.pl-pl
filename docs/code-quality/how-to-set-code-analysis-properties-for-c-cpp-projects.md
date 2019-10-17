---
title: 'Porady: ustawianie właściwości analizy kodu dla projektów C/C++'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 27f3d68d28b8d1799c52fcf83c6a00dc5f81f48a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448917"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Porady: ustawianie właściwości analizy kodu dla projektów C/C++

Można skonfigurować reguły używane przez narzędzie do analizy kodu do analizowania kodu w każdej konfiguracji projektu. Ponadto można skierować analizę kodu, aby pominąć ostrzeżenia z kodu, który został wygenerowany i dodany do projektu przez narzędzie innej firmy.

## <a name="code-analysis-property-page"></a>Strona właściwości analizy kodu

Strona właściwości **Analiza kodu** zawiera wszystkie ustawienia konfiguracji analizy kodu dla projektu MSBuild. Aby otworzyć stronę właściwości Analiza kodu dla projektu w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**. Następnie rozwiń węzeł **Właściwości konfiguracji** i wybierz kartę **Analiza kodu** .

## <a name="project-configuration-and-platform"></a>Konfiguracja i platforma projektu

Lista **konfiguracji** i lista **platform** w górnej części okna umożliwiają stosowanie różnych ustawień analizy kodu do różnych konfiguracji projektu i kombinacji platform. Na przykład można skierować analizę kodu w celu zastosowania jednego zestawu reguł do projektu na potrzeby kompilacji debugowania i innego zestawu dla kompilacji wydań.

## <a name="enabling-code-analysis"></a>Włączanie analizy kodu

Możesz włączyć analizę kodu dla projektu, przełączając opcje **Włącz analizę kodu firmy Microsoft** i **Włącz opcję Clang-uporządkowanego** , a następnie skonfiguruj, czy ma on działać w ramach kompilacji, wybierając pozycję **Włącz analizę kodu podczas kompilacji**. W połączeniu z listą **konfiguracji** można na przykład zdecydować, aby wyłączyć analizę kodu dla kompilacji debugowania i włączyć ją dla kompilacji wydań.

Analiza kodu została zaprojektowana w celu ułatwienia poprawy jakości kodu i unikania typowych pułapek. W związku z tym należy uważnie rozważyć, czy należy wyłączyć analizę kodu. Zazwyczaj lepiej jest wyłączyć zestawy reguł, indywidualne reguły lub indywidualne kontrole, które nie mają być stosowane do projektu.

## <a name="cmake-configuration"></a>Konfiguracja CMake

W projektach CMake Zmień wartość kluczy `enableMicrosoftCodeAnalysis` i `enableClangTidyCodeAnalysis` w `CMakeSettings.json`, aby włączyć lub wyłączyć analizę kodu. Aby uzyskać więcej informacji, zobacz [Używanie Clang-uporządkowanego w programie Visual Studio](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>Zobacz także

- [Analiza jakości zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md)
- [Analiza kodu C/C++ — ostrzeżenia](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Zestawy reguł dla C++ kodu](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Korzystanie z Clang-uporządkowanego](../code-quality/clang-tidy.md)
