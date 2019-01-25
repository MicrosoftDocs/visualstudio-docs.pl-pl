---
title: SuspendProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b40b37c8c0ee97b5d7e0cc33773af140bd1010b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790272"
---
# <a name="suspendprofile"></a>SuspendProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SuspendProfile` Metody zwiększa Licznik wstrzymań/wznowień dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
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
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
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
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: Zadeklarowane w VSPerf.h  
  
 Biblioteka importów: VSPerf.lib  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metodę SuspendProfile. W tym przykładzie założono, że dokonano wcześniejszym wywołaniu StartProfile proces lub wątek identyfikowane przez [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów API profilera programu Visual Studio (natywnych)](../profiling/visual-studio-profiler-api-reference-native.md)
