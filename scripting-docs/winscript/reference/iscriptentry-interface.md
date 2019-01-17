---
title: Interfejs IScriptEntry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9d7b33e2e5c90d5c489fe283575b4a2e45671f9a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349351"
---
# <a name="iscriptentry-interface"></a>Interfejs IScriptEntry
Obiekt, który implementuje `IScriptEntry` interfejs reprezentuje blok skryptu lub obiekt funkcyjny.  
  
 Oprócz metod odziedziczone `IScriptNode`, `IScriptEntry` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Zwraca tekst, który odnosi się do treści `IScriptEntry` blok skryptu, bloku funkcji lub scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Zwraca nazwę elementu, który identyfikuje `IScriptEntry` obiektu.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Wpisy, które reprezentują pojedynczy obiekt (na przykład funkcja) zwraca nazwę obiektu.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Zwraca pozycji początkowej i długości hasła.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Zwraca typ informacji dla `IScriptEntry` obiektu funkcyjnego.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Zwraca tekst, który odpowiada `IScriptEntry` blok skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` programu obsługi zdarzeń.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Ustawia tekst, który znajduje się w treści `IScriptEntry` blok skryptu albo `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Ustawia nazwę elementu, który identyfikuje `IScriptEntry` obiektu.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Wpisy, które reprezentują pojedynczy obiekt (na przykład funkcja) ustawia nazwę obiektu.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Ustawia typ informacji dla `IScriptEntry` obiektu funkcyjnego.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Ustawia tekst, który odpowiada `IScriptEntry` blok skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` programu obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)