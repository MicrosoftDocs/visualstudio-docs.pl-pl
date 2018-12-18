---
title: Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów | Dokumentacja firmy Microsoft
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
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28c5ba7dffecd73556a5f963c471910bb190f1db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756974"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas implementowania typów zagnieżdżonych projektów, można wykonać dodatkowe kroki, jeśli zwolnisz i ponownie Załaduj projekty. Poprawnie o rozwiązaniu zdarzenia, należy poprawnie zgłosić `OnBeforeUnloadProject` i `OnAfterLoadProject` zdarzenia.  
  
 Jednym z powodów trzeba zwiększyć te zdarzenia w ten sposób jest zrezygnować kontroli kodu źródłowego (SCC), aby usunąć elementy z serwera, a następnie dodać je jako coś nowego w przypadku `Get` SCC podczas operacji. W takim przypadku nowy plik, które będą ładowane poza SCC i trzeba zwolnić i załaduj ponownie wszystkie pliki w przypadku, gdy są one różne. Wywołania SCC `ReloadItem`. Implementacja to wywołanie jest do usunięcia projektu, a następnie ponownie go utworzyć ponownie przez zaimplementowanie `IVsFireSolutionEvents` do wywołania `OnBeforeUnloadProject` i `OnAfterLoadProject`. Podczas wykonywania tej implementacji SCC jest informowany, projekt został czasowo usunięty i ponownie dodać. W związku z tym SCC nie będzie działać w projekcie, tak, jakby rzeczywiście zostały usunięte z serwera i ponownie dodać projektu.  
  
## <a name="reloading-projects"></a>Ponownego ładowania projektów  
 Aby zapewnić obsługę ponownego ładowania zagnieżdżonych projektów, możesz wdrożyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. W danej implementacji `ReloadItem`, zamknij zagnieżdżonych projektów, a następnie ponownie utwórz je.  
  
 Zwykle po załadowaniu projektu, IDE zgłasza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> i `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` zdarzenia. Dla zagnieżdżonych projektów, które zostanie usunięty i ponownie załadować projekt nadrzędny inicjuje proces nie środowiska IDE. Ponieważ projekt nadrzędny nie zgłaszać zdarzenia rozwiązania i środowiska IDE nie ma informacji o inicjowania procesu, zdarzenia nie są zgłaszane.  
  
 Aby obsługiwać ten proces nadrzędny wywoływanych w projekcie `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfejsu poza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfejsu. `IVsFireSolutionEvents` dostępne są funkcje, pasujących do środowiska IDE, aby podnieść `OnBeforeUnloadProject` zdarzeń można zwolnić projektu zagnieżdżonego, a następnie podnieś `OnAfterLoadProject` zdarzenie, aby ponownie załadować projekt.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)

