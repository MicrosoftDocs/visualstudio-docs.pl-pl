---
title: Init | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185844"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przygotowuje składnik aplikacji diagnostyki grafiki do aktywnego przechwytywania i rejestrowania informacji graficznych w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vsgLogGetter`  
 Wywoływana jednostka — taka jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcji — który przyjmuje jako parametry długość buforu składającego się z `wchar_t` i wskaźnik do tego buforu i zwraca wartość `void` . Gdy wywoływana jednostka określa nazwę pliku, który będzie używany do rejestrowania informacji graficznych, i zapisuje je do określonego buforu przed zwróceniem.  
  
## <a name="remarks"></a>Uwagi  
 `Init`Funkcja jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasy jest konstruowane przez określenie `bDefaultInit` parametru jego konstruktora jako `true` ; w przeciwnym razie, `Init` musi zostać wywołane jawnie przed rozpoczęciem aktywnego przechwytywania i rejestrowania informacji graficznych.  
  
 Możesz zakończyć i zamknąć aktywny plik dziennika grafiki `UnInit` , wywołując, a następnie Przechwyć i Zapisz więcej informacji graficznych do nowego pliku dziennika grafiki, wywołując `Init` ponownie. Można powtórzyć tyle razy, ile chcesz utworzyć kilka niezależnych plików dziennika grafiki przy użyciu tego samego `VsgDbg` wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [UnInit](../debugger/init.md)
