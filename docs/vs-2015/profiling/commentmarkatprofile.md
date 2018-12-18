---
title: CommentMarkAtProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b65b7067dee996f7b50cb98345c2777fc6224df3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805197"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`CommentMarkAtProfile` Metoda wstawia wartość sygnatury czasowej, liczbowych znakiem i ciąg komentarza w pliku Vsp. Wartość znacznika czasu może służyć do synchronizowania zdarzenia zewnętrzne. Dla tego znaku i komentarz do wstawienia profilowania dla wątków, która zawiera funkcję CommentMarkAtProfile musi mieć wartość ON.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
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
>  Należy używać metod CommentMarkAtProfile z Instrumentacją tylko.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacje o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują VSPerf.h|  
|**Biblioteka**|Użyj VSPerf.lib|  
|**Unicode**|Zaimplementowane jako CommentMarkAtProfileW (Unicode) i CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje sposób używania CommentMarkAtProfile wywołania funkcji ogólnego. W przykładzie założono użycie makra ciągu Win32 i ustawienia kompilatora standardu ANSI ustalić, czy kod wywołuje ANSI jest włączona funkcja.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów API profilera programu Visual Studio (natywnych)](../profiling/visual-studio-profiler-api-reference-native.md)



