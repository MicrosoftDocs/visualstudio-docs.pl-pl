---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61c3d580c4e9e0362629d70c23e0b918fe698429
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983459"
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