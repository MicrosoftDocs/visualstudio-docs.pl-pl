---
title: Tworzenie i używanie zasad ewidencjonowania analizy kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 274aa497e004ddafee9a56b028f3001bb8deb630
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437077"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Tworzenie zasad ewidencjonowania analizy kodu i korzystanie z nich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy używasz Team Foundation Version Control (TFVC), można utworzyć zasad analizy kodu ewidencjonowania programu .NET Framework i natywne projekty kodu (C/C++) w projekcie zespołowym. Zasady analizy kodu ewidencjonowania służy do kontroli i poprawy jakości kodu, który jest ewidencjonowany w kodzie podstawowym.  
  
 Zasady zostają spełnione, gdy lokalna kompilacja jest aktualna oraz analiza kodu została uruchomiona na najnowszych plikach źródłowych. Co najmniej reguły analizy kodu, które są włączone w projekcie kodu musi zawierać te same reguły jako te, które są definiowane w team project zasad ewidencjonowania. Reguły, które zostały określone jako błędy w ustawieniach projektu zespołowego musi być także określona jako błędy w projekcie kodu  
  
> [!IMPORTANT]
> Nie można zastosować zasad ewidencjonowania analizy kodu do projektów witryny sieci web. Mogą być stosowane do projektów aplikacji sieci web.  
  
 Tworzenie zasad ewidencjonowania analizy kodu za pomocą ustawień projektu zespołowego [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Zasady ewidencjonowania są określone i wymuszane dla projektu zespołowego, ale przebiegi analizy kodu są skonfigurowane i uruchamiane dla poszczególnych projektów kodu, na komputerach rozwoju lokalnego. W tej sekcji opisano sposób określania zasad ewidencjonowania analizy kodu dla projektu zespołowego oraz sposób implementacji niestandardowych zasad analizy kodu dla kodu zarządzanego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie lub aktualizowanie standardowych zasad analizy kodu zaewidencjonowania](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Wyjaśnia kroki, których używasz, aby ustawić i zmodyfikować zasady analizy kodu dla projektu zespołowego.  
  
 [Implementowanie niestandardowych zasad ewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Wyjaśnia kroki, które są używane do tworzenia niestandardowego zestawu reguł dla zasad ewidencjonowania projektu zespołowego i synchronizować projekty kodu projektu zespołowego za pomocą zasad ewidencjonowania.  
  
 [Zgodność wersji dla zasad zaewidencjonowania analizy kodu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Wyjaśnia kod analizy ewidencjonowania problemy ze zgodnością między wersjami [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Instrukcje: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Wyjaśnia, jak dodać wyrazy i tokeny do słownika, do którego odwołują się zasady nazewnictwa analizy kodu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Ustawianie i wymuszanie bram jakości](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Doskonalenie jakości kodu za pomocą zasad zaewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
