---
title: 'Instrukcje: Debugowanie wprowadzonego kodu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35d2343343bf554df7592c8616e7697d88665baf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847780"
---
# <a name="how-to-debug-injected-code"></a>Instrukcje: Debugowanie wprowadzonego kodu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

Przy użyciu atrybutów znacznie upraszcza programowania w języku C++. Aby uzyskać więcej informacji, zobacz [pojęcia](/cpp/windows/attributed-programming-concepts). Niektóre atrybuty są interpretowane bezpośrednio przez kompilator. Inne atrybuty wstrzyknięcie kodu do źródło programu, w którym kompilator następnie kompiluje. Ten kod wprowadzonego sprawia, że ułatwia programowanie dzięki zmniejszeniu ilości kodu, który trzeba napisać. Jednak czasami usterkę może spowodować awarię podczas wykonywania wprowadzonego kodu aplikacji. W takim przypadku prawdopodobnie można przyjrzeć się wprowadzonego kodu. Program Visual Studio udostępnia dwa sposoby, aby wprowadzony kod:

- Możesz wyświetlić wprowadzonego kodu w **dezasemblacji** okna.

- Za pomocą [/Fx](/cpp/build/reference/fx-merge-injected-code), można utworzyć pliku scalonego źródła, który zawiera oryginalną i wprowadzonego kodu.

**Dezasemblacji** okno przedstawia instrukcje języka asemblera, które odnoszą się do kodu źródłowego i kodu, wprowadzony przez atrybuty. Ponadto **dezasemblacji** okna można wyświetlić adnotacji kodu źródłowego.

## <a name="to-turn-on-source-annotation"></a>Aby włączyć funkcję adnotacji źródła

- Kliknij prawym przyciskiem myszy **dezasemblacji** oknie i wybierz polecenie **Pokaż kod źródłowy** z menu skrótów.

     Jeśli znasz lokalizację atrybutu w oknie źródła, można użyć menu skrótów, można znaleźć wprowadzonego kodu w **dezasemblacji** okna.

## <a name="to-view-injected-code"></a>Aby wyświetlić wprowadzonego kodu

1. Debuger musi być w trybie przerwania.

2. W oknie kodu źródłowego umieść kursor w miejscu dostępnym dla atrybutu, którego wprowadzonego kodu, którą chcesz wyświetlić.

3. Kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **przejdź do demontażu** z menu skrótów.

     Jeśli lokalizacja atrybutu zbliża się bieżący punkt wykonania, możesz wybrać **dezasemblacji** w oknie **debugowania** menu.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Aby wyświetlić kod dezasemblacji w bieżącym punkcie Wykonywanie

1. Debuger musi być w trybie przerwania.

2. Z **debugowania** menu, wybierz **Windows**i kliknij przycisk **dezasemblacji**.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)