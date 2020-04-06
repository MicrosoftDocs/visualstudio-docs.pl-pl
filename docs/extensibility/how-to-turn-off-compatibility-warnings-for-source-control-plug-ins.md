---
title: Wyłącz ostrzeżenia o zgodności dla wtyczek kontroli źródła | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710724"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Jak: Wyłącz ostrzeżenia o zgodności dla wtyczek kontroli źródła
Użytkownik może zobaczyć kilka ostrzeżeń zgodności podczas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]stosowania kontroli źródła w . Przedstawione ostrzeżenia zależą od możliwości wtyczki kontroli źródła i można je wyłączyć, jak opisano tutaj.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenie: "Aby zapewnić optymalną integrację kontroli źródła z programem Visual Studio"

- Ustaw następujący wpis rejestru (dodanie wartości w razie potrzeby):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   To ostrzeżenie jest wyświetlane dla[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] wszystkich innych niż wtyczki.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenie: "Zainstalowany dostawca kontroli źródła nie obsługuje wszystkich możliwości"

- Ustaw następujące dwie wartości rejestru (dodanie wartości w razie potrzeby):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     To ostrzeżenie jest wyświetlane, jeśli wtyczka kontroli źródła nie obsługuje jawnie reentrancy dla wielu projektów (to znaczy, jeśli można zaewidencjonować tylko jeden plik i projekt naraz).

     Najlepiej jest wspierać reentrancy`SCC_CAP_REENTRANT` (zdolność); spowoduje to usunięcie tego ostrzeżenia. Jeśli jednak ta obsługa nie jest możliwa, można ustawić te wpisy rejestru.

## <a name="see-also"></a>Zobacz też
- [Flagi możliwości](../extensibility/capability-flags.md)
