---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561670"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Jeśli aparat skryptów systemu Windows umożliwia dodanie tekstu kodu źródłowego do skryptu, implementuje interfejs `IActiveScriptParseProcedure`. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska projektowego, takiego jak VBScript, zapewnia on alternatywny mechanizm (inny niż `IActiveScriptParse` lub `IPersist` *), aby dodać procedury skryptu do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)