---
title: Interfejs IScriptNode | Microsoft Docs
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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577516"
---
# <a name="iscriptnode-interface"></a>Interfejs IScriptNode
Obiekt implementujący interfejs `IScriptNode` reprezentuje stronę sieci Web.  
  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `IScriptNode` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Wskazuje, czy obiekt jest nadal aktywny.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Dodaje wystąpienie podrzędne `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Dodaje Scriptlet jako wystąpienie podrzędne `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Usuwa drzewo obiektów.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Zwraca element podrzędny, który znajduje się w określonym indeksie w węźle.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Zwraca wartość zdefiniowaną przez aplikację, która jest używana do kojarzenia Scriptlet z obiektem hosta.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Zwraca indeks obiektu znajdującego się na liście elementów podrzędnych elementu nadrzędnego.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Zwraca język skryptów używany przez bieżący węzeł skryptu.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Zwraca liczbę węzłów podrzędnych obiektu `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Zwraca obiekt `IScriptNode`, który jest elementem nadrzędnym obiektu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)