---
title: Dokumentacja interfejsu API (debugowanie w programie Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c45f89a6deafad5317f4cde704b73d9d4a1f30a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771704"
---
# <a name="api-reference-visual-studio-debugging"></a>Dokumentacja interfejsu API (Debugowanie w programie Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta część zawiera omówienie interfejsu API, przewodnik, który pokazuje składni i użycia dla wszystkich elementów interfejsu API i gamę przykłady kodu. Wszystkie odwołania są wymieniane alfabetycznie według kategorii.  
  
 W poniższej tabeli przedstawiono typowe `HRESULT` wartości zwracane przez metody.  
  
|Nazwa|Opis|Wartość|  
|----------|-----------------|-----------|  
|S_OK|Powodzenie.|0x00000000|  
|WARTOŚĆ E_UNEXPECTED|Nieoczekiwany błąd.|0x8000FFFF|  
|E_NOTIMPL|Nie zaimplementowano.|0x80004001|  
|E_OUTOFMEMORY|Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.|0x8007000E|  
|E_INVALIDARG|Jeden lub więcej argumentów są nieprawidłowe.|0x80070057|  
|E_NOINTERFACE|Taki interfejs nie jest obsługiwane.|0x80004002|  
|E_POINTER|Nieprawidłowy wskaźnik.|0x80004003|  
|E_HANDLE|Nieprawidłowe dojście.|0x80070006|  
|E_ABORT|Operacja została przerwana.|0x80004004|  
|E_FAIL|Nieoczekiwany błąd.|0x80004005|  
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu.|0x80070005|  
  
> [!NOTE]
>  Gdy [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugowania metoda zwraca `S_OK`, zakłada się, że wszystkie out parametru wskaźniki są prawidłowe, oznacza to, że nie nastąpi sprawdzanie poprawności jest przeprowadzane na się wskaźniki parametru podczas `S_OK` jest zwracana.  
  
> [!NOTE]
>  Nieprawidłowy lub `NULL` [parametry out] może spowodować, że środowisko IDE ulega awarii.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

