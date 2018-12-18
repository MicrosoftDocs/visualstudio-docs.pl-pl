---
title: 'Porady: wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eacdce1e311ad15e449ddec6e99ffcf9e4d26c8a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726104"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Porady: wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użytkownik może zostać wyświetlony kilka ostrzeżenia dotyczącego zgodności przy kontroli źródła w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ostrzeżenia prezentowane zależą od możliwości wtyczka do kontroli źródła i może być wyłączone jako szczegółowe tutaj.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Aby wyłączyć ostrzeżenia: "Aby zapewnić optymalną integracją kontroli źródła z programem Visual Studio..."  
  
-   Ustaw następujący wpis rejestru (dodanie wartości, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     To ostrzeżenie jest wyświetlane dla wszystkich non -[!INCLUDE[vsvss](../includes/vsvss-md.md)] wtyczek.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Aby wyłączyć ostrzeżenia: "zainstalowany dostawca kontroli źródła nie obsługuje wszystkie funkcje..."  
  
-   Ustaw następujące wartości rejestru dwóch (dodanie wartości, jeśli to konieczne):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     To ostrzeżenie jest wyświetlane, gdy wtyczka do kontroli źródła nie jawnego zapewnienia obsługi współużytkowania wątkowości dla wielu projektów (to znaczy, jeśli można sprawdzić w tylko jednym pliku, a projekt naraz).  
  
     Zaleca się do obsługi współużytkowania wątkowości (`SCC_CAP_REENTRANT` możliwości); będzie więc usunąć to ostrzeżenie. Jednak jeśli ta funkcja nie jest możliwe, można ustawić te wpisy rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Flagi możliwości](../extensibility/capability-flags.md)

