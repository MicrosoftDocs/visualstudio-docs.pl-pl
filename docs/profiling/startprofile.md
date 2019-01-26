---
title: StartProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f656d0d669fbe9186412805b145b02bdff8e22da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982445"
---
# <a name="startprofile"></a>StartProfile
`StartProfile` Funkcja ustawia licznik do 1 (funkcja włączona) dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Level`  
  
 Wskazuje poziom profilu do wydajności, które mogą być stosowane zbierania danych. Następujące **PROFILE_CONTROL_LEVEL** moduły wyliczające może służyć do wskazania jednego z trzech poziomów wydajności, które zbieranie danych można stosować:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienie poziomie ma wpływ na wszystkie procesy i wątki podczas uruchomienia profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu ma wpływ na wszystkie wątki, które są dostępne w ramach określonego procesu.|  
|PROFILE_THREADLEVEL|Wątek ustawienie poziomie profilowania dotyczy określonego wątku.|  
  
 `dwId`  
  
 Proces lub wątek identyfikator generowany przez system.  
  
## <a name="property-valuereturn-value"></a>Właściwość wartości/zwracana wartość  
 Funkcja wskazuje powodzenie lub niepowodzenie, za pomocą **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących czynności:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Identyfikator elementu profilowania nie istnieje.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Określony poziom profilowania nie istnieje.|  
|PROFILE_ERROR_MODE_NEVER|W trybie profilowania zostało ustawione na nigdy nie w przypadku, gdy funkcja została wywołana.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profilowania wywołanie funkcji, profilowania poziom lub kombinacji wywołania i poziom nie została jeszcze zaimplementowana.|  
|PROFILE_OK|Wywołanie zakończyło się pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 StartProfile i StopProfile kontrolować stan uruchomień/zatrzymań poziomu profilowania. Wartość domyślna uruchomień/zatrzymań jest 1. Początkowa wartość można zmienić w rejestrze. Każde wywołanie StartProfile ustawia uruchomień/zatrzymań 1; Każde wywołanie StopProfile ustawia ją na 0.  
  
 Podczas uruchamiania/zatrzymywania jest większa niż 0, stan uruchomień/zatrzymań poziomu ma wartość ON. Gdy jest on mniejszy niż lub równa 0, stan uruchomień/zatrzymań został WYŁĄCZONY.  
  
 W przypadku uruchomień/zatrzymań stan i stan wstrzymań/wznowień zarówno na, stan profilowania dla poziomu ma wartość ON. Na wątek być profilowane, globalne, proces i poziomu stany wątku dla wątku musi być włączone.  
  
## <a name="net-framework-equivalent"></a>Równoważne z .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: Zadeklarowane w *VSPerf.h*  
  
 Biblioteka importów: *VSPerf.lib*  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano wywołanie funkcji StartProfile.  
  
```cpp  
void ExerciseStartProfile()  
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
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
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
 [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)