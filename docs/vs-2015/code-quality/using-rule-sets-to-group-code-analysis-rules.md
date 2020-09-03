---
title: Korzystanie z zestawów reguł do grupowania reguł analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603482"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Korzystanie z zestawów reguł do grupowania reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas konfigurowania analizy kodu w programie [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] lub można [!INCLUDE[vsPro](../includes/vspro-md.md)] wybrać jedną z listy wbudowanych *zestawów reguł*firmy Microsoft. Zestaw reguł jest logicznym grupowaniem reguł analizy kodu, które identyfikują docelowe problemy i określone warunki. Na przykład można zastosować zestaw reguł, który jest przeznaczony do skanowania kodu dla publicznie dostępnych interfejsów API lub można zastosować zestaw reguł, który zawiera tylko minimalne zalecane reguły. Można również zastosować zestaw reguł, który zawiera wszystkie reguły.

 Zestaw reguł można dostosować, dodając lub usuwając reguły lub zmieniając reguły, aby były wyświetlane w oknie **Lista błędów** jako ostrzeżenia lub błędy. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Po dostosowaniu zestawu reguł strona zestawu reguł dostarcza narzędzia do wyszukiwania i filtrowania pomocne w przetwarzaniu.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Uzyskaj praktyczne wskazówki:** Użyj narzędzi analizy kodu, aby określić niestandardowy zestaw reguł, który umożliwia znajdowanie i rozwiązywanie problemów w prostej aplikacji .NET Framework.|-   [Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Konfiguruj analizę kodu dla projektu:** Wybierz istniejący zestaw reguł dla projektu, witryny sieci Web lub rozwiązania.|-   [Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Używanie zestawów reguł do określania reguł C++ do uruchomienia](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Instrukcje: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Instrukcje: Określanie zestawów reguł dla wielu projektów w rozwiązaniu](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Dostosuj zestaw reguł:** Określ reguły, które mają być stosowane do projektu.|-   [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Zapoznaj się z wbudowanymi zestawami reguł:** Wyświetl reguły analizy kodu, które składają się na wbudowane zestawy reguł.|-   [Odwołanie do zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md)|
|**Integruj analizę kodu z Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] zasady ewidencjonowania umożliwiają zespołom programistycznym upewnienie się, że wszystkie operacje sprawdzania kodu spełniają wspólny zestaw standardów analizy kodu.|-   [Instrukcje: synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
