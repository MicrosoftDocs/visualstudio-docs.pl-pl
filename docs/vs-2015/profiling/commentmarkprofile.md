---
title: CommentMarkProfile | Dokumentacja firmy Microsoft
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
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d1722cd09bfb76e2ca8c72c6948923b0713100
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802944"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`CommentMarkProfile` Funkcji wstawia znacznik liczbowe i ciągu tekstowego w pliku Vsp. Dla tego znaku i komentarz do wstawienia, profilowania dla wątku, który zawiera `CommentMarkProfile` funkcja musi być włączone.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lMarker`  
  
 Znacznik liczbowych do wstawienia. Znacznik muszą być większe niż lub równa 0 (zero).  
  
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
 Stan profilowania dla wątku, który zawiera funkcję profilu znacznika musi być na, jeśli znaczniki i komentarze wstawione za pomocą polecenia VSInstr znaku lub za pomocą funkcji (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).  
  
 Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jednym wątku może służyć do oznaczania początku lub końcu segmentu data w żadnym z wątków w pliku Vsp.  
  
> [!IMPORTANT]
>  Metoda CommentMarkProfile należy używać tylko z Instrumentacją.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacje o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują VSPerf.h|  
|**Biblioteka**|Użyj VSPerf.lib|  
|**Unicode**|Zaimplementowane jako `CommentMarkProfileW` (Unicode) i `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje CommentMarkProfile wywołania funkcji. W przykładzie założono użycie makra ciągu Win32 i ustawienia kompilatora Unicode w celu ustalenia, czy kod wywołuje [!INCLUDE[vcpransi](../includes/vcpransi-md.md)] wywołania funkcji.  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów API profilera programu Visual Studio (natywnych)](../profiling/visual-studio-profiler-api-reference-native.md)



