---
title: Interfejs IDebugDocumentTextEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bec89ae81d79fb7b0d822cafe2bf44f0ecd8ad81
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345663"
---
# <a name="idebugdocumenttextevents-interface"></a>Interfejs IDebugDocumentTextEvents
Dostępne są zdarzenia wskazujące zmiany w dokumencie tekstu.  
  
> [!NOTE]
>  Zdarzenia dla tego interfejsu fire zmienia tekstu dokumentu. Programy obsługi zdarzeń może pobrać nowy tekst za pomocą `IDebugDocumentText` interfejsu.  
  
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