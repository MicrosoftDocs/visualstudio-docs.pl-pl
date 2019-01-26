---
title: MarkProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15a53b3423cbda77f0625e6791e96db740636000
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925191"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile` Metoda wstawia znacznik profilu w. *Vsp* pliku. Profilowanie w przypadku wątku zawierający `MarkProfile` funkcja musi być ON znak do wstawienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parametry  
 `lMarker`  
  
 Znacznik do wstawienia. Znacznika musi być większa lub równa 0 (zero).  
  
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
 Wartość znaku jest wstawiana do. *vsp* pliku przy każdym uruchomieniu kodu Jeśli wątek zawierający funkcję MarkProfile jest profilowana. MarkProfile można wywołać wiele razy.  
  
 Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jednym wątku może służyć do oznaczania początku lub końcu segmentu data w żadnym z wątków w. *vsp* pliku.  
  
 Stan profilowania dla wątku, który zawiera funkcję profilu znacznika musi być na, jeśli znaczniki i komentarze wstawione za pomocą polecenia znaku lub za pomocą interfejsu API funkcji (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).  
  
> [!IMPORTANT]
>  Metoda MarkProfile należy używać z tylko profilowanie instrumentacji.  
  
## <a name="net-framework-equivalent"></a>Równoważne z .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informacje o funkcji  
 Nagłówek: Zadeklarowane w *VSPerf.h*  
  
 Biblioteka importów: *VSPerf.lib*  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje funkcja MarkProfile.  
  
```cpp  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)