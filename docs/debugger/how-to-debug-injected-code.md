---
title: Debuguj wstrzyknięty kod | Microsoft Docs
description: 'Poznaj dwa sposoby wyświetlania wprowadzonego kodu: 1) w oknie demontażu przez program Visual Studio. 2) w pliku źródłowym, który ma zarówno wstrzyknięty, jak i oryginalny kod.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 5bce49eebf430ccaca9919c74966fb9efd00b09b
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903951"
---
# <a name="how-to-debug-injected-code"></a>Porady: Debugowanie wprowadzonego kodu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Używanie atrybutów może znacznie uprościć programowanie w języku C++. Aby uzyskać więcej informacji, zobacz [pojęcia](/cpp/windows/attributed-programming-concepts). Niektóre atrybuty są interpretowane bezpośrednio przez kompilator. Inne atrybuty wstrzyknąć kod do źródła programu, które następnie Kompilator kompiluje. Ten wstrzyknięty kod ułatwia programowanie przez zmniejszenie ilości kodu, który trzeba napisać. Czasami jednak usterka może spowodować niepowodzenie aplikacji podczas wykonywania wstrzykniętego kodu. Gdy tak się stanie, prawdopodobnie zechcesz przyjrzeć się wprowadzonym kodem. Program Visual Studio oferuje dwa sposoby wyświetlania wstrzykiwanego kodu:

- Wprowadzany kod można wyświetlić w oknie **demontażu** .

- Za pomocą [/FX](/cpp/build/reference/fx-merge-injected-code)można utworzyć scalony plik źródłowy zawierający oryginalny i wprowadzający kod.

Okno **demontażowe** zawiera instrukcje dotyczące języka zestawu, które odpowiadają kodowi źródłowej i kod wstrzykiwany przez atrybuty. Ponadto w oknie **demontażu** można wyświetlić adnotację kodu źródłowego.

## <a name="to-turn-on-source-annotation"></a>Aby włączyć adnotację źródłową

- Kliknij prawym przyciskiem myszy okno **demontaż** i wybierz polecenie **Pokaż kod źródłowy** z menu skrótów.

     Jeśli znasz lokalizację atrybutu w oknie źródłowym, możesz użyć menu skrótów, aby znaleźć wprowadzony kod w oknie **demontażu** .

## <a name="to-view-injected-code"></a>Aby wyświetlić wstrzyknięty kod

1. Debuger musi być w trybie przerwania.

2. W oknie kod źródłowy Umieść kursor przed atrybutem, którego kod został dodany.

3. Kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Przejdź do demontażu** z menu skrótów.

     Jeśli lokalizacja atrybutu znajduje się w bliskim bieżącym punkcie wykonywania, możesz wybrać okno **demontaż** z menu **debugowanie** .

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Aby wyświetlić kod demontażu w bieżącym punkcie wykonywania

1. Debuger musi być w trybie przerwania.

2. Z menu **Debuguj** wybierz opcję **Windows**, a następnie kliknij pozycję **demontaż**.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)