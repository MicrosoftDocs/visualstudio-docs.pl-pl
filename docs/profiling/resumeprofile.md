---
title: ResumeProfile | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c503c0fccf6cd78a01914647294a37e0b86f55e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947910"
---
# <a name="resumeprofile"></a>ResumeProfile
`ResumeProfile` Metoda zmniejsza wstrzymań/wznowień licznik do określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Level`  
  
 Wskazuje poziom profilu do wydajności, które mogą być stosowane zbierania danych. Następujące **PROFILE_CONTROL_LEVEL** moduły wyliczające może służyć do wskazania jednego z trzech poziomów wydajności, które zbieranie danych można stosować:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienie poziomie ma wpływ na wszystkie procesy i wątki podczas uruchomienia profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomie proces wpływają na wszystkie wątki, które są dostępne w ramach określonego procesu.|  
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
 Początkowa wartość licznika wstrzymań/wznowień to 0. Każde wywołanie SuspendProfile dodaje 1 Liczba wstrzymań/wznowień; Każde wywołanie ResumeProfile odejmuje 1.  
  
 Gdy liczba wstrzymań/wznowień jest większa niż 0, stan wstrzymań/wznowień poziomu został WYŁĄCZONY. Gdy liczba jest mniejsza lub równa 0, stan wstrzymań/wznowień ma wartość ON.  
  
 W przypadku uruchomień/zatrzymań stan i stan wstrzymań/wznowień zarówno na, stan profilowania dla poziomu ma wartość ON. Na wątek być profilowane, globalne, proces i poziomie wątku stany wątku muszą być włączone.  
  
## <a name="net-framework-equivalent"></a>Równoważne z .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: Zadeklarowane w *VSPerf.h*  
  
 Biblioteka importów: *VSPerf.lib*  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcję ResumeProfile. W przykładzie założono, czy Wykonano wywołanie metody SuspendProfile dla tego samego wątku lub proces zidentyfikowany przez [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)