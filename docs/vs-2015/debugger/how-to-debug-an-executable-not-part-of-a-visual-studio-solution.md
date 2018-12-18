---
title: 'Porady: debugowanie pliku wykonywalnego nie jest częścią rozwiązania programu Visual Studio | Dokumentacja firmy Microsoft'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fb9b0a31f078ce197851bccb1f4c85f24408a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798667"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami możesz chcieć debugowanie pliku wykonywalnego, który nie jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Może być wykonywalny, który został utworzony poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub wykonywalny, który otrzymałeś od kogoś innego.  
  
 Zwykle rozwiązaniem tego problemu jest uruchomienie pliku wykonywalnego poza programem Visual Studio i dołączenie do niego przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera. Aby uzyskać więcej informacji, zobacz[dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Dołączanie do aplikacji wymaga dodatkowych ręcznych czynności, więc zajmuje kilka sekund. To niewielkie opóźnienie oznacza, że dołączanie nie pomoże, jeśli chcesz debugować problem, który występuje podczas uruchamiania. Ponadto Jeśli debugujesz program, który nie czeka na dane wejściowe użytkownika i szybko się kończy, możesz nie mieć czasu, aby dołączyć do niego. Jeśli masz [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] zainstalowane, można utworzyć projekt EXE dla takiego programu.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Aby utworzyć projekt EXE dla istniejącego pliku wykonywalnego  
  
1.  Na **pliku** menu, kliknij przycisk **Otwórz** i wybierz **projektu**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij listę rozwijaną listę obok **nazwy pliku** i zaznacz **wszystkie pliki projektu**.  
  
3.  Znajdź plik wykonywalny, a następnie kliknij przycisk **OK**.  
  
     Tworzy to rozwiązanie tymczasowe, które zawiera plik wykonywalny.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Aby zaimportować plik wykonywalny do rozwiązania programu Visual Studio  
  
1.  Na **pliku** menu wskaż **Dodaj projekt**, a następnie kliknij przycisk **istniejący projekt**.  
  
2.  W **Dodaj istniejący projekt** okno dialogowe, kliknij listę rozwijaną listę obok **nazwy pliku** i zaznacz **wszystkie pliki projektu**.  
  
3.  Znajdź i zaznacz plik wykonywalny.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Uruchom plik wykonywalny, wybierając polecenie wykonania, takie jak **Start**, z **debugowania** menu.  
  
    > [!NOTE]
    >  Nie wszystkie języki programowania wspierają projekty EXE. Zainstaluj [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Jeśli musisz korzystać z tej funkcji.  
  
     Podczas debugowania pliku wykonywalnego bez kodu źródłowego, dostępne funkcje debugowania są ograniczone, czy dołączyć do uruchomionego pliku wykonywalnego lub dodać plik wykonywalny do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania. Jeśli plik wykonywalny został skompilowany bez informacji debugowania w zgodnym formacie, funkcje dostępne są dalej ograniczone. Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest zaimportowanie kodu źródłowego do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i utworzenie kompilacja do debugowania pliku wykonywalnego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [DBG, pliki](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



