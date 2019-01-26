---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48c4e76105c024f9f414a884c2e3cabde716db86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019112"
---
# <a name="uninit"></a>UnInit
Kończenie znajdujących się w pliku dziennika grafiki, a następnie zamyka i zwalnia zasoby, które były używane podczas, gdy aplikacja została aktywnie rejestrowanie informacji graficznych.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Uwagi  
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasa jest niszczona. Jeśli `VsgDbg` wystąpienia nie została aktywnie rejestrowanie informacji graficznych, nie ma to wpływu.  
  
 Po `UnInit` została wywołana w wystąpieniu `VsgDbg` klasy grafiki nowy plik dziennika można utworzyć przez wywołanie metody `Init` i opracowane przez wywołanie `UnInit`. To można powtarzać dowolną liczbę razy używać tego samego `VsgDbg` wystąpienia, aby utworzyć kilka niezależnych grafiki pliki dziennika.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](init.md)