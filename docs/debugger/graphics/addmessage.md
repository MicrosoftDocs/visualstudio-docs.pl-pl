---
title: AddMessage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aa23265c2f0d8d006d53faf575e2ea608c071d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027532"
---
# <a name="addmessage"></a>AddMessage
Dodaje niestandardowy komunikat do diagnostyki grafiki *HUD* (wyświetlanie Head-Up).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szMessage`  
 Komunikat, który ma zostać dodany do HUD.  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona w ramach diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie tej funkcji.  
  
 Aby dodać komunikat HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — oznacza to, że można dodać komunikat za pośrednictwem wystąpienia `VsgDbg` klasy, ale [Init](init.md) funkcji składowej nie jest wywoływany jako pierwszy. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.