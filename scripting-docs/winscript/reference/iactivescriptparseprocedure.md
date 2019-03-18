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
ms.openlocfilehash: 5ed07ce5ed48abfb377dde5fc4d5dc128d881b4a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151352"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Jeśli aparat skryptu Windows umożliwia tekstu kodu źródłowego dla procedur, które mają zostać dodane do skryptu, implementuje `IActiveScriptParseProcedure` interfejsu. Dla interpretowanych języków skryptów, które mają nie niezależnych środowisko tworzenia, np. VBScript, zapewnia to alternatywny mechanizm (inne niż `IActiveScriptParse` lub `IPersist`*) można dodać skrypt procedury do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizuje procedury danego kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)