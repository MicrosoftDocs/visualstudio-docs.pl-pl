---
title: 'Instrukcje: czyszczenie stosu cofania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db77f93fd7f6af16b5358b75b6ffcd5927430653
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549172"
---
# <a name="how-to-clear-the-undo-stack"></a>Instrukcje: czyszczenie stosu cofania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższa procedura wyjaśnia, jak wyczyścić stos cofania.  
  
### <a name="to-clear-the-undo-stack"></a>Aby wyczyścić stos cofania  
  
1. Aby wyczyścić stos cofania, użyj metody [IOleUndoManager::D iscardfrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) . Poniżej znajduje się przykład:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: implementowanie zarządzania cofaniem](../extensibility/how-to-implement-undo-management.md)
