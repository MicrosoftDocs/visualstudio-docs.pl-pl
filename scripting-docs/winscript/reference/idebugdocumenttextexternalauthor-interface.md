---
title: Interfejs IDebugDocumentTextExternalAuthor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor interface
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fb0d68d8052990fcc1783f86d0213b714dbfc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978488"
---
# <a name="idebugdocumenttextexternalauthor-interface"></a>Interfejs IDebugDocumentTextExternalAuthor
Zezwala na zewnętrzne edytory bezpiecznie edytować dokumentów opartych na plikach debugera, informując o tym dokumencie, po zmianie pliku źródłowego.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugDocumentTextExternalAuthor` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|Zwraca pełną ścieżkę i nazwę dokumentu.|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|Zwraca nazwę dokumentu bez informacji o ścieżce.|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|Powiadamia hosta, że dokument źródłowy został zmieniony.|