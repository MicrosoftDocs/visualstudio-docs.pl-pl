---
title: Wyświetlanie wartości rejestru w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8622bb1288324429ad346834930559d1435ac6d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867582"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Wyświetlanie wartości rejestru w oknie rejestrów (C#, C++, Visual Basic F#)

**Rejestruje** okna wyświetla zawartość rejestru podczas debugowania programu Visual Studio. Ogólne wprowadzenie do pojęć dotyczących rejestrów i **rejestruje** okna, zobacz [podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informacje rejestru nie są dostępne dla skryptu lub aplikacji programu SQL.

Podczas debugowania, należy zarejestrować zmiany wartości, ponieważ kod jest wykonywany w swojej aplikacji. Wartości, które zostały zmienione ostatnio wyświetlane na czerwono na **rejestruje** okna.

Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach, które zależą od platformy i procesora typu. Możesz wyświetlać lub ukrywanie grup rejestru. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie i ukrywanie grup rejestru](../debugger/how-to-display-and-hide-register-groups.md).

Możesz edytować wartości rejestru. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie wartości rejestru](../debugger/how-to-edit-a-register-value.md).

**Aby otworzyć okno rejestrów**

1. Włącz debugowanie poziomie adresów, wybierając **Włącz debugowanie na poziomie adresów** w **narzędzia** (lub **debugowania**) > **opcje**  >  **Debugowania**.

1. Podczas debugowania jest uruchomione lub w punkcie przerwania, wybierz **debugowania** > **Windows** > **rejestruje**, lub naciśnij **Alt** + **5**.

>[!NOTE]
>Okna dialogowe i polecenia menu mogą się różnić w zależności od ustawienia lub wersji programu Visual Studio. Aby zmienić swoje ustawienia, wybierz pozycję **Import i eksport ustawień** w programie Visual Studio **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Zobacz także

- [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
