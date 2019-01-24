---
title: Pobieranie z wyprzedzeniem zawartości aplikacji Windows Store apps | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b7d8b859efa5fac2e3643f4d3a0bd694cd2edd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766617"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Zawartość pobrana z wyprzedzeniem dla aplikacji Sklepu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aby zapewnić zwiększyć szybkość reakcji aplikacji Windows Store, możesz poprosić o Windows do wstępnego ładowania niektórych zawartości sieci web, takich jak strony sieci web lub obrazów do aplikacji [WinINet](http://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)pamięci podręcznej. Ta funkcja jest wywoływana, trwa pobieranie z wyprzedzeniem. Jest szczególnie efektywna, dla zawartości, która jest używana podczas uruchamiania, ale użytkownik może zawartość pobrana z wyprzedzeniem inne często używane, za. Metody [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) klasy umożliwiają określenie identyfikatorów URI zawartości, którą chcesz wstępnego ładowania. Zobacz zestaw SDK Windows [przykładowej zawartości pobierania z wyprzedzeniem](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) przykładów dotyczących sposobów dodać funkcje ContentPrefetcher do aplikacji.  
  
 Windows korzysta z algorytmów heurystycznych, aby określić, gdy, a pobieranie z wyprzedzeniem powinny być wykonywane i jakie zasoby zostaną pobrane. Algorytm heurystyczny uwzględniać konto system sieci i stan zasilania, Historia użycia aplikacji użytkownika oraz liczbę prób wcześniejszego pobierania z wyprzedzeniem. W programie Visual Studio, można użyć **wyzwalacza Windows Store App pobieranie z wyprzedzeniem** polecenie, aby wymusić Windows umożliwia zignorowanie Algorytm heurystyczny ContentPrefetcher i wstępnego ładowania całą zawartość określona witryna sieci web. Może to być przydatne, jeśli chcesz, aby przetestować zachowanie aplikacji lub wydajność dzięki zawartość pobrana z wyprzedzeniem w znanym stanie (załadowane lub nie załadowano).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Aby wymusić wstępne ładowanie ContentPrefetcher określone zasoby  
 Ta procedura zakłada, że masz już Ustawianie funkcji ContentPrefetcher i określony identyfikator URI zawartości do wstępnego w projekcie aplikacji. Aby wymusić wstępne ładowanie zawartości, gdy określone zasoby są nowe lub zmodyfikowane, musisz uruchomić i zatrzymać aplikację, przed wybraniem **wyzwalacza Windows Store App pobieranie z wyprzedzeniem** polecenia. Możesz uruchomić tę aplikację, aby najpierw zarejestrować identyfikatory URI. **Wyzwalanie pobierania z wyprzedzeniem programu Windows Store App** polecenie wymusza następnie ContentPrefetcher, aby pobrać zawartość i dodaj ją w pamięci podręcznej. W kolejnych uruchomień aplikacji można założyć, że zawartość jest wstępnie załadowane.  
  
1. Uruchom aplikację, aby zarejestrować zawartość pobieranie z wyprzedzeniem identyfikatory URI z aplikacją. Na **debugowania** menu, wybierz **Rozpocznij debugowanie** (skrót klawiaturowy: F5).  
  
2. Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (skrót klawiaturowy: Shift + F5).  
  
3. Na **debugowania** menu, wybierz **inne cele debugowania** , a następnie wybierz **wyzwalacza Windows Store App pobieranie z wyprzedzeniem**.  
  
   Można teraz debugować, test lub analizowanie aplikacji przy użyciu zasobów internetowych pobieranych z wyprzedzeniem.  
  
> [!NOTE]
>  Powtórz te czynności przy dodawaniu lub zmodyfikować zawartość określona witryna sieci web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wpis w blogu: Wyzwalanie pobierania z wyprzedzeniem dla aplikacji Windows Store w Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
