---
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97494f2180d0aede2dfd8e1a539a0d957f9a0bcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150079"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia wartość rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 podczas Wartość z wyliczenia [CV_HREG_e wyliczeniem](../../debugger/debug-interface-access/cv-hreg-e.md) określająca rejestrację, w której ma zostać zapisany.  
  
 `NewVal`  
 podczas Nowa wartość rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Pomimo rozmiaru wartości implementacja powinna przechowywać tylko te dane, które są zwykle przechowywane w rejestrze. Na przykład rejestr 8-bitowy będzie zawierał tylko najmniejsze 8 bitów danej wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)
