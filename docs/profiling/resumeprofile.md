---
title: ResumeProfile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3d65d5fcf8961493c2b780453f2143de788551a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778313"
---
# <a name="resumeprofile"></a>ResumeProfile
Metoda `ResumeProfile` zmniejsza wstrzymanie/wznowienie licznika dla określonego poziomu profilowania.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `Level`

 Wskazuje poziom profilu, do którego można zastosować zbieranie danych o wydajności. Następujące **PROFILE_CONTROL_LEVEL** wyliczaczy może służyć do wskazania jednego z trzech poziomów, do których można zastosować zbieranie danych wydajności:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Ustawienie poziomu globalnego wpływa na wszystkie procesy i wątki w przebiegu profilowania.|
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu wpływa na wszystkie wątki, które są częścią określonego procesu.|
|PROFILE_THREADLEVEL|Ustawienie poziom profilowania wątku wpływa na określony wątek.|

 `dwId`

 Identyfikator procesu lub wątku generowany przez system.

## <a name="property-valuereturn-value"></a>Wartość właściwości/wartość zwracana
 Funkcja wskazuje sukces lub niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących wartości:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Identyfikator elementu profilowania nie istnieje.|
|PROFILE_ERROR_LEVEL_NOEXIST|Określony poziom profilowania nie istnieje.|
|PROFILE_ERROR_MODE_NEVER|Tryb profilowania został ustawiony na NIGDY, gdy funkcja została wywołana.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Wywołanie funkcji profilowania, poziom profilowania lub kombinacja wywołania i poziomu nie została jeszcze zaimplementowana.|
|PROFILE_OK|Połączenie zakończyło się pomyślnie.|

## <a name="remarks"></a>Uwagi
 Wartość początkowa licznika wstrzymania/wznowienia wynosi 0. Każde wywołanie SuspendProfile dodaje 1 do liczby Wstrzymaj/Wznów; każde wywołanie resumeProfile odejmuje 1.

 Gdy liczba wstrzymania/wznowienia jest większa niż 0, stan Wstrzymaj/Wznów dla poziomu jest wyłączony. Gdy liczba jest mniejsza lub równa 0, stan Wstrzymaj/Wznów jest włączony.

 Gdy stan Start/Stop i stan Wstrzymaj/Wznów są włączone, stan profilowania dla poziomu jest włączony. Aby wątek ma być profilowany, stany poziomu globalnego, procesu i wątku dla wątku muszą być włączone.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 *Plik dll Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcjach
 Nagłówek: Zadeklarowany w *vsPerf.h*

 Import biblioteki: *VSPerf.lib*

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje ResumeProfile funkcji. W przykładzie przyjęto założenie, że wywołanie SuspendProfile metoda została wykonana dla tego samego wątku lub procesu zidentyfikowanego przez [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
