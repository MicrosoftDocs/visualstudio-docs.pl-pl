---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 16d432b6c150b53fdd059a48cc683d240bd1a50a
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835306"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Jeśli aparat skryptów systemu Windows umożliwia dodanie tekstu kodu źródłowego do skryptu, implementuje `IActiveScriptParseProcedure32` interfejs. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska projektowego, takiego jak VBScript, zapewnia alternatywny mechanizm (inny niż `IActiveScriptParse32` lub `IPersist` *), aby dodać procedury skryptu do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)