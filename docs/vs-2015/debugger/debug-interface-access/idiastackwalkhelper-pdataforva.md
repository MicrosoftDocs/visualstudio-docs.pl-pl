---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150089"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca blok danych PDATA skojarzony z adresem wirtualnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 podczas Określa adres wirtualny danych do uzyskania.  
  
 `cbData`  
 podczas Rozmiar danych w bajtach do uzyskania.  
  
 `pcbData`  
 określoną Zwraca rzeczywisty rozmiar danych uzyskanych w bajtach.  
  
 `pbData`  
 [in. out] Bufor, który jest wypełniony danymi żądanymi. Nie może być `NULL` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy dla podanego adresu nie ma pdata. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 PDATA (sekcja o nazwie ". pdata") jednostka kompilacji zawiera informacje o obsłudze wyjątków dla funkcji.  
  
 Obiekt wywołujący wie, ile danych ma zostać zwróconych, aby obiekt wywołujący nie musiał żądać ilości dostępnych danych. W związku z tym jest akceptowalny dla implementacji tej metody w celu zwrócenia błędu, jeśli `pbData` parametr ma wartość `NULL` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
