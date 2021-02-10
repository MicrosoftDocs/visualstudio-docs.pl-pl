---
title: CommentMarkProfile | Microsoft Docs
description: Użyj funkcji CommentMarkProfile, aby wstawić znacznik liczbowy i ciąg tekstowy do pliku *. vsp* .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2518a7dbd97643b1eaa49daa8dd3e6007dcdbb93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941297"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
`CommentMarkProfile`Funkcja Wstawia znacznik liczbowy i ciąg tekstowy do pliku *. vsp* . Dla znacznika i komentarza, który ma zostać wstawiony, Profilowanie wątku, który zawiera `CommentMarkProfile` funkcję, musi być włączone.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `lMarker`

 Znacznik liczbowy do wstawienia. Znacznik musi być większy lub równy 0 (zero).

 `szComment`

 Wskaźnik na ciąg tekstowy, który ma zostać wstawiony. Ciąg musi być krótszy niż 256 znaków, łącznie z terminatorem o wartości NULL.

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
 Stan profilowania wątku, który zawiera funkcję profilu znacznika, musi być włączony, gdy znaczniki i komentarze są wstawiane za pomocą polecenia VSInstr Mark lub funkcji (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).

 Znaczniki profilów są globalne w zakresie. Na przykład znacznik profilu wstawiony w jednym wątku może służyć do oznaczania początku lub końca segmentu danych w dowolnym wątku w pliku *. vsp* .

> [!IMPORTANT]
> Metody CommentMarkProfile można używać tylko z instrumentacją.

## <a name="net-framework-equivalent"></a>.NET Framework równoważne
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informacje o funkcji

|Element|Wartość|
|-|-|
|**Nagłówek**|Uwzględnij VSPerf. h|
|**Biblioteki**|Użyj VSPerf. lib|
|**Unicode**|Zaimplementowane jako `CommentMarkProfileW` (Unicode) i `CommentMarkProfileA` (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje wywołanie funkcji CommentMarkProfile. W przykładzie założono użycie makr ciągu Win32 i ustawień kompilatora Unicode do określenia, czy kod wywołuje [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] wywołanie funkcji.

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
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
