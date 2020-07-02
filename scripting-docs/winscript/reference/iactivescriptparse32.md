---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835319"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Jeśli aparat skryptów systemu Windows zezwala na dodanie nieprzetworzonego kodu tekstu skryptlety do skryptu lub zezwala na ocenę tekstu wyrażenia w czasie wykonywania, implementuje `IActiveScriptParse32` interfejs. W przypadku interpretowanych języków skryptów, które nie mają niezależnego środowiska autorskiego, takiego jak VBScript, zapewnia on alternatywny mechanizm (inny niż `IPersist*` ) do pobierania kodu skryptu do aparatu skryptów i dołączania fragmentów skryptów do różnych zdarzeń obiektów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Dodaje kod Scriptlet do skryptu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicjuje aparat skryptów.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizuje daną Scriptlet kodu, dodając deklaracje do przestrzeni nazw i oceniając kod zgodnie z potrzebami.|