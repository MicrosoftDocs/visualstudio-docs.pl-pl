---
title: Właściwość SCRIPTPROP_HOSTKEEPALIVE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c8918e277fa9c7183e6d46a4853824a74fa4548
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087376"
---
# <a name="scriptprophostkeepalive-property"></a>Właściwość SCRIPTPROP_HOSTKEEPALIVE
Służy do określania, czy aparat skryptów powinny być przechowywane w pełni funkcjonalne, w przypadku innych odwołań.  
  
 Użyj [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) można ustawić tę właściwość na `true`. Jeśli ta właściwość jest ustawiona `true`, aparat skryptów są przechowywane w pełni funkcjonalne, tak długo, jak istnieje co najmniej jedno odwołanie oczekujących do silnika wykonywania skryptów, samego lub `IDispatch` wskaźnika do obiektu JavaScript utworzone za pomocą skryptów aparat. Jeśli ta właściwość jest równa `true`, należy nie zostały jawnie Zamknij lub zresetuj aparat skryptu przy użyciu [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) lub [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metody. Wydanie to ostatnie odwołanie do obiektu skryptu zamyka aparat skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Wymagania  
 Właściwość ta pojawia się tylko w wersji activscp.idl, który został zainstalowany przy użyciu [!INCLUDE[win8](../../javascript/includes/win8-md.md)], za pomocą 2707082 KB programu Internet Explorer 8, na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], lub za pomocą 2722913 KB dla programu Internet Explorer 9 na [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] lub [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].