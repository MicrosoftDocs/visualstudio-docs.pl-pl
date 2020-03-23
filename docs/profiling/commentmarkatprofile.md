---
title: CommentMarkAtProfile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51028dce1d60c0d01c83cee509a1ed7321855437
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777845"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
Metoda `CommentMarkAtProfile` wstawia wartość sygnatury czasowej, znacznik numeryczny i ciąg komentarza w pliku . *vsp.* Wartość sygnatury czasowej może służyć do synchronizowania zdarzeń zewnętrznych. Aby znacznik i komentarz mają zostać wstawione, profilowanie wątku zawierającego commentMarkAtProfile funkcja musi być wł..

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `dnTimestamp`

 64-bitowa liczba całkowita reprezentująca wartość sygnatury czasowej.

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
 Stan profilowania wątku, który zawiera funkcję profilu znaczników, musi być włączony, gdy znaczniki i komentarze wstawione za pomocą polecenia Mark lub z funkcjami interfejsu API (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile). Znaki profilu mają zasięg globalny. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w pliku vsp.

> [!IMPORTANT]
> CommentMarkAtProfile metody powinny być używane tylko z instrumentacji.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 *Plik dll Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcjach

|||
|-|-|
|**Nagłówka**|Uwzględnij *VSPerf.h*|
|**Biblioteka**|Użyj *pliku VSPerf.lib*|
|**Unicode**|Implementowane jako CommentMarkAtProfileW (Unicode) i CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje użycie CommentMarkAtProfile ogólne wywołanie funkcji. W przykładzie przyjęto użycie makr ciągów Win32 i ustawień kompilatora dla interfejsu ANSI w celu ustalenia, czy kod wywołuje funkcję z włączoną funkcją ANSI.

```cpp
void ExerciseCommentMarkAtProfile(void)
{
    // Declare and initalize variables to pass to
    // CommentMarkAtProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    int64 timeStamp = 0x1111;
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkAtProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkAtProfile(
        timeStamp,
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
    pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API programu Visual Studio Profiler (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
