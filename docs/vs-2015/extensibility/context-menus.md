---
title: Menu kontekstowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184266"
---
# <a name="context-menus"></a>Menu kontekstowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menu kontekstowe są wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy w aktywnym regionie obszaru klienta i wyczyści po zwolnieniu prawego przycisku myszy.  
  
## <a name="editor-context-menus"></a>Menu kontekstowe edytora  
 Dzięki przechwyceniu `ECMD_SHOWCONTEXTMENU` Usługa języka może kontrolować menu kontekstowe, które będą wyświetlane w edytorze. Aby wyświetlić własne menu kontekstowe, należy obsłużyć to polecenie, gdy zostanie ono przesłane do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> telefonu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Jeśli to polecenie nie jest obsługiwane, środowisko IDE wyświetla standardowe menu kontekstowe dostępne dla edytora. Można również kontrolować zawartość menu kontekstowego dla poszczególnych znaczników. Aby uzyskać więcej informacji na ten temat, zobacz [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md) i [przechwycenie starszych poleceń usługi językowej](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
