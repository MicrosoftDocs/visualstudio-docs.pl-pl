---
title: StartProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 994cde18cfe304add796bffa74d2a327e1c63f45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199756"
---
# <a name="startprofile"></a>StartProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`StartProfile`Funkcja ustawia licznik na 1 (włączony) dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Level`  
  
 Wskazuje poziom profilu, do którego można zastosować zbieranie danych wydajności. Poniższe moduły wyliczające **PROFILE_CONTROL_LEVEL** mogą służyć do wskazania jednego z trzech poziomów, do których można zastosować zbieranie danych o wydajności:  
  
|Liczeni|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienie poziomu ma wpływ na wszystkie procesy i wątki w przebiegu profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu wpływa na wszystkie wątki, które są częścią określonego procesu.|  
|PROFILE_THREADLEVEL|Ustawienie poziomu profilowania wątku ma wpływ na określony wątek.|  
  
 `dwId`  
  
 Identyfikator procesu lub wątku generowany przez system.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Funkcja wskazuje powodzenie lub niepowodzenie przy użyciu wyliczenia **PROFILE_COMMAND_STATUS** . Zwracana wartość może być jedną z następujących:  
  
|Liczeni|Opis|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Identyfikator elementu profilowania nie istnieje.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Określony poziom profilowania nie istnieje.|  
|PROFILE_ERROR_MODE_NEVER|Tryb profilowania został ustawiony tak, aby nigdy nie był wywoływany przez funkcję.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Nie zaimplementowano jeszcze wywołania funkcji profilowania, poziomu profilowania lub kombinacji wywołania i poziomu.|  
|PROFILE_OK|Wywołanie zakończyło się pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 StartProfile i StopProfile kontrolują stan uruchomienia/zatrzymania dla poziomu profilowania. Wartość domyślna uruchomienia/zatrzymania to 1. Wartość początkową można zmienić w rejestrze. Każde wywołanie StartProfile ustawia początek/zatrzymanie na 1; Każde wywołanie StopProfile ustawia wartość 0.  
  
 Gdy wartość Start/Stop jest większa od zera, stan uruchomienia/zatrzymania dla poziomu jest włączony. Gdy wartość jest mniejsza lub równa 0, stan uruchomienia/zatrzymania jest wyłączony.  
  
 Gdy stan uruchomienia/zatrzymania i wstrzymania/wznowienia jest włączony, stan profilowania dla poziomu jest włączony. W przypadku wątku, który ma zostać profilowany, Stany globalne, proces i poziom wątku dla wątku muszą być włączone.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: zadeklarowany w VSPerf. h  
  
 Biblioteka importowana: VSPerf. lib  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje wywołanie funkcji StartProfile.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
