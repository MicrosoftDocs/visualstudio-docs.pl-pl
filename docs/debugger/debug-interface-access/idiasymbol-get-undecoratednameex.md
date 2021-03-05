---
description: Pobiera część lub całą niedekoracyjną nazwę nazwy dekoracyjnej (powiązania) języka C++.
title: 'IDiaSymbol:: get_undecoratedNameEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35e1dcb2704b4a8e76fe8d7ffb172f0846fbdc78
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155531"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Pobiera część lub całą niedekoracyjną nazwę nazwy dekoracyjnej (powiązania) języka C++.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parametry
 `undecoratedOptions`

podczas Określa kombinację flag kontrolujących zwracaną wartość. Zapoznaj się z sekcją uwagi dla określonych wartości i co robią.

 `pRetVal`

określoną Zwraca niedekoracyjną nazwę dla nazwy dekoracyjnej języka C++.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 `undecorateOptions`Może być kombinacją następujących flag.

> [!NOTE]
> Nazwy flag nie są zdefiniowane w DIA SDK, więc musisz dodać deklaracje do kodu lub użyć nieprzetworzonych wartości.

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Włącza pełen tryb dekoracji.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Usuwa znaki podkreślenia wiodące ze słów kluczowych Microsoft Extended.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Wyłącza rozszerzanie rozszerzonych słów kluczowych firmy Microsoft.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Wyłącza rozszerzanie zwracanego typu dla deklaracji podstawowej.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Wyłącza Rozszerzanie modelu deklaracji.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Wyłącza rozszerzanie specyfikatora języka deklaracji.|
|UNDNAME_RESERVED1|0x0020|Rezerwacj.|
|UNDNAME_RESERVED2|0x0040|Rezerwacj.|
|UNDNAME_NO_THISTYPE|0x0060|Wyłącza wszystkie Modyfikatory w `this` typie.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Wyłącza rozszerzanie specyfikatorów dostępu dla elementów członkowskich.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Wyłącza rozszerzanie "throw-Signatures" dla funkcji i wskaźników do funkcji.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Wyłącza rozszerzanie `static` `virtual` elementów członkowskich lub.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Wyłącza Rozszerzanie modelu firmy Microsoft dla zwracanych UDT.|
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32-bitowe nazwy dekoracyjne.|
|UNDNAME_NAME_ONLY|0x1000|Pobiera tylko nazwę głównej deklaracji; zwraca tylko nazwę [Scope::].  Rozwija parametry szablonu.|
|UNDNAME_TYPE_ONLY|0x2000|Dane wejściowe są tylko kodowaniem typu; redaguje abstrakcyjną deklarator.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Parametry rzeczywistego szablonu są dostępne.|
|UNDNAME_NO_ECSU|0x8000|Pomija Wyliczenie/Class/struct/Union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Pomija sprawdzanie prawidłowych znaków identyfikatora.|
|UNDNAME_NO_PTR64|0x20000|Nie zawiera ptr64 w danych wyjściowych.|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
