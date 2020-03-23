---
title: CommentMarkProfile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d45bab6b909fffa107158236d9050632f114c530
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772793"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
Funkcja `CommentMarkProfile` wstawia znacznik numeryczny i ciąg tekstowy w pliku . *vsp.* Aby znacznik i komentarz mają zostać wstawione, profilowanie wątku zawierającego `CommentMarkProfile` funkcję musi być włączone.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Znacznik numeryczny do wstawienia. Znacznik musi być większy lub równy 0 (zero).

 `szComment`

 Wskaźnik do ciągu tekstowego do wstawienia. Ciąg musi być mniejszy niż 256 znaków, w tym terminator NULL.

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
 Stan profilowania wątku, który zawiera funkcję profilu znaczników, musi być włączony, gdy znaczniki i komentarze wstawione za pomocą polecenia VSInstr Mark lub z funkcjami (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).

 Znaki profilu mają zasięg globalny. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w pliku . *vsp.*

> [!IMPORTANT]
> CommentMarkProfile metoda może być używana tylko z instrumentacji.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 Plik dll Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informacje o funkcjach

|||
|-|-|
|**Nagłówka**|Uwzględnij VSPerf.h|
|**Biblioteka**|Użyj pliku VSPerf.lib|
|**Unicode**|Zaimplementowano `CommentMarkProfileW` jako `CommentMarkProfileA` (Unicode) i (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje commentmarkprofile wywołanie funkcji. W przykładzie przyjęto użycie makr ciągów Win32 i ustawień kompilatora Unicode w celu ustalenia, czy kod wywołuje wywołanie [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] funkcji.

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
