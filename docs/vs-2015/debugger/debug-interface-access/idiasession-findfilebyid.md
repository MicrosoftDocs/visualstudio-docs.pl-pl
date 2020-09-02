---
title: 'IDiaSession:: findFileById | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c57072d4b8707136f0ccd2a759bc3d393720efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150438"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera plik źródłowy według identyfikatora pliku źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uniqueId`  
 podczas Określa identyfikator pliku źródłowego.  
  
 `ppResult`  
 określoną Zwraca obiekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , który reprezentuje pobrany plik źródłowy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Identyfikator pliku źródłowego jest unikatową wartością używaną wewnętrznie do DIA SDK, aby wszystkie pliki źródłowe były unikatowe. Ta metoda jest zwykle używana wewnętrznie w DIA SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession:: FindFile —](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
