---
title: 'Porady: debugowanie źródła .NET Framework | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce5e20524040d131a655da1567606ffbb0934a80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725432"
---
# <a name="how-to-debug-net-framework-source"></a>Porady: debugowanie źródła .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najbardziej aktualną wersję [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oferuje nowe funkcje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] debugowania. Aby debugować [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] źródło, musisz mieć dostęp do symboli debugowania dla kodu. Należy również umożliwić stepping do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] źródła.  
  
 Aby umożliwić [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] przechodzenie krok po kroku i ściąganie symbolu w **opcje** okno dialogowe. Po włączeniu pobierania symboli, można od razu pobrać symbole lub po prostu włączyć opcję późniejszego pobrania. Jeśli użytkownik nie pobierze symboli natychmiast, symbole będą pobierane przy następnym uruchomieniu debugowania aplikacji. Możesz także zrobić ręczne pobranie z **modułów** okna lub **stos wywołań** okna.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Aby włączyć debugowanie źródła .NET Framework  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okno dialogowe, kliknij przycisk **debugowanie** kategorii.  
  
3.  W **ogólne** polu **Włącz .NET Framework** krokowe wykonywanie źródła.  
  
    1.  Jeśli masz włączoną opcję tylko mój kod, okno dialogowe ostrzeżenia informuje, że tylko mój kod jest teraz wyłączony. Kliknij przycisk **OK**.  
  
    2.  Jeśli nie masz ustawione lokalizacji pamięci podręcznej symboli, osobne okno dialogowe ostrzeżenia informuje, że teraz ustawiono domyślną lokalizacji pamięci podręcznej symboli. Kliknij przycisk **OK**.  
  
4.  W obszarze **debugowanie** kategorię, kliknij przycisk **symbole**.  
  
5.  Jeśli chcesz zmienić lokalizację pamięci podręcznej symboli:  
  
    1.  Otwórz **debugowanie** węzła w polu po lewej stronie.  
  
    2.  W obszarze **debugowanie** węzła, kliknij przycisk **symbole**.  
  
    3.  Edytuj lokalizację w **Buforuj symbole z serwerów symboli do tego katalogu** lub kliknij przycisk **Przeglądaj** aby wybrać lokalizację.  
  
6.  Jeśli chcesz pobrać symbole natychmiast, kliknij przycisk **Załaduj symbole z powyższych lokalizacji**.  
  
     Ten przycisk jest niedostępny w trybie projektowania.  
  
     Jeśli użytkownik nie chce pobrać symboli teraz, symbole będą pobierane automatycznie przy następnym uruchomieniu debugowania programu.  
  
7.  Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Aby załadować symbole Framework w oknie modułów  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy moduł, dla której symbole nie są ładowane. Można stwierdzić, czy symbole są załadowane lub nie, patrząc **stan symboli** kolumny.  
  
2.  Wskaż **Załaduj symbole z** i kliknij przycisk **serwery symboli firmy Microsoft** można pobrać symbole z serwera publicznego symboli firmy Microsoft lub **ścieżki symboli** załadować z katalogu gdzie można symbole zostały wcześniej zapisane.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Aby załadować symbole Framework w oknie stosu wywołań  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramkę, dla której symbole nie są ładowane. Ramki będą wyszarzone.  
  
2.  Wskaż **Załaduj symbole z** i kliknij przycisk **serwery symboli firmy Microsoft** lub **ścieżki symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



