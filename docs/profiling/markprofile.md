---
title: MarkProfile | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f53b51f9e78e2cb5d327abd3a79ebf2faa3a9204
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778573"
---
# <a name="markprofile"></a>MarkProfile
Metoda `MarkProfile` wstawia znacznik profilu w pliku . *vsp.* Profilowanie wątku zawierającego `MarkProfile` funkcję musi być włączone, aby znak został wstawiony.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Znacznik do wstawienia. Znacznik musi być większy lub równy 0 (zero).

## <a name="property-valuereturn-value"></a>Wartość właściwości/wartość zwracana
 Funkcja wskazuje sukces lub niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących wartości:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametr jest mniejszy lub równy 0. Te wartości są zastrzeżone. Znak i komentarz nie są rejestrowane.|
|MARK_ERROR_MODE_NEVER|Tryb profilowania został ustawiony na NIGDY, gdy funkcja została wywołana. Znak i komentarz nie są rejestrowane.|
|MARK_ERROR_MODE_OFF|Tryb profilowania został ustawiony na OFF, gdy funkcja została wywołana. Znak i komentarz nie są rejestrowane.|
|MARK_ERROR_NO_SUPPORT|Brak obsługi znaku w tym kontekście. Znak i komentarz nie są rejestrowane.|
|MARK_ERROR_OUTOFMEMORY|Pamięć nie była dostępna do nagrywania zdarzenia. Znak i komentarz nie są rejestrowane.|
|MARK_TEXTTOOLONG|Ciąg przekracza maksymalnie 256 znaków. Ciąg komentarza zostanie obcięty, a znacznik i komentarz są rejestrowane.|
|MARK_OK|MARK_OK jest zwracany, aby wskazać sukces.|

## <a name="remarks"></a>Uwagi
 Wartość znacznika zostanie wstawiona do pliku . *vsp* plik za każdym razem, gdy kod jest uruchamiany, jeśli wątek zawierający MarkProfile funkcji jest profilowane. MarkProfile można wywołać wiele razy.

 Znaki profilu mają zasięg globalny. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w pliku . *vsp.*

 Stan profilowania wątku, który zawiera funkcję profilu znaczników, musi być włączony, gdy znaczniki i komentarze wstawione za pomocą polecenia Mark lub z funkcjami interfejsu API (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).

> [!IMPORTANT]
> MarkProfile metoda powinna być używana tylko z profilowania instrumentacji.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 *Plik dll Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcjach
 Nagłówek: Zadeklarowany w *vsPerf.h*

 Import biblioteki: *VSPerf.lib*

## <a name="example"></a>Przykład
 Poniższy kod ilustruje MarkProfile funkcji.

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

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
