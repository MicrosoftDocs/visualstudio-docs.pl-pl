---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f36da19e6bc47d70010dd96a26256537803ccb29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551621"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs wylicza konteksty kodu skojarzone z sesją debugowania lub z określonym programem lub dokumentem.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować listę kontekstów kodu dla konkretnej pozycji tekstu w programie lub listę kontekstów kodu dla danego kontekstu dokumentu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) , aby uzyskać ten interfejs reprezentujący listę kontekstów kodu dla określonej pozycji tekstu w dokumencie źródłowym programu.  
  
 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) , aby uzyskać ten interfejs reprezentujący listę wszystkich kontekstów kodu w określonym dokumencie źródłowym.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IEnumDebugCodeContexts2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Pobiera określoną liczbę kontekstów kodu w sekwencji wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Pomija określoną liczbę kontekstów kodu w sekwencji wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Pobiera liczbę kontekstów kodu w module wyliczającym.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio wywołuje [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) , aby wypełnić listę kontekstów kodu, z których użytkownik może wybrać podczas ustawiania następnej instrukcji lub pokazywania oddzielenia pliku źródłowego. Może wystąpić wiele kontekstów kodu, na przykład gdy istnieje wiele wystąpień szablonu w stylu języka C++.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
