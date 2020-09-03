---
title: Analizowanie jakości kodu zarządzanego za pomocą analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671116"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analiza jakości zarządzanego kodu za pomocą analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia do analizy kodu w programie Visual Studio umożliwiają odnajdywanie potencjalnych problemów w kodzie, takich jak niebezpieczny dostęp do danych, naruszenia użycia i problemy z projektowaniem. Analiza kodu działa na .NET Framework, natywnych (C i C++) i aplikacjach baz danych. Analiza kodu dla kodu zarządzanego organizuje reguły w *zestawach reguł* , których dotyczą konkretne problemy z kodowaniem.

## <a name="common-tasks"></a>Typowe zadania

|Typowe zadania|Zawartość pomocnicza|
|------------------|------------------------|
|**Uzyskaj praktyczne wskazówki:** Poznaj podstawy analizy kodu, poprawiając wady w prostej aplikacji .NET Framework.|-   [Przewodnik: Analizowanie kodu zarządzanego pod kątem wad kodu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Konfiguruj analizę kodu dla projektu:** Reguły dla kodu zarządzanego są zorganizowane w zestawy reguł, które są przeznaczone dla określonych obszarów, takich jak zabezpieczenia i projektowanie. Możesz użyć jednego z standardowych zestawów reguł firmy Microsoft lub utworzyć własne.|-   [Analiza kodu dla zarządzanego kodu — Omówienie](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Uruchom analizę kodu:** Można określić, że analiza kodu ma być uruchamiana automatycznie za każdym razem, gdy tworzona jest konfiguracja projektu, i można uruchomić analizę kodu ręcznie w projekcie.|-   [Instrukcje: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Instrukcje: ręczne uruchamianie analizy kodu](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Analizuj wyniki analizy kodu:** Ostrzeżenia i błędy analizy kodu są wyświetlane w oknie Analiza kodu. Możesz wybrać ostrzeżenie lub tytuł błędu, aby wyświetlić dodatkowe informacje o ostrzeżeniu i wyświetlić i wyróżnić wiersz kodu źródłowego, który uruchomił regułę. Możesz wybrać identyfikator ostrzeżenia, aby wyświetlić szczegółowe informacje w bibliotece MSDN zawierającej informacje i Przykłady sposobu rozwiązania problemu.|-   [Instrukcje: wyświetlanie usterek kodu zarządzanego](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analiza kodu dla ostrzeżeń związanych z kodem zarządzanym](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Ostrzeżenia według CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Integruj analizę kodu z cyklem życia rozwoju:** Zasady ewidencjonowania w programie [!INCLUDE[esprscc](../includes/esprscc-md.md)] umożliwiają zespołom programistycznym upewnienie się, że wszystkie operacje sprawdzania kodu spełniają wspólny zestaw standardów analizy kodu. Tworzenie elementu pracy dla naruszenia reguły analizy kodu jest prostą procedurą, którą można wykonać w oknie Lista błędów.|-   [Zwiększanie jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Instrukcje: synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Instrukcje: Tworzenie elementu pracy dla defektu kodu zarządzanego](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
