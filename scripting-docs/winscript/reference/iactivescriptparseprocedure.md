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
ms.openlocfilehash: 3567a22eac2ad270739e62e0f0fb9914bdf4a9ec
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144574"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Jeśli aparat skryptów systemu Windows umożliwia dodanie tekstu kodu źródłowego do skryptu, implementuje `IActiveScriptParseProcedure` interfejs. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska projektowego, takiego jak VBScript, zapewnia alternatywny mechanizm (inny niż `IActiveScriptParse` lub `IPersist` *), aby dodać procedury skryptu do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|
|-|-|
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)