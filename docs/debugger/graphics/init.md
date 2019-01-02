---
title: Init | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06594b749b5d92781f6c3389ca6f5f9395c98c75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827250"
---
# <a name="init"></a>Init
Przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vsgLogGetter`  
 Wywoływane jednostki — takich jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcyjny — która przyjmuje jako parametry długość buforu, składające się z `wchar_t` i wskaźnik do buforu i zwraca `void`. Po wywołaniu, wywoływane jednostki Określa nazwę pliku, który będzie używany do rejestrowania informacji graficznych i zapisuje go do określonego bufora przed zwróceniem.  
  
## <a name="remarks"></a>Uwagi  
 `Init` Funkcja jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` klasy jest tworzony przez określenie `bDefaultInit` parametr jej konstruktora jako `true`; w przeciwnym razie `Init` musi być jawnie wywołana przed można aktywnie przechwytywanie i rejestrowanie informacji graficznych.  
  
 Można zakończyć, i zamknij aktywne grafiki pliku dziennika przez wywołanie metody `UnInit`, a następnie przechwycić i zarejestrować więcej informacji graficznych w pliku dziennika grafiki, wywołując `Init` ponownie. To można powtarzać dowolną liczbę razy utworzyć kilka niezależnych grafiki pliki dziennika, korzystając z tych samych `VsgDbg` wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [UnInit](init.md)