---
title: Interfejs IScriptScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571887"
---
# <a name="iscriptscriptlet-interface"></a>Interfejs IScriptScriptlet
Obiekt implementujący interfejs `IScriptScriptlet` reprezentuje skrypt procedury obsługi zdarzeń.  
  
 Oprócz metod dziedziczonych z `IScriptEntry` interfejs `IScriptScriptlet` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Zwraca nazwę zdarzenia skojarzonego z Scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Zwraca prostą nazwę zdarzenia skojarzoną z Scriptlet. Jest to nazwa jednowyrazowa, która nie zawiera żadnych białych znaków.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Zwraca ostatni identyfikator w w pełni kwalifikowanej nazwie hosta obiektów Scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Ustawia nazwę zdarzenia skojarzonego z Scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Ustawia prostą nazwę zdarzenia skojarzoną z Scriptlet. Jest to nazwa jednowyrazowa, która nie zawiera żadnych białych znaków.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Ustawia ostatni identyfikator w w pełni kwalifikowanej nazwie hosta obiektów Scriptlet.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)