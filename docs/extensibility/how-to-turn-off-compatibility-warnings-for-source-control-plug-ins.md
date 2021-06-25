---
title: Wyłączanie ostrzeżeń dotyczących wtyczek kontroli źródła
description: Użytkownik może zobaczyć kilka ostrzeżeń dotyczących zgodności podczas korzystania z kontroli źródła w Visual Studio. Dowiedz się, jak wyłączyć te ostrzeżenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ced04b09f8d4442cf0769ef503ee52772eccc0f6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905751"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Jak wyłączyć ostrzeżenia zgodności dla wtyczek kontroli źródła

Podczas korzystania z kontroli źródła w programie użytkownik może zobaczyć kilka ostrzeżeń dotyczących [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zgodności. Przedstawione ostrzeżenia zależą od możliwości wtyczki kontroli źródła i można je wyłączyć zgodnie z informacjami przedstawionymi tutaj.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenie: "Aby zapewnić optymalną integrację kontroli źródła z Visual Studio"

- Ustaw następujący wpis rejestru (dodając wartość w razie potrzeby):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   To ostrzeżenie jest wyświetlane dla wszystkich wtyczek [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] innych niż.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenie: "Zainstalowany dostawca kontroli źródła nie obsługuje wszystkich możliwości"

- Ustaw następujące dwie wartości rejestru (w razie potrzeby dodając wartości):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:000000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     To ostrzeżenie jest wyświetlane, jeśli wtyczka kontroli źródła nie obsługuje jawnie ponownego weswojenia dla wielu projektów (to znaczy, jeśli może zaewidencjować tylko jeden plik i projekt jednocześnie).

     Najlepszym rozwiązaniem jest obsługa ponownego wespoju `SCC_CAP_REENTRANT` (możliwość). Spowoduje to usunięcie tego ostrzeżenia. Jeśli jednak ta obsługa nie jest możliwa, można ustawić te wpisy rejestru.

## <a name="see-also"></a>Zobacz też

- [Flagi możliwości](../extensibility/capability-flags.md)
