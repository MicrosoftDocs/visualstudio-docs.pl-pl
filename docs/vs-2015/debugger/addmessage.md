---
title: AddMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f01d4e80c3740ae27b5df8badbc74989c2da2c60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156512"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodaje niestandardowy komunikat do *HUD* diagnostyki grafiki (wyświetlacz podręczny).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szMessage`  
 Komunikat, który ma zostać dodany do HUD.  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlana w lewym górnym rogu aplikacji, która jest uruchamiana w obszarze Diagnostyka grafiki. Są w nim wyświetlane informacje o aplikacji i informacje o grafice i komunikaty dodawane przez wywołanie tej funkcji.  
  
 Aby dodać komunikat do HUD, nie musisz aktywnie przechwytywać informacji graficznych — to znaczy, że komunikat można dodać za pomocą wystąpienia `VsgDbg` klasy, ale funkcja [init](../debugger/init.md) member nie jest wywoływana jako pierwsza. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.
