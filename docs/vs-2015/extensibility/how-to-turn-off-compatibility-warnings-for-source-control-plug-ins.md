---
title: 'Instrukcje: Wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060582"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Instrukcje: Wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użytkownik może zostać wyświetlony kilka ostrzeżenia dotyczącego zgodności przy kontroli źródła w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ostrzeżenia prezentowane zależą od możliwości wtyczka do kontroli źródła i może być wyłączone jako szczegółowe tutaj.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenia: "Aby zapewnić optymalną integracją kontroli źródła przy użyciu programu Visual Studio..."  
  
- Ustaw następujący wpis rejestru (dodanie wartości, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001  
  
     To ostrzeżenie jest wyświetlane dla wszystkich non -[!INCLUDE[vsvss](../includes/vsvss-md.md)] wtyczek.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenia: "Zainstalowany dostawca kontroli źródła nie obsługuje wszystkie funkcje..."  
  
- Ustaw następujące wartości rejestru dwóch (dodanie wartości, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001  
  
     To ostrzeżenie jest wyświetlane, gdy wtyczka do kontroli źródła nie jawnego zapewnienia obsługi współużytkowania wątkowości dla wielu projektów (to znaczy, jeśli można sprawdzić w tylko jednym pliku, a projekt naraz).  
  
     Zaleca się do obsługi współużytkowania wątkowości (`SCC_CAP_REENTRANT` możliwości); będzie więc usunąć to ostrzeżenie. Jednak jeśli ta funkcja nie jest możliwe, można ustawić te wpisy rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi możliwości](../extensibility/capability-flags.md)
