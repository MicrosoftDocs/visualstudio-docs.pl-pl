---
title: 'Instrukcje: Ustawianie właściwości analizy kodu dla projektów C/C++'
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
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 72866618383382389ad5e5706ae2a0999c89c346
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923983"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Instrukcje: Ustawianie właściwości analizy kodu dla projektów C/C++
Można skonfigurować reguły używane przez narzędzie do analizy kodu do analizowania kodu w każdej konfiguracji projektu. Ponadto można skierować analizę kodu, aby pominąć ostrzeżenia z kodu, który został wygenerowany i dodany do projektu przez narzędzie innej firmy.

## <a name="code-analysis-property-page"></a>Strona właściwości analizy kodu
Strona właściwości **Analiza kodu** zawiera wszystkie ustawienia konfiguracji analizy kodu dla projektu. Aby otworzyć stronę właściwości Analiza kodu dla projektu w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**. Następnie rozwiń węzeł **Właściwości konfiguracji** i wybierz kartę **Analiza kodu** .

## <a name="project-configuration-and-platform"></a>Konfiguracja i platforma projektu
Lista **konfiguracji** i lista **platform** umożliwiają stosowanie różnych ustawień analizy kodu do różnych konfiguracji projektu i kombinacji platform. Na przykład można skierować analizę kodu w celu zastosowania jednego zestawu reguł do projektu na potrzeby kompilacji debugowania i innego zestawu dla kompilacji wydań.

## <a name="enabling-code-analysis"></a>Włączanie analizy kodu
Możesz zdecydować, czy włączyć analizę kodu dla projektu, wybierając opcję **Włącz analizę kodu dla C/C++ on Build**. W połączeniu z listą **konfiguracji** można na przykład zdecydować, aby wyłączyć analizę kodu dla kompilacji debugowania i włączyć ją dla kompilacji wydań.

Jeśli projekt zawiera kod zarządzany, możesz zdecydować, czy włączyć lub wyłączyć analizę kodu, wybierając opcję **Włącz analizę kodu podczas kompilacji**.

Analiza kodu została zaprojektowana w celu ułatwienia poprawy jakości kodu i unikania typowych pułapek. W związku z tym należy uważnie rozważyć, czy należy wyłączyć analizę kodu. Zazwyczaj lepiej jest wyłączyć zestawy reguł lub pojedyncze reguły, które nie mają być stosowane do projektu.

## <a name="generated-code"></a>Wygenerowany kod
Deweloperzy często wykorzystują narzędzia, aby szybko opracowywać aplikacje. Narzędzia te mogą generować kod, który jest dodawany do projektu. Warto zapoznać się z naruszeniami reguł, które są wykrywane przez analizę kodu w wygenerowanym kodzie. Nie trzeba jednak ich zobaczyć, jeśli nie chcesz zachować kodu.

Pole wyboru **Pomiń wyniki z wygenerowanego kodu** na stronie właściwości **Ogólne** umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu zarządzanego, który jest generowany przez narzędzie innej firmy.

## <a name="rule-sets"></a>Zestawy reguł
Jeśli projekt zawiera kod zarządzany, możesz wybrać reguły do zastosowania w analizie kodu, wybierając zestaw reguł z listy **Uruchom ten zestaw reguł** .

## <a name="see-also"></a>Zobacz też

- [Analiza jakości zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md)
- [Analiza kodu C/C++ — ostrzeżenia](../code-quality/code-analysis-for-c-cpp-warnings.md)