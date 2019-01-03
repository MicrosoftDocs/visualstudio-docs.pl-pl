---
title: Kopiowanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aab2b18c8c349211f4b5bd26b055d6ee5b65f0c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990951"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
Kopiuje zawartość active grafiki (.vsglog) pliku do nowego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szNewVSGLog`  
 Nazwa pliku nowy plik dziennika grafiki.  
  
## <a name="remarks"></a>Uwagi  
 Aby skopiować informacje graficzne do nowego pliku, muszą już udało się przechwycić pewne informacje grafiki; w przeciwnym razie nic się nie dzieje.