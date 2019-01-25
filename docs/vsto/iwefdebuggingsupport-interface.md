---
title: IWefDebuggingSupport, interfejs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55a09c3db9a47b5bcf22a7faeb891a1f709d244a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865687"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport, interfejs
  Implementowany przez środowisko debugowania, takich jak Visual Studio, aby ułatwić debugowanie aplikacji dla pakietu Office. Aplikacji pakietu Office, takich jak Word lub Excel, uzyskuje dostęp do tego interfejsu z programu Visual Studio, a następnie wywołuje metody interfejsu w niektórych punktach podczas sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Metody  
 Poniższa tabela zawiera listę metod, które definiuje IWefDebuggingSupport, interfejs.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[GetAutoInsertExtensions, metoda](../vsto/getautoinsertextensions-method.md)|Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.|  
|[SetWefProcessId, metoda](../vsto/setwefprocessid-method.md)|Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).|  
