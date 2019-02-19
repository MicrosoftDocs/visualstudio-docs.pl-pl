---
title: VSPerfCLREnv | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7387f2bc55d00695e85df3b023914e8d6fe9696d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54768088"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vsperfclrenv — narzędzie służy do ustawiania zmiennych środowiskowych, które są wymagane do profilu aplikacji .NET Framework. Używa następującej składni:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Możesz wybrać opcję zależy od tego, której te trzy rodzaje profilowania, należy użyć: próbkowanie, Instrumentacja, lub globalnego. Osobną opcją jest wymagany do uwzględnienia danych o interakcji między warstwami w danych profilowania. W poniższych tabelach opisano składnię dla każdej opcji.  
  
> [!NOTE]
>  Po zakończeniu profilowania, uruchom **VSPerfCLREnv** z **/ off** lub **/globaloff** możliwość usuwanie zmiennych środowiskowych niezbędnych do profilowania. Aby uzyskać więcej informacji zobacz Opcje polecenia VSPerfCLREnv do ustawienia środowiska Usuń pokazano poniżej.  
  
 **Opcje polecenia VSPerfCLREnv, w tym dane interakcji między warstwami**  
  
> [!WARNING]
>  Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] i [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)], Natomiast obejrzeć takie dane można wyświetlić tylko w [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] i [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat zapytań ADO.NET w aplikacjach wielowarstwowych. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej. Dane interakcji między można dodać do dowolnej profilowania przy użyciu dowolnej metody profilowania.  
  
 **InteractionOn** i **GlobalInteractionOn** opcje włączyć zbieranie danych o interakcji między warstwami. Opcja interakcji musi być ustawiona, po ustawienie zmiennej środowiskowej VSPerfCLREnv, który jest wymagany do profilu aplikacji.  
  
 Poniższy przykład zawiera dane interakcji między warstwami do uruchomienia profilowania, która używa metody pobierania próbek:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Poniższy przykład zawiera dane interakcji między warstwami do uruchomienia profilowania dla usługi Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Opcje polecenia VSPerfCLREnv przetwarzania profilowania Instrumentacji**  
  
 W poniższej tabeli opisano opcje polecenia VSPerfCLREnv do profilowania Instrumentacji:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**TraceOn**|Włącza profilowanie przy użyciu metody instrumentacji. Nie uwzględnia alokacji pamięci profilowania, lub zbieranie danych o okresie istnienia obiektu.|  
|**TraceGC**|Włącza profilowanie przydziału pamięci przy użyciu metody instrumentacji. Włącza zbieranie danych o okresie istnienia obiektu.|  
|**TraceGCLife**|Umożliwia przydzielanie pamięci, profilowanie i zbieranie danych o okresie istnienia obiektu przy użyciu metody instrumentacji.|  
  
 **Opcje polecenia VSPerfCLREnv profilowanie próbkowania procesu**  
  
 W poniższej tabeli opisano opcje polecenia VSPerfCLREnv profilowanie próbkowania:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**SampleOn**|Włącza profilowanie przy użyciu metody pobierania próbek. Nie uwzględnia alokacji pamięci profilowania, lub zbieranie danych o okresie istnienia obiektu.|  
|**SampleGC**|Włącza profilowanie przydziału pamięci przy użyciu metody próbkowania. Włącza zbieranie danych o okresie istnienia obiektu.|  
|**SampleGCLife**|Włącza profilowanie przydziału pamięci przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|  
|**SampleLineOff**|Wyłącza kolekcję .NET profilowania danych na poziomie wiersza.|  
  
 **Opcje polecenia VSPerfCLREnv do globalnego profilowania**  
  
 Profilowanie usług zarządzanych, takich jak i aplikacji sieci web ASP.NET, który jest uruchamiany przez system operacyjny, a nie jest uruchomiony przez użytkownika, należy użyć opcji pod kątem globalnego profilowania opcji polecenia VSPerfCLREnv. W poniższej tabeli opisano globalnego wersje VSPerfCLREnv opcje. Te opcje ustawić odpowiednie zmienne środowiskowe w rejestrze.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**GlobalTraceOn**|Włącza profilowanie globalnego przy użyciu metody instrumentacji. Zbiera zdarzenia alokacji pamięci ani danych o okresie istnienia obiektu.|  
|**GlobalTraceGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Włącza zbieranie danych o okresie istnienia obiektu.|  
|**GlobalTraceGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Umożliwia także zbierania danych o okresie istnienia obiektu.|  
|**GlobalSampleOn**|Umożliwia globalny profilowania przy użyciu metody próbkowania. Nie umożliwi zbieranie zdarzeń alokacji pamięci lub danych o okresie istnienia obiektu.|  
|**GlobalSampleGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Włącza zbieranie danych o okresie istnienia obiektu.|  
|**GlobalSampleGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|  
  
 **Opcje polecenia VSPerfCLREnv do usunięcia ustawień środowiska**  
  
 Po zakończeniu profilowania aplikacji zarządzanej użyj jednej z następujących opcji, aby usunąć zmienne środowiskowe, które zostały dodane przez VSPerfCLREnv. W poniższej tabeli opisano sposób usuwania obu zmiennych środowiskowych standardowe i globalne:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Off**|Usuwa zmienne środowiskowe profilowania .NET standard. Użyj tej opcji, gdy nieglobalnych opcje polecenia VSPerfClrEnv były używane do ustawiania zmiennych środowiskowych programu profilującego.|  
|**GlobalOff**|Usuwa zmienne środowiskowe globalnego profilowania platformy .NET. Użyj tej opcji podczas uruchomienia aplikacji według systemu operacyjnego i nie profilera.|  
  
## <a name="remarks"></a>Uwagi  
 Te opcje nie są wymagane do profilowania aplikacji zarządzanej, gdy aplikacja zostanie uruchomiona przy użyciu Eksploratora wydajności w środowisku IDE. Eksplorator wydajności Ustawia wszystkie ustawienia wymagane środowisko dla Ciebie.  
  
 Jeśli odpowiednie środowisko nie została ustawiona podczas profilowania, ostrzeżenie jest zgłaszane podczas analizy i funkcji zarządzanej, których nazwy nie będą prawidłowo rozpoznawane.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
