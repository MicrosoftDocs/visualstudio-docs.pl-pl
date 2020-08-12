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
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144392"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Jeśli aparat skryptów systemu Windows umożliwia dodanie tekstu kodu źródłowego do skryptu, implementuje `IActiveScriptParseProcedure32` interfejs. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska projektowego, takiego jak VBScript, zapewnia alternatywny mechanizm (inny niż `IActiveScriptParse32` lub `IPersist` *), aby dodać procedury skryptu do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)