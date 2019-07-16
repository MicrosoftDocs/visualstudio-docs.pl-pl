---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197938"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kończenie znajdujących się w pliku dziennika grafiki, a następnie zamyka i zwalnia zasoby, które były używane podczas, gdy aplikacja została aktywnie rejestrowanie informacji graficznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Uwagi  
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasa jest niszczona. Jeśli `VsgDbg` wystąpienia nie została aktywnie rejestrowanie informacji graficznych, nie ma to wpływu.  
  
 Po `UnInit` została wywołana w wystąpieniu `VsgDbg` klasy grafiki nowy plik dziennika można utworzyć przez wywołanie metody `Init` i opracowane przez wywołanie `UnInit`. To można powtarzać dowolną liczbę razy używać tego samego `VsgDbg` wystąpienia, aby utworzyć kilka niezależnych grafiki pliki dziennika.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](../debugger/init.md)
