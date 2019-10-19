---
title: Interfejs IActiveScriptParseProcedureOld | Microsoft Docs
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
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571428"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfejs IActiveScriptParseProcedureOld
Umożliwia dodanie tekstu kodu źródłowego do skryptu. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska projektowego, takiego jak VBScript, zapewnia alternatywny mechanizm (inny niż `IActiveScriptParse` lub `IPersist*`), aby dodać procedury skryptu do przestrzeni nazw.  
  
> [!NOTE]
> Ten interfejs jest przestarzały na korzyść interfejsu `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Metody  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `IActiveScriptParseProcedureOld` udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)