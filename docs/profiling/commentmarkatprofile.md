---
title: CommentMarkAtProfile | Microsoft Docs
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
ms.openlocfilehash: ee9eb5353109bcf5df6903e7e607a11b8bfd0536
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545616"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile`Metoda wstawia wartość znacznika czasu, znacznik liczbowy i ciąg komentarza w.* plik VSP* . Wartość sygnatury czasowej może służyć do synchronizowania zdarzeń zewnętrznych. Dla znacznika i komentarza, który ma zostać wstawiony, Profilowanie wątku, który zawiera funkcję CommentMarkAtProfile, musi być włączone.

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

 Znacznik liczbowy do wstawienia. Znacznik musi być większy lub równy 0 (zero).

 `szComment`

 Wskaźnik do ciągu tekstowego do wstawienia. Ciąg musi być krótszy niż 256 znaków, łącznie z terminatorem o wartości NULL.

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
 Stan profilowania wątku, który zawiera funkcję profilu znacznika, musi być włączony, gdy znaczniki i komentarze są wstawiane za pomocą polecenia Mark lub funkcji interfejsu API (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile). Znaczniki profilów są globalne w zakresie. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w pliku. vsp.

> [!IMPORTANT]
> Metody CommentMarkAtProfile powinny być używane tylko z instrumentacją.

## <a name="net-framework-equivalent"></a>.NET Framework równoważne
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcji

|Element|Wartość|
|-|-|
|**Nagłówki**|Uwzględnij *VSPerf. h*|
|**Biblioteka**|Użyj *VSPerf. lib*|
|**Unicode**|Zaimplementowane jako CommentMarkAtProfileW (Unicode) i CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje użycie wywołania funkcji ogólnej CommentMarkAtProfile. W przykładzie założono użycie makr ciągu Win32 i ustawień kompilatora dla ANSI, aby określić, czy kod wywołuje funkcję z obsługą ANSI.

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

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
