---
title: Wyłącz ostrzeżenia dla wtyczek kontroli źródła
description: Podczas stosowania kontroli źródła w programie Visual Studio użytkownik może zobaczyć kilka ostrzeżeń dotyczących zgodności. Dowiedz się, jak wyłączyć te ostrzeżenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7bbf2f01b2fb82e3bbb640eba5c44f99f2b7a53
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074902"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Instrukcje: wyłączanie ostrzeżeń dotyczących zgodności dla wtyczek kontroli źródła

Podczas stosowania kontroli źródła w programie użytkownik może zobaczyć kilka ostrzeżeń dotyczących zgodności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Przedstawione ostrzeżenia zależą od możliwości wtyczki kontroli źródła i można je wyłączyć zgodnie z opisem w tym miejscu.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć Ostrzeżenie: "aby zapewnić optymalną integrację kontroli źródła z programem Visual Studio"

- Ustaw następujący wpis rejestru (w razie potrzeby Dodaj wartość):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   To ostrzeżenie jest wyświetlane dla wszystkich [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] niewtyczek.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć Ostrzeżenie: "zainstalowany dostawca kontroli źródła nie obsługuje wszystkich możliwości"

- Ustaw następujące dwie wartości rejestru (w razie potrzeby dodaj wartości):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     To ostrzeżenie jest wyświetlane, jeśli wtyczka do kontroli źródła nie obsługuje jawnie współużytkowania wątkowości dla wielu projektów (oznacza to, że w danym momencie może zaewidencjonować tylko jeden plik i projekt).

     Najlepiej jest obsługiwać współużytkowania wątkowości ( `SCC_CAP_REENTRANT` możliwości). spowoduje to usunięcie tego ostrzeżenia. Jeśli jednak ta obsługa nie jest możliwa, można ustawić te wpisy rejestru.

## <a name="see-also"></a>Zobacz też

- [Flagi możliwości](../extensibility/capability-flags.md)
