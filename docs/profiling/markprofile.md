---
title: MarkProfile | Microsoft Docs
description: Metoda MarkProfile Wstawia znacznik profilu do pliku. vsp. Profilowanie wątku zawierającego funkcję MarkProfile musi być włączone dla znacznika, który ma zostać wstawiony.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecf676c58d8850834ec0c3333196dfb7144f885e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718866"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile`Metoda Wstawia znacznik profilu w.*plik VSP* . Profilowanie wątku zawierającego `MarkProfile` funkcję musi być włączone dla znacznika, który ma zostać wstawiony.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Znacznik do wstawienia. Znacznik musi być większy lub równy 0 (zero).

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość
 Funkcja wskazuje powodzenie lub niepowodzenie przy użyciu wyliczenia **PROFILE_COMMAND_STATUS** . Zwracana wartość może być jedną z następujących:

|Liczeni|Opis|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametr jest mniejszy lub równy 0. Te wartości są zarezerwowane. Znacznik i komentarz nie są rejestrowane.|
|MARK_ERROR_MODE_NEVER|Tryb profilowania został ustawiony tak, aby nigdy nie był wywoływany przez funkcję. Znacznik i komentarz nie są rejestrowane.|
|MARK_ERROR_MODE_OFF|Tryb profilowania został ustawiony na OFF, gdy funkcja została wywołana. Znacznik i komentarz nie są rejestrowane.|
|MARK_ERROR_NO_SUPPORT|Brak obsługi znacznika w tym kontekście. Znacznik i komentarz nie są rejestrowane.|
|MARK_ERROR_OUTOFMEMORY|Pamięć nie jest dostępna do rejestrowania zdarzenia. Znacznik i komentarz nie są rejestrowane.|
|MARK_TEXTTOOLONG|Ciąg przekracza maksymalną 256 znaków. Ciąg komentarza jest obcinany, a znacznik i komentarz są rejestrowane.|
|MARK_OK|MARK_OK jest zwracany, aby wskazać powodzenie.|

## <a name="remarks"></a>Uwagi
 Wartość znacznika jest wstawiana do. plik *VSP* za każdym razem, gdy kod jest uruchamiany, jeśli wątek zawierający funkcję MarkProfile jest profilowany. Możesz wywoływać MarkProfile wiele razy.

 Znaczniki profilów są globalne w zakresie. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w. plik *VSP* .

 Stan profilowania wątku, który zawiera funkcję profilu znacznika, musi być włączony, gdy znaczniki i komentarze są wstawiane za pomocą polecenia Mark lub funkcji interfejsu API (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).

> [!IMPORTANT]
> Metoda MarkProfile powinna być używana tylko z profilowania Instrumentacji.

## <a name="net-framework-equivalent"></a>.NET Framework równoważne
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcji
 Nagłówek: zadeklarowany w *VSPerf. h*

 Biblioteka importowana: *VSPerf. lib*

## <a name="example"></a>Przykład
 Poniższy kod ilustruje funkcję MarkProfile.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
