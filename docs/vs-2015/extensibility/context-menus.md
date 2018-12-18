---
title: Menu kontekstowe | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efd4e1c80b9af2a0d73730f0bd7d741cd877fb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796847"
---
# <a name="context-menus"></a>Menu kontekstowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menu kontekstowe są wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy aktywny region obszaru klienta i usuń zaznaczenie po zwolnieniu prawego przycisku myszy.  
  
## <a name="editor-context-menus"></a>Menu kontekstowe edytora  
 Przechwycenie `ECMD_SHOWCONTEXTMENU`, usługi w języka można kontrolować menu kontekstowe, które będą wyświetlane w edytorze. Aby wyświetlić menu kontekstowe, obsługi tego polecenia, gdy jest przekazywany do usługi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Jeśli nie obsługuje tego polecenia, IDE Wyświetla standardowe menu kontekstowe podane dla edytora. Można także kontrolować zawartość elementu menu kontekstowego na podstawie poszczególnych znacznika. Aby uzyskać więcej informacji na ten temat, zobacz [przy użyciu znaczników tekstu przy użyciu interfejsu API starszych](../extensibility/using-text-markers-with-the-legacy-api.md) i [poleceń usługi języka Legacy przechwytuje](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)

