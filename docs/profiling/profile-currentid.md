---
title: PROFILE_CURRENTID | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 747922bf52bee18b20aeba95f7d549c890afceea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972437"
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID zwraca identyfikator wątku lub identyfikator procesu, w wywołaniu funkcji NameProfile, StartProfile, StopProfile, SuspendProfile i ResumeProfile pseudo-token. Umożliwia ona spowodować, że funkcja działać względem bieżącego wątku lub procesów, zamiast jednego wyraźnie wskazane.

## <a name="example"></a>Przykład
 PROFILE_CURRENTID jest zdefiniowany w *VSPerf.h* jako:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje PROFILE_CURRENTID. W przykładzie użyto PROFILE_CURRENTID jako parametr identyfikacji bieżącego wątku w wywołaniu [StartProfile](../profiling/startprofile.md) funkcji.

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

## <a name="see-also"></a>Zobacz także
- [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)