---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a987b4be3430f2ed8b0562f41b51a94797f96dc4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152187"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Jeśli skrypt Windows aparat pozwala nieprzetworzony tekst skryptlety kodu do dodania do skryptu lub zezwala na tekst wyrażenie oceniane w czasie wykonywania, implementuje `IActiveScriptParse` interfejsu. Dla interpretowanych języków skryptów, które mają nie niezależnych środowisko tworzenia, np. VBScript, zapewnia to alternatywny mechanizm (inne niż `IPersist*`) pobierać kod skryptu do silnika wykonywania skryptów i Dołącz fragmenty skryptu do różnych obiektów zdarzenia.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicjuje aparat skryptów.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Dodaje skryptletu kodu do skryptu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizuje danego skryptletu kodu, dodając deklaracje do przestrzeni nazw i oceniając kod, zgodnie z potrzebami.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)