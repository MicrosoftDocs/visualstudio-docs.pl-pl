---
title: Init | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed9bffdcd9f5e6a862197928f2a7369cd3643625
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781299"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przygotowuje składnik w aplikacji Narzędzie Diagnostyka grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [UnInit](../debugger/init.md)



