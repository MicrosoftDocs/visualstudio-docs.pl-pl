---
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83170c72eeabaae2ac193e47ddc91e1ec1e54046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695421"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs określa komunikat o błędzie, który ma zostać zgłoszony użytkownikowi.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby raportować błędy w miarę czytelnych wiadomości. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Po utworzeniu i wysłaniu tego obiektu zdarzenia w celu zgłoszenia błędu. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|`GetErrorMessage`|Zwraca błąd jako ciąg czytelny dla człowieka.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat debugowania napotka błąd, może użyć tego interfejsu, aby zgłosić komunikat za pomocą programu Visual Studio do użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
