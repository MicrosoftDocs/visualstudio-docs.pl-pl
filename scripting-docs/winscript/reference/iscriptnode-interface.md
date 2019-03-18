---
title: Interfejs IScriptNode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13bf20f9e1e642b948ddaa72ae9dca7bb457fba2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155842"
---
# <a name="iscriptnode-interface"></a>Interfejs IScriptNode
Obiekt, który implementuje `IScriptNode` interfejs reprezentuje stronę sieci Web.  
  
 Oprócz metod odziedziczone `IUnknown`, `IScriptNode` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Wskazuje, czy obiekt jest nadal aktywne.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Dodaje wystąpienie podrzędnych `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Dodaje scriptlet jako wystąpienie podrzędnych `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Usuwa drzewa obiektów.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Zwraca element podrzędny, który jest umieszczony pod określonym indeksem w węźle.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Zwraca wartość zdefiniowanych przez aplikację, używanego do kojarzenia scriptlet za pomocą obiektu hosta.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Zwraca indeks obiektu w liście elementów podrzędnych elementu nadrzędnego.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Zwraca język skryptów, używany przez bieżącego węzła skryptu.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Zwraca liczbę węzłów podrzędnych `IScriptNode` obiektu.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Zwraca `IScriptNode` obiektu, który jest elementem nadrzędnym obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)