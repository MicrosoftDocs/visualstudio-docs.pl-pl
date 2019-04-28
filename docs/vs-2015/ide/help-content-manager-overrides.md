---
title: Przesłonięcia menedżera zawartości pomocy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9dfd7f7d75a44cb28e2829e38c27b63a329eacaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584556"
---
# <a name="help-content-manager-overrides"></a>Przesłonięcia Menedżera zawartości Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmodyfikować rejestr, aby zmienić domyślne zachowanie w Podglądzie pomocy i pomocy funkcjach dostępnych w środowisku IDE programu Visual Studio.  
  
|Zadanie|Klucz rejestru|Wartość i definicji|  
|----------|------------------|--------------------------|  
|Definiowanie punktu końcowego usługi unikatowy|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Zdefiniować domyślne online/offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp — wprowadź `0` Określ pomocy lokalnej, a następnie wprowadź `1` do określenia pomocy online.|  
|Zdefiniuj unikatowe końcowy F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Zastąp priorytet zadania usługi BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na klawiaturze machine)\Microsoft\Help\v2.2 64-bitowych|BITSPriority — użyj jednej z następujących wartości: **pierwszego planu**, **wysokiej**, **normalne**, lub **niski**.|  
|Wyłącz w trybie Online (i opcji IDE w trybie Online)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na klawiaturze machine)\Microsoft\VisualStudio\14.0\Help 64-bitowych|OnlineHelpPreferenceDisabled — ustawiona na 1, aby wyłączyć dostęp do zawartości Pomocy online.|  
|Wyłącz zarządzanie zawartością|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na klawiaturze machine)\Microsoft\VisualStudio\14.0\Help 64-bitowych|ContentManagementDisabled — ustawiona na 1, aby wyłączyć **zarządzanie zawartością** karty w Podglądzie pomocy.|  
|Wskaż magazynu zawartości lokalnej w udziale sieciowym|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath=”*ContentStoreNetworkShare*”|  
|Wyłączyć możliwość instalacji zawartości przy pierwszym uruchomieniu funkcji programu Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na klawiaturze machine)\Microsoft\VisualStudio\14.0\Help 64-bitowych|DisableFirstRunHelpSelection — ustawiona na 1, aby wyłączyć funkcje pomocy, które są skonfigurowane przy pierwszym uruchomieniu programu Visual Studio.|  
  
## <a name="see-also"></a>Zobacz też  
 [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md)
