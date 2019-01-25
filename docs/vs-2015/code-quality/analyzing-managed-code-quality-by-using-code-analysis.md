---
title: Analiza jakości zarządzanego kodu za pomocą analizy kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d8740b79b026ade7f3da19aa4a89cacd94df17d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772449"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analiza jakości zarządzanego kodu za pomocą analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia do analizy kodu w programie Visual Studio służy do wykrywania potencjalnych problemów w kodzie, takiej jak-secure data access, naruszenia użycia i problemów projektowych. Analiza kodu działa na .NET Framework, natywnego (C i C++) i bazy danych aplikacji. Analiza kodu dla kodu zarządzanego organizuje reguły w *zestawów reguł* przeznaczonych określonych występujące problemy z kodem.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Typowe zadania|Zawartość pomocnicza|  
|------------------|------------------------|  
|**Uzyskaj praktyczne:** Poznaj podstawowe zasady analizy kodu, poprawiając defektów w prostej aplikacji .NET Framework.|-   [Wskazówki: Analizowanie kodu zarządzanego pod względem wad kodu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurowanie analizy kodu dla projektu:** Reguły dla zarządzanego kodu są zorganizowane w zestawy reguł, przeznaczonych dla określonych obszarach, takich jak bezpieczeństwo i projektowanie. Można użyć jednego z firmy Microsoft, standardowe reguły Ustawia lub tworzyć własne.|-   [Analiza kodu dla zarządzanego kodu — omówienie](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Przeprowadź analizę kodu:** Można określić analiza kodu będzie wykonywany automatycznie, ilekroć dany plik konfiguracyjny jest wbudowana i uruchomić analizę kodu ręcznie dla projektu.|-   [Jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Jak: Ręczne przeprowadzanie analizy kodu](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizowanie wyników analizy kodu:** Ostrzeżenia analizy kodu i błędy są wymienione w oknie analizy kodu. Możesz wybrać ostrzeżenie lub tytuł błędu, aby wyświetlić dodatkowe informacje na temat ostrzeżenia oraz do wyświetlania i wyróżnić wiersza kodu źródłowego, które spowodowało wyzwolenie reguły. Możesz wybrać identyfikator ostrzeżenia, aby wyświetlić szczegółowe informacje w bibliotece MSDN, który zawiera informacje i przykłady dotyczące rozwiązania problemu.|-   [Jak: Wyświetlanie defektów kodu zarządzanego](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analiza kodu dla zarządzanego kodu — ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Ostrzeżenia dzięki CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integracja analizy kodu, z cyklem życia Twojej programowania:** Zasady ewidencjonowania w [!INCLUDE[esprscc](../includes/esprscc-md.md)] Włącz zespołów programistycznych, aby upewnić się, że kod wszystkie zaewidencjonowania spełniają wspólny zestaw standardów analizy kodu. Tworzenie elementu roboczego dla naruszenie reguły analizy kodu jest prostą procedurę, które można wykonywać w oknie Lista błędów.|-   [Poprawa jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Jak: Synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Jak: Tworzenie elementu roboczego dla defektu kodu zarządzanego](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
