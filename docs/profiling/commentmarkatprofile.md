---
title: CommentMarkAtProfile | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e67f41bc4e30f0790e672a241dfe478a13ded9b7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407566"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile` Metoda wstawia wartość sygnatury czasowej, liczbowych znakiem i ciąg komentarza w. *Vsp* pliku. Wartość znacznika czasu może służyć do synchronizowania zdarzenia zewnętrzne. Dla tego znaku i komentarz do wstawienia profilowania dla wątków, która zawiera funkcję CommentMarkAtProfile musi mieć wartość ON.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametry
 `dnTimestamp`

 64-bitowa liczba całkowita, która reprezentuje wartość sygnatury czasowej.

 `lMarker`

 Liczbowe znacznik do wstawienia. Znacznik muszą być większe niż lub równa 0 (zero).

 `szComment`

 Wskaźnik do ciągu tekstowego do wstawienia. Ciąg musi być mniejsza niż 256 znaków, w tym terminator o wartości NULL.

## <a name="property-valuereturn-value"></a>Właściwość wartości/zwracana wartość
 Funkcja wskazuje powodzenie lub niepowodzenie, za pomocą **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących czynności:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametr jest mniejsza lub równa 0. Te wartości są zastrzeżone. Znak i komentarzy nie są rejestrowane.|
|MARK_ERROR_MODE_NEVER|W trybie profilowania zostało ustawione na nigdy nie w przypadku, gdy funkcja została wywołana. Znak i komentarzy nie są rejestrowane.|
|MARK_ERROR_MODE_OFF|W trybie profilowania zostało ustawione na OFF, gdy funkcja została wywołana. Znak i komentarzy nie są rejestrowane.|
|MARK_ERROR_NO_SUPPORT|Brak obsługi znacznik, w tym kontekście. Znak i komentarzy nie są rejestrowane.|
|MARK_ERROR_OUTOFMEMORY|Pamięć nie jest dostępny do rejestrowania zdarzenia. Znak i komentarzy nie są rejestrowane.|
|MARK_TEXTTOOLONG|Ciąg przekracza maksymalnie 256 znaków. Ciąg komentarza zostanie obcięta i znacznika i komentarz są rejestrowane.|
|MARK_OK|MARK_OK jest zwracany do wskazania sukcesu.|

## <a name="remarks"></a>Uwagi
 Stan profilowania dla wątku, który zawiera funkcję profilu znacznika musi być na, jeśli znaczniki i komentarze wstawione za pomocą polecenia znaku lub za pomocą interfejsu API funkcji (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile). Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jednym wątku może służyć do oznaczania początku lub końcu segmentu data w żadnym z wątków w pliku Vsp.

> [!IMPORTANT]
> Należy używać metod CommentMarkAtProfile z Instrumentacją tylko.

## <a name="net-framework-equivalent"></a>Równoważne z .NET framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcji

|||
|-|-|
|**Nagłówek**|Obejmują *VSPerf.h*|
|**Biblioteka**|Use *VSPerf.lib*|
|**Unicode**|Zaimplementowane jako CommentMarkAtProfileW (Unicode) i CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje sposób używania CommentMarkAtProfile wywołania funkcji ogólnego. W przykładzie założono użycie makra ciągu Win32 i ustawienia kompilatora standardu ANSI ustalić, czy kod wywołuje ANSI jest włączona funkcja.

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
- [Odwołanie w Visual Studio Profiler API (w trybie macierzystym)](../profiling/visual-studio-profiler-api-reference-native.md)