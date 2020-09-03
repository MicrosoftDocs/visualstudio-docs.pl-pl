---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1f30c3a465d4803e5c91f14ee45ad582e76d986
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200216"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje pozycję w pliku źródłowym jako przesunięcie znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Zaimplementowane przez środowisko IDE i używane przez aparaty debugowania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugDocumentPositionOffset2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Pobiera zakres dla bieżącego położenia dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca te same informacje jak [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , ale w `char` przesunięciach od początku dokumentu. Przedstawia to dokument, taki jak na dysku, czyli tablicę jednowymiarową znaków, zamiast informacji o wierszu i kolumnie, które są zwykle zwracane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
