---
title: IActiveScriptParseProcedureOld Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160631"
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