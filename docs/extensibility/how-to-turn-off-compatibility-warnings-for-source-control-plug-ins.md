---
title: Wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a113dc3b4a4b3a8a4482dd092878851d740c6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911699"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Instrukcje: Wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego
Użytkownik może zostać wyświetlony kilka ostrzeżenia dotyczącego zgodności przy kontroli źródła w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ostrzeżenia prezentowane zależą od możliwości wtyczka do kontroli źródła i może być wyłączone jako szczegółowe tutaj.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenia: "Aby zapewnić optymalną integracją kontroli źródła przy użyciu programu Visual Studio"

- Ustaw następujący wpis rejestru (dodanie wartości, jeśli to konieczne):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   To ostrzeżenie jest wyświetlane dla wszystkich non -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] wtyczek.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenia: "Zainstalowany dostawca kontroli źródła nie obsługuje wszystkie funkcje"

- Ustaw następujące wartości rejestru dwóch (dodanie wartości, jeśli to konieczne):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     To ostrzeżenie jest wyświetlane, gdy wtyczka do kontroli źródła nie jawnego zapewnienia obsługi współużytkowania wątkowości dla wielu projektów (to znaczy, jeśli można sprawdzić w tylko jednym pliku, a projekt naraz).

     Zaleca się do obsługi współużytkowania wątkowości (`SCC_CAP_REENTRANT` możliwości); będzie więc usunąć to ostrzeżenie. Jednak jeśli ta funkcja nie jest możliwe, można ustawić te wpisy rejestru.

## <a name="see-also"></a>Zobacz także
- [Flagi możliwości](../extensibility/capability-flags.md)