---
title: Funkcja SccBeginBatch | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6bb145358184117046e14b7b598ce6d4bb4586b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333898"
---
# <a name="sccbeginbatch-function"></a>Funkcja SccBeginBatch
Ta funkcja zostanie uruchomiony sekwencji operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana w celu zakończenia zadania wsadowego. Partie te nie mogą być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Batch operacji rozpoczęło się pomyślnie.|
|SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonania tych samych operacji między wieloma projektami lub wieloma kontekstów. Partie można wyeliminować okna dialogowe projektu nadmiarowe od środowiska użytkownika podczas operacji wsadowej. `SccBeginBatch` Funkcji i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako pary funkcji do wskazania rozpoczęcie i zakończenie operacji. Nie można zagnieżdżać ich. `SccBeginBatch` Ustawia flagę wskazującą, że trwa wykonywanie operacji przetwarzania wsadowego.

 Podczas operacji zbiorczej jest włączone, wtyczka do kontroli źródła należy co najwyżej jedno okno dialogowe dla pytań użytkownik widzi i zastosować odpowiedzi z tego okna dialogowego na wszystkie kolejne operacje.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)