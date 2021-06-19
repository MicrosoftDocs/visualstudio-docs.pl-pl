---
title: Wyświetlanie wartości rejestru w debugerze | Microsoft Docs
description: Wyświetl wartości rejestru w oknie Rejestry w Visual Studio. Podczas debugowania wartości są rejestrowane podczas wykonywania kodu w aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2648f74453f51cd8d655ccb0c2344eb1030c1ed
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385399"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Wyświetlanie wartości rejestru w oknie Rejestry (C#, C++, Visual Basic, F#)

W **oknie Rejestry** jest wyświetlana zawartość rejestru Visual Studio debugowania. Aby uzyskać szczegółowe wprowadzenie do pojęć związanych z rejestrami i okna **Rejestry,** zobacz [Debugging basics: Registers window](../debugger/debugging-basics-registers-window.md)(Podstawy debugowania: rejestry).

> [!NOTE]
> Informacje o rejestracji nie są dostępne dla skryptów ani aplikacji SQL.

Podczas debugowania wartości są rejestrowane podczas wykonywania kodu w aplikacji. Ostatnio zmienione wartości są wyświetlane na czerwono w **oknie Rejestry.**

Aby ograniczyć nieład, w **oknie Rejestry** rejestry są organizowane w grupy, które różnią się w zależności od typu platformy i procesora. Grupy rejestrów można wyświetlać lub ukrywać. Aby uzyskać więcej informacji, zobacz [How to: Display and hide register groups (Jak wyświetlać i ukrywać grupy rejestru).](../debugger/how-to-display-and-hide-register-groups.md)

Aby uzyskać informacje na temat flag wyświetlonych w **oknie Rejestry,** zobacz [Informacje o oknie Rejestry](../debugger/debugging-basics-registers-window.md)

Wartości rejestru można edytować. Aby uzyskać więcej informacji, [zobacz Jak edytować wartość rejestru](../debugger/how-to-edit-a-register-value.md).

**Aby otworzyć okno Rejestry**

1. Włącz debugowanie na poziomie adresu, wybierając pozycję Włącz **debugowanie na** poziomie adresu w menu Narzędzia **(lub** Debugowanie **)**>   >  **debugowania.**

1. Gdy debugowanie jest uruchomione lub w punkcie przerwania, wybierz pozycję **Debuguj** rejestry systemu  >  **Windows**  >  lub naciśnij **klawisze Alt** + **5.**

>[!NOTE]
>Okna dialogowe i polecenia menu mogą się różnić w zależności od Visual Studio lub ustawień. Aby zmienić ustawienia, wybierz pozycję **Importuj i** eksportuj ustawienia w menu Visual Studio **Narzędzia.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Zobacz też

- [Podstawy debugowania: okno Rejestry](../debugger/debugging-basics-registers-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
