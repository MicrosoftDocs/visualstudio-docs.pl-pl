---
title: StopProfile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a5492d2bbd33e6b250b564532c929234d748506c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778235"
---
# <a name="stopprofile"></a>StopProfile
Funkcja `StopProfile` ustawia licznik na 0 (off) dla określonego poziomu profilowania.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(
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
 StartProfile i StopProfile kontrolować start/stop stanu profilowania na poziomie profilowania. Domyślna wartość start/stop to 1. Wartość początkową można zmienić w rejestrze. Każde wywołanie startprofile ustawia Start/Stop do 1; każde wywołanie StopProfile ustawia go na 0.

 Gdy start/stop jest większa niż 0, stan Start/Stop dla poziomu jest włączony. Gdy jest mniejsza lub równa 0, stan Start/Stop jest wyłączony.

 Gdy stan Start/Stop i stan Wstrzymaj/Wznów są włączone, stan profilowania dla poziomu jest włączony. Aby wątek ma być profilowany, stany poziomu globalnego, procesu i wątku dla wątku muszą być włączone.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 Plik dll Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informacje o funkcjach
 Nagłówek: Zadeklarowany w vsPerf.h

 Import biblioteki: VSPerf.lib

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje StopProfile metody. W przykładzie przyjęto założenie, że wywołanie StartProfile metoda została wykonana dla tego samego wątku lub procesu zidentyfikowanego przez [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseStopProfile()
{
    // StartProfile and StopProfile control the
    // Start/Stop state for the profiling level.
    // The default initial value of Start/Stop is 1.
    // The initial value can be changed in the registry.
    // Each call to StartProfile sets Start/Stop to 1;
    // each call to StopProfile sets it to 0.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to StopProfile.
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = StopProfile(
        PROFILE_THREADLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StopProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
