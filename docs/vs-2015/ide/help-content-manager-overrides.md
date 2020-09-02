---
title: Przesłonięcia Menedżera zawartości pomocy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70c0044a0436dcf27a3b087b3f11a5f759824735
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645562"
---
# <a name="help-content-manager-overrides"></a>Przesłonięcia Menedżera zawartości Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zmodyfikować rejestr, aby zmienić domyślne zachowanie podglądu pomocy i funkcji związanych z pomocą w środowisku IDE programu Visual Studio.

|Zadanie|Klucz rejestru|Wartość i definicja|
|----------|------------------|--------------------------|
|Zdefiniuj unikatowy punkt końcowy usługi|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|
|Definiowanie domyślnego trybu online/offline|HKEY_LOCAL_MACHINE \Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp — wprowadź `0` , aby określić pomoc lokalną, i wprowadź, `1` Aby określić pomoc online.|
|Zdefiniuj unikatowy punkt końcowy F1|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl —*HTTPValueForTheServiceEndpoint*|
|Zastąp priorytet zadania usługi BITS|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (na komputerze 64-bitowym) \Microsoft\Help\v2.2|BITSPriority — Użyj jednej z następujących wartości: **pierwszy plan**, **wysoki**, **normalny**lub **niski**.|
|Wyłącz tryb online (i opcję IDE online)|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (na komputerze 64-bitowym) \Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--ustaw wartość 1, aby wyłączyć dostęp do zawartości pomocy online.|
|Wyłącz zarządzanie zawartością|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (na komputerze 64-bitowym) \Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--ustaw wartość 1, aby wyłączyć kartę **Zarządzaj zawartością** w podglądzie pomocy.|
|Wskaż lokalny magazyn zawartości w udziale sieciowym|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath = "*ContentStoreNetworkShare*"|
|Wyłącz instalację zawartości przy pierwszym uruchomieniu funkcji programu Visual Studio.|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (na komputerze 64-bitowym) \Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--ustaw wartość 1, aby wyłączyć funkcje pomocy, które są konfigurowane podczas pierwszego uruchomienia programu Visual Studio.|

## <a name="see-also"></a>Zobacz też
 [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md)
