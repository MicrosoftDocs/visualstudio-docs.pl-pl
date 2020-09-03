---
title: Kopiowanie (przechwycenie programowe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161511"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kopiuje zawartość aktywnego pliku dziennika grafiki (. vsglog) do nowego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szNewVSGLog`  
 Nazwa pliku nowego pliku dziennika grafiki.  
  
## <a name="remarks"></a>Uwagi  
 Aby skopiować informacje graficzne do nowego pliku, należy wcześniej przechwycić niektóre informacje graficzne; w przeciwnym razie nic się nie dzieje.
