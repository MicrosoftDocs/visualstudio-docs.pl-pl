---
title: PROFILE_CURRENTID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 63b44bee152acbf5529acfcadaa49a19e9feb52b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778365"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID zwraca pseudo-token identyfikatora wątku lub identyfikatora procesu w wywołaniu funkcji NameProfile, StartProfile, StopProfile, SuspendProfile i ResumeProfile. Użyj go, aby spowodować, że funkcja będzie działać w bieżącym wątku lub procesie, a nie w określonym powyżej.

## <a name="example"></a>Przykład
 PROFILE_CURRENTID jest zdefiniowany w *VSPerf. h* jako:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje PROFILE_CURRENTID. W przykładzie używa się PROFILE_CURRENTID jako parametru identyfikującego bieżący wątek w wywołaniu funkcji [StartProfile](../profiling/startprofile.md) .

```cpp
void ExerciseProfileCurrentID()
{
    // Declare ProfileOperationResult enumeration
    // to hold return value of a call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    profileResult = StartProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StartProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
