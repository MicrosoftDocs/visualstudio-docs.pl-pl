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
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561638"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Jeśli aparat skryptów systemu Windows umożliwia dodanie do skryptu niesformatowanego kodu tekstu skryptlety lub zezwala na ocenę tekstu wyrażenia w czasie wykonywania, implementuje interfejs `IActiveScriptParse`. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska autorskiego, takiego jak VBScript, zapewnia on alternatywny mechanizm (inny niż `IPersist*`), aby uzyskać kod skryptu do aparatu skryptów i dołączyć fragmenty skryptów do różnych zdarzeń obiektów .  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicjuje aparat skryptów.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Dodaje kod Scriptlet do skryptu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizuje daną Scriptlet kodu, dodając deklaracje do przestrzeni nazw i oceniając kod zgodnie z potrzebami.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)