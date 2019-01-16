---
title: 'Instrukcje: Debugowanie wprowadzonego kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff81b082c877098acec78e56ef9ef211cae8854
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "51778153"
---
# <a name="how-to-debug-injected-code"></a>Instrukcje: Debugowanie wprowadzonego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Przy użyciu atrybutów znacznie upraszcza programowania w języku C++. Aby uzyskać więcej informacji, zobacz [pojęcia](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Niektóre atrybuty są interpretowane bezpośrednio przez kompilator. Inne atrybuty wstrzyknięcie kodu do źródło programu, w którym kompilator następnie kompiluje. Ten kod wprowadzonego sprawia, że ułatwia programowanie dzięki zmniejszeniu ilości kodu, który trzeba napisać. Jednak czasami usterkę może spowodować awarię podczas wykonywania wprowadzonego kodu aplikacji. W takim przypadku prawdopodobnie można przyjrzeć się wprowadzonego kodu. Program Visual Studio udostępnia dwa sposoby, aby wprowadzony kod:  
  
- Możesz wyświetlić wprowadzonego kodu w **dezasemblacji** okna.  
  
- Za pomocą [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), można utworzyć pliku scalonego źródła, który zawiera oryginalną i wprowadzonego kodu.  
  
  **Dezasemblacji** okno przedstawia instrukcje języka asemblera, które odnoszą się do kodu źródłowego i kodu, wprowadzony przez atrybuty. Ponadto **dezasemblacji** okna można wyświetlić adnotacji kodu źródłowego.  
  
### <a name="to-turn-on-source-annotation"></a>Aby włączyć funkcję adnotacji źródła  
  
-   Kliknij prawym przyciskiem myszy **dezasemblacji** oknie i wybierz polecenie **Pokaż kod źródłowy** z menu skrótów.  
  
     Jeśli znasz lokalizację atrybutu w oknie źródła, można użyć menu skrótów, można znaleźć wprowadzonego kodu w **dezasemblacji** okna.  
  
### <a name="to-view-injected-code"></a>Aby wyświetlić wprowadzonego kodu  
  
1.  Debuger musi być w trybie przerwania.  
  
2.  W oknie kodu źródłowego umieść kursor w miejscu dostępnym dla atrybutu, którego wprowadzonego kodu, którą chcesz wyświetlić.  
  
3.  Kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **przejdź do demontażu** z menu skrótów.  
  
     Jeśli lokalizacja atrybutu zbliża się bieżący punkt wykonania, możesz wybrać **dezasemblacji** w oknie **debugowania** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Aby wyświetlić kod dezasemblacji w bieżącym punkcie Wykonywanie  
  
1.  Debuger musi być w trybie przerwania.  
  
2.  Z **debugowania** menu, wybierz **Windows**i kliknij przycisk **dezasemblacji**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)



