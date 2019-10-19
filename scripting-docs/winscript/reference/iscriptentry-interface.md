---
title: Interfejs IScriptEntry | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575394"
---
# <a name="iscriptentry-interface"></a>Interfejs IScriptEntry
Obiekt implementujący interfejs `IScriptEntry` reprezentuje blok skryptu lub obiekt funkcji.  
  
 Oprócz metod dziedziczonych z `IScriptNode` interfejs `IScriptEntry` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Zwraca tekst, który odpowiada treści bloku skryptu `IScriptEntry`, bloku funkcji lub Scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Zwraca nazwę elementu, który identyfikuje obiekt `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|W przypadku wpisów reprezentujących pojedynczy obiekt (na przykład funkcja) zwraca nazwę obiektu.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Zwraca pozycję początkową i długość wpisu.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Zwraca informacje o typie dla obiektu funkcji `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Zwraca tekst, który odnosi się do bloku skryptu `IScriptEntry` lub kod źródłowy, który jest zawarty w `IScriptScriptlet` obsługi zdarzeń.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Ustawia tekst, który znajduje się w treści bloku skryptu `IScriptEntry` lub `IScriptScriptlet` Scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Ustawia nazwę elementu, który identyfikuje obiekt `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Dla wpisów reprezentujących pojedynczy obiekt (na przykład funkcja) ustawia nazwę obiektu.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Ustawia informacje o typie dla obiektu funkcji `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Ustawia tekst, który odpowiada blokowi skryptu `IScriptEntry` lub kod źródłowy, który jest zawarty w `IScriptScriptlet` obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)