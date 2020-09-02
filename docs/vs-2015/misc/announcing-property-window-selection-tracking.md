---
title: Ogłaszanie zaznaczenia okna właściwości śledzenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002455"
---
# <a name="announcing-property-window-selection-tracking"></a>Ogłoszenie śledzenia wyboru okna właściwości
Jeśli chcesz korzystać z okna **Właściwości** lub stron **Właściwości** , na przykład formularza, tekstu lub zaznaczenia, dla którego chcesz wyświetlić właściwości, musisz mieć kompletną wiedzę na temat sposobu koordynowania wyboru. Na przykład musisz wiedzieć, czy masz pojedynczy wybór, czy wiele zaznaczeń. Następnie należy zaanonsować typ wyboru (jeden lub wiele) do IDE przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu. Ten interfejs zapewnia informacje wymagane przez okno **Właściwości** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Aby ogłosić zaznaczenie w środowisku  
  
1. Wywołaj metodę `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. W tym celu należy użyć wskaźnika witryny przesłanego do widoku podczas jego tworzenia.  
  
    2. Wywołaj `QueryService` z widoku dla `SID_STrackSelection` usługi.  
  
         Zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metodę za każdym razem, gdy wybór zostanie zmieniony, i przekaż wskaźnik do obiektu, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     Obiekt kontenera wyboru może korzystać z wybranych opcji pojedynczej lub wielu i zawiera informacje o zaznaczeniu w `IDispatch` obiekcie. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metody powiadamia okno **Właściwości** , że zaznaczenie zostało zmienione. W oknie **Właściwości** zostanie użyta funkcja obiekty na <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , aby określić, czy wystąpiły pojedyncze lub wiele wybranych opcji i jakie są rzeczywiste wybory obiektów.  
  
     Jeśli określisz wybór wielokrotny, okno **Właściwości** znajdzie wspólną część między typowymi właściwościami obiektów. Jeśli określisz pojedynczy wybór obiektów, w oknie **Właściwości** zostaną wyświetlone wszystkie właściwości jednego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)   
 [Strony właściwości](../extensibility/internals/property-pages.md)