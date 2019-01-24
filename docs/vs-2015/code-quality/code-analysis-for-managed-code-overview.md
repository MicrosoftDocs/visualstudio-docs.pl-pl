---
title: Analiza kodu dla zarządzanego kodu — omówienie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a38909eb0917b3ad5b02d5e953c17c950c7c819e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755973"
---
# <a name="code-analysis-for-managed-code-overview"></a>Analiza kodu dla zarządzanego kodu — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiza kodu dla kodu zarządzanego analizuje zestawy zarządzane i raportuje informacje o zestawach, takie jak naruszenia programowania i projektowania reguły określone w wytycznych projektowych programu Microsoft .NET Framework.  
  
 Narzędzie do analizy reprezentuje kontrole wykonywane podczas analizy jako komunikaty ostrzegawcze. Komunikaty ostrzegawcze identyfikują wszystkie istotne błędy programowania i projektowania i gdy jest możliwe, dostarczają informacji na temat sposobu rozwiązania problemu.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja z IDE (zintegrowanym środowiskiem programistycznym)  
 Jako deweloper można uruchomić analizę kodu projektu automatycznie lub uruchomić ją ręcznie.  
  
 Aby uruchomić analizę kodu za każdym razem, tworzysz projekt, należy wybrać **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS)** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Aby uruchomić analizę kodu ręcznie dla projektu, na **analizy** menu, kliknij przycisk **Uruchom analizę kodu dla**_ProjectName_. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Zestawy reguł  
 Reguły analizy kodu dla zarządzanego kodu są grupowane w *zestawów reguł*. Można użyć jednej standardowych zestawów reguł Microsoft lub można utworzyć niestandardowy zestaw reguł, aby spełnić szczególną potrzebę. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>W pomijanie źródła  
 Często jest to użyteczne, aby wskazać, że ostrzeżenie nie ma zastosowania. Informuje dewelopera i inne osoby, które mogą później przejrzeć kod że ostrzeżenie zostało zbadane a następnie pominięte lub ignorowane.  
  
 W pomijanie źródła ostrzeżeń, które jest implementowane za pomocą atrybutów niestandardowych. Aby pominąć ostrzeżenie, Dodaj atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w poniższym przykładzie:  
  
 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```
  
 Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchamianie analizy kodu jako części zasad ewidencjonowania  
 Jako organizacja można wymagać, aby wszystkie zaewidencjonowania spełniały pewne zasady. W szczególności chcesz upewnić się, że spełnione są następujące zasady:  
  
- Nie było żadnych błędów kompilacji w kodzie, które zostały zaewidencjonowane.  
  
- Analiza kodu została uruchomiona jako część najnowszej kompilacji.  
  
  Można to zrobić poprzez określenie zasad ewidencjonowania. Aby uzyskać więcej informacji, zobacz [udoskonalanie jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integracji kompilacji zespołu  
 Zintegrowane funkcje systemu kompilacji można użyć, aby uruchomić narzędzie do analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [skompilować aplikację](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Instrukcje: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
