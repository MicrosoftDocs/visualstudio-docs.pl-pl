---
title: Wyłącz ostrzeżenia dotyczące zgodności dla wtyczek kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710724"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Instrukcje: wyłączanie ostrzeżeń dotyczących zgodności dla wtyczek kontroli źródła
Podczas stosowania kontroli źródła w programie użytkownik może zobaczyć kilka ostrzeżeń dotyczących zgodności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Przedstawione ostrzeżenia zależą od możliwości wtyczki kontroli źródła i można je wyłączyć zgodnie z opisem w tym miejscu.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć Ostrzeżenie: "aby zapewnić optymalną integrację kontroli źródła z programem Visual Studio"

- Ustaw następujący wpis rejestru (w razie potrzeby Dodaj wartość):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   To ostrzeżenie jest wyświetlane dla wszystkich [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] niewtyczek.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć Ostrzeżenie: "zainstalowany dostawca kontroli źródła nie obsługuje wszystkich możliwości"

- Ustaw następujące dwie wartości rejestru (w razie potrzeby dodaj wartości):

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = wartość DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     To ostrzeżenie jest wyświetlane, jeśli wtyczka do kontroli źródła nie obsługuje jawnie współużytkowania wątkowości dla wielu projektów (oznacza to, że w danym momencie może zaewidencjonować tylko jeden plik i projekt).

     Najlepiej jest obsługiwać współużytkowania wątkowości ( `SCC_CAP_REENTRANT` możliwości). spowoduje to usunięcie tego ostrzeżenia. Jeśli jednak ta obsługa nie jest możliwa, można ustawić te wpisy rejestru.

## <a name="see-also"></a>Zobacz też
- [Flagi możliwości](../extensibility/capability-flags.md)
