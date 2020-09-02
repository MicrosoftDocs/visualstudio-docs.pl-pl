---
title: Odinicjuj inicjowanie | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197938"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kończy plik dziennika grafiki, zamyka go i zwalnia zasoby, które były używane podczas aktywnie rejestrowania informacji graficznych przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Uwagi  
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasy zostanie zniszczone. Jeśli `VsgDbg` wystąpienie nie było aktywnie rejestrować informacji graficznych, nie ma to wpływu.  
  
 Po `UnInit` wywołaniu w wystąpieniu `VsgDbg` klasy nowy plik dziennika grafiki można utworzyć, wywołując `Init` i finaljąc wywołując metodę `UnInit` . Możesz powtórzyć tyle razy, ile chcesz używać tego samego `VsgDbg` wystąpienia do tworzenia kilku niezależnych plików dziennika grafiki.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](../debugger/init.md)
