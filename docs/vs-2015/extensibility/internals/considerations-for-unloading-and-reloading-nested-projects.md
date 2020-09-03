---
title: Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197013"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas implementowania zagnieżdżonych typów projektów należy wykonać dodatkowe czynności podczas zwalniania i ponownego ładowania projektów. Aby poprawnie powiadomić odbiorniki do zdarzeń rozwiązania, należy prawidłowo podnieść `OnBeforeUnloadProject` `OnAfterLoadProject` zdarzenia i.  
  
 Jedną z przyczyn, należy zgłosić te zdarzenia w ten sposób, że nie chcesz, aby kontrola kodu źródłowego (SCC) mogła usunąć elementy z serwera, a następnie dodać je ponownie jako nowe, jeśli istnieje jakaś `Get` operacja z SCC. W takim przypadku nowy plik zostanie załadowany z SCC i konieczne będzie zwolnienie i ponowne załadowanie wszystkich plików w przypadku, gdy są one różne. Wywołania SCC `ReloadItem` . Twoja implementacja tego wywołania polega na usunięciu projektu i ponownym utworzeniu go przez implementację `IVsFireSolutionEvents` w celu wywołania `OnBeforeUnloadProject` i `OnAfterLoadProject` . Podczas wykonywania tej implementacji SCC zostanie poinformowany o tym, że projekt został tymczasowo usunięty i ponownie dodany. W związku z tym SCC nie działa w projekcie tak, jakby projekt został rzeczywiście usunięty z serwera, a następnie ponownie dodany.  
  
## <a name="reloading-projects"></a>Ponowne ładowanie projektów  
 Aby obsługiwać ponowne ładowanie zagnieżdżonych projektów, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodę. W implementacji programu `ReloadItem` można zamknąć zagnieżdżone projekty, a następnie utworzyć je ponownie.  
  
 Zwykle po ponownym załadowaniu projektu środowisko IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> i `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` zdarzenia. Jednak w przypadku projektów zagnieżdżonych, które zostaną usunięte i ponownie załadowane, projekt nadrzędny inicjuje proces, a nie IDE. Ponieważ projekt nadrzędny nie zgłasza zdarzeń rozwiązania, a IDE nie ma informacji o inicjalizacji procesu, zdarzenia nie są wywoływane.  
  
 Aby obsłużyć ten proces, projekt nadrzędny wywołuje interfejs `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> poza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfejsem. `IVsFireSolutionEvents` Program zawiera funkcje, które informują IDE o podniesieniu `OnBeforeUnloadProject` zdarzenia w celu zwolnienia projektu zagnieżdżonego, a następnie podniesienia `OnAfterLoadProject` zdarzenia w celu ponownego załadowania tego samego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
