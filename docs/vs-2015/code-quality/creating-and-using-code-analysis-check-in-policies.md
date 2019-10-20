---
title: Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667712"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Tworzenie zasad ewidencjonowania analizy kodu i korzystanie z nich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z Kontrola wersji serwera Team Foundation (TFVC), można utworzyć zasady ewidencjonowania analizy kodu dla projektów kodu .NET Framework i natywnych (C/C++) w projekcie zespołowym. Za pomocą zasad ewidencjonowania analizy kodu można kontrolować i poprawiać jakość kodu, który jest sprawdzany w bazie kodu.

 Zasady są przekazywane, gdy lokalna kompilacja jest aktualna, a analiza kodu została uruchomiona na najnowszych plikach źródłowych. Co najmniej reguły analizy kodu, które są włączone w projekcie kodu, muszą zawierać takie same reguły jak te, które są zdefiniowane w zasadach ewidencjonowania projektu zespołowego. Reguły, które zostały określone jako błędy w ustawieniach projektu zespołowego, muszą być również określone jako błędy w projekcie kodu

> [!IMPORTANT]
> Nie można zastosować zasad zaewidencjonowania analizy kodu do projektów witryny sieci Web. Mogą być stosowane do projektów aplikacji sieci Web.

 Zasady ewidencjonowania analizy kodu można tworzyć przy użyciu ustawień projektu zespołowego [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Zasady ewidencjonowania są określone i wymuszane dla projektu zespołowego, ale przebiegi analizy kodu są konfigurowane i uruchamiane dla poszczególnych projektów kodu na lokalnych komputerach deweloperskich. W tej sekcji opisano sposób określania zasad zaewidencjonowania analizy kodu dla projektu zespołowego i implementowania niestandardowych zasad analizy kodu dla kodu zarządzanego.

## <a name="in-this-section"></a>W tej sekcji
 [Instrukcje: Tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Wyjaśnia kroki, które należy wykonać, aby ustawić i zmodyfikować zasady analizy kodu dla projektu zespołowego.

 [Implementowanie niestandardowych zasad ewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Wyjaśnia kroki, które należy wykonać, aby utworzyć niestandardowy zestaw reguł dla zasad ewidencjonowania dla projektu zespołowego i zsynchronizować projekty kodu projektu zespołowego z zasadami ewidencjonowania.

 [Zgodność wersji dla zasad zaewidencjonowania analizy kodu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Wyjaśnia problemy ze zgodnością zaewidencjonowania analizy kodu między wersjami [!INCLUDE[vstsLong](../includes/vstslong-md.md)].

 [Instrukcje: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Wyjaśnia, jak dodawać wyrazy i tokeny do słownika, do którego odwołuje się reguła nazewnictwa analizy kodu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Ustawianie i wymuszanie bram jakości](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Doskonalenie jakości kodu za pomocą zasad zaewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
