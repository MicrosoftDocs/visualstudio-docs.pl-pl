---
title: 'Instrukcje: Wyczyścić stosu cofania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d6e7c2536b7c5556139ce7a9b56756e20fd3648
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072867"
---
# <a name="how-to-clear-the-undo-stack"></a>Instrukcje: Wyczyścić stosu cofania
Następujące Poniższa procedura wyjaśnia, jak wyczyścić stosu cofania.

## <a name="to-clear-the-undo-stack"></a>Aby wyczyścić stosu cofania

1. Aby wyczyścić wykorzystanie stosu cofania [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) metody. Oto przykład:

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

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Implementowanie cofania zarządzania](../extensibility/how-to-implement-undo-management.md)