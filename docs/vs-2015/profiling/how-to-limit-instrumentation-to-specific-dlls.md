---
title: 'Instrukcje: ograniczanie Instrumentacji do określonych bibliotek DLL | Dokumentacja firmy Microsoft'
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
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 054a281d445f5910e9a2d635bb453dd283425453
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803464"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Porady: ograniczanie instrumentacji do określonych bibliotek DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą metody profilowania instrumentacji, można ograniczyć zbierania danych profilowania do jednego lub więcej bibliotek DLL w aplikacji. Aby profilować jedną lub więcej bibliotek DLL w aplikacji, należy utworzyć sesję wydajności, który zawiera pliki .dll jako elementy docelowe. Można określić bibliotek DLL, które chcesz profilować jako projekty w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania lub jako niezależnego pliki binarne.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Ograniczenie Instrumentacji do określonych bibliotek DLL w rozwiązaniu Visual Studio  
  
1.  Otwórz rozwiązanie, które zawiera DLL w [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Na **analizy** menu, wybierz opcję **Uruchom Kreatora wydajności**.  
  
3.  Wybierz **Instrumentacji** metody profilowania, a następnie kliknij przycisk **dalej**.  
  
4.  Z **które z następujących dostępnych elementów docelowych chcesz profil?**, wybierz nazwę projektu dll, a następnie kliknij przycisk **dalej**.  
  
5.  Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowa sesja wydajności w **Eksplorator wydajności** okna.  
  
6.  Kliknij prawym przyciskiem myszy **cele** , a następnie wybierz **Dodaj projekt docelowy**.  
  
7.  Z **Dodaj projekt docelowy** listy, wybierz projekt wykonywalny, który chcesz używać do wykonywania pliku DLL.  
  
     Opcjonalna. Możesz dodać wszelkie projekty biblioteki DLL, które mają do profilu.  
  
8.  Aby zapobiec zbierania danych dla projektu dodano, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść **Instrument** pole wyboru.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określonych bibliotek DLL do profilu jako niezależne plików binarnych  
  
1.  Otwórz [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Na **analizy** menu, wybierz opcję **Uruchom Kreatora wydajności**.  
  
3.  Z **które z następujących dostępnych elementów docelowych chcesz profilu**, wybierz opcję **Profiluj bibliotekę dołączaną dynamicznie (. Biblioteka DLL)** a następnie kliknij przycisk **dalej**.  
  
4.  Na drugiej stronie kreatora wykonaj następujące czynności:  
  
    -   Wpisz ścieżkę i nazwę pliku dll, który chcesz przeprowadzić profilowanie w **ścieżka biblioteki Dll**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **Biblioteka dołączana dynamicznie do profilowania** okno dialogowe. Należy pamiętać o konieczności podania kopia pliku dll, który zostanie uruchomiony przez plik wykonywalny (.exe), który należy wybrać następne.  
  
    -   Wpisz ścieżkę i nazwę pliku wykonywalnego (.exe), który będzie wykonywał .dll w **ścieżka do pliku wykonywalnego**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **pliku wykonywalnego do uruchomienia** okno dialogowe.  
  
    -   Opcjonalna. Wpisz wszelkie argumenty wiersza polecenia, które mają być przekazywane do pliku wykonywalnego w **argumenty wiersza polecenia**. Jeśli to konieczne, należy określić katalog roboczy dla aplikacji w **katalog roboczy**.  
  
    -   Kliknij przycisk **Dalej**.  
  
5.  Wybierz **Instrumentacji** metody profilowania, a następnie kliknij przycisk **dalej**.  
  
6.  Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowa sesja wydajności w **Eksplorator wydajności** okna.  
  
7.  Opcjonalna. Aby dodać więcej plików .dll, kliknij prawym przyciskiem myszy **cele** , a następnie wybierz **Dodaj binarne docelowej**. Wybierz pliki z **Dodaj binarne docelowej** okno dialogowe.  
  
    > [!NOTE]
    >  Nie należy określać plik wykonywalny (.exe), która wykonuje operacje biblioteki dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)



