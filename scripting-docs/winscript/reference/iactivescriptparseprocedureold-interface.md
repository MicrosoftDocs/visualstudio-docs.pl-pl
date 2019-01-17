---
title: IActiveScriptParseProcedureOld Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349998"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfejs IActiveScriptParseProcedureOld
Umożliwia tekstu kodu źródłowego dla procedur, które mają zostać dodane do skryptu. Dla interpretowanych języków skryptów, które nie mają niezależne środowisko tworzenia, np. VBScript, zapewnia to alternatywny mechanizm (inne niż `IActiveScriptParse` lub `IPersist*`) aby dodać skrypt procedury do przestrzeni nazw.  
  
> [!NOTE]
>  Ten interfejs jest przestarzała zastąpiona ceną `IActiveScriptParseProcedure` interfejsu.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IActiveScriptParseProcedureOld` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizuje procedury danego kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)