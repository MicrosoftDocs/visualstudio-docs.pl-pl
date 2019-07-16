---
title: 'Instrukcje: Ustawianie właściwości analizy kodu dla projektów C i C++ | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 4ebed266924861dac4bfc9e316a56907dbd11534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201319"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Instrukcje: Ustawianie właściwości analizy kodu dla projektów C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować zasady, które używa narzędzie do analizy kodu w celu analizowania kodu w każdej konfiguracji projektu. Ponadto można kierować analizy kodu, aby pominąć ostrzeżenia, od kodu, który został wygenerowany i dodany do projektu za pomocą narzędzia innych firm.  
  
## <a name="code-analysis-property-page"></a>Strona właściwości analizy kodu  
 **Analizy kodu** strona właściwości zawiera wszystkie ustawienia konfiguracji analizy kodu dla projektu. Aby otworzyć stronę właściwości analizy kodu dla projektu w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**. Następnie rozwiń węzeł **właściwości konfiguracji** i wybierz **analizy kodu** kartę.  
  
## <a name="project-configuration-and-platform"></a>Konfiguracja projektu i Platform  
 **Konfiguracji** listy i **platformy** listy umożliwiają zastosowanie ustawienia analizy kodu w różnych kombinacji konfiguracji i platformy inny projekt. Na przykład można kierować kompilacje analizy kodu, aby zastosować jeden zestaw reguł do projektu do debugowania i inny zestaw w wersji kompilacji.  
  
## <a name="enabling-code-analysis"></a>Włączanie analizy kodu  
 Zdecyduj, czy włączyć analizy kodu dla projektu, wybierając **Włącz kod analiza C/C++ podczas kompilacji**. W połączeniu z **konfiguracji** listy, można na przykład zdecydujesz się wyłączyć analizę kodu dla kompilacji do debugowania i włącz ją dla wersji kompilacji.  
  
 Jeśli projekt zawiera kod zarządzany, możesz zdecydować, czy włączyć lub wyłączyć analizy kodu, wybierając **Włącz analizę kodu podczas kompilacji**.  
  
 Analiza kodu jest przeznaczony do pomagają poprawić jakość kodu i uniknąć typowych pułapek. W związku z tym, zastanów się, czy wyłączyć analizę kodu. Jest to zazwyczaj lepiej wyłączyć zestawy reguł lub poszczególnych reguł, które mają być stosowane do projektu.  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Deweloperzy często narzędzia ułatwiające szybkie tworzenie aplikacji. Narzędzia te może wygenerować kod, który jest dodawany do projektu. Możesz chcieć wyświetlić naruszenia reguły, które analizy kodu, który umożliwia odnalezienie w wygenerowanym kodzie. Jednak możesz nie chcieć je wyświetlić, jeśli nie chcesz utrzymywać kod.  
  
 **Pomijaj wyniki z wygenerowany kod** pole wyboru na **ogólne** strony właściwości można wybrać, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu zarządzanego, który jest generowany przez narzędzia innej firmy .  
  
## <a name="rule-sets"></a>Zestawy reguł  
 Jeśli projekt zawiera kod zarządzany, możesz wybrać zasady do zastosowania w analizy kodu, wybierając zestaw reguł z **Uruchom ten zestaw reguł** listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Analiza kodu C/C++ — ostrzeżenia](../code-quality/code-analysis-for-c-cpp-warnings.md)
