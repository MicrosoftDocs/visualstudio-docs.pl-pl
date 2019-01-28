---
title: 'Instrukcje: Wyczyścić stosu cofania | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: e45ec665b75be99781495bc5f2407c30c5f7e12a
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2019
ms.locfileid: "55089162"
---
# <a name="how-to-clear-the-undo-stack"></a>Instrukcje: Wyczyścić stosu cofania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące Poniższa procedura wyjaśnia, jak wyczyścić stosu cofania.  
  
### <a name="to-clear-the-undo-stack"></a>Aby wyczyścić stosu cofania  
  
1.  Aby wyczyścić wykorzystanie stosu cofania [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) metody. Oto przykład:  
  
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
 [Instrukcje: Implementowanie cofania zarządzania](../extensibility/how-to-implement-undo-management.md)
