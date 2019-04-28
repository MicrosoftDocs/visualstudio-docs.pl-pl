---
title: Interfejs IDebugDocumentTextEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c83a6e3a41ed7087338989d5cb077fa070e724b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434264"
---
# <a name="idebugdocumenttextevents-interface"></a>Interfejs IDebugDocumentTextEvents
Dostępne są zdarzenia wskazujące zmiany w dokumencie tekstu.  
  
> [!NOTE]
> Zdarzenia dla tego interfejsu fire zmienia tekstu dokumentu. Programy obsługi zdarzeń może pobrać nowy tekst za pomocą `IDebugDocumentText` interfejsu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugDocumentTextEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Wskazuje, że podstawowy dokument został zniszczony i nie jest już prawidłowy|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Wskazuje, czy nowy tekst został dodany do dokumentu|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Wskazuje, czy tekst został usunięty z dokumentu.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Wskazuje, czy tekst został zastąpiony.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Wskazuje, że atrybuty tekstu skojarzonych z zakresem pozycji podstawowego znak zostały zmienione.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Wskazuje, że zmienione atrybuty dokumentu.|