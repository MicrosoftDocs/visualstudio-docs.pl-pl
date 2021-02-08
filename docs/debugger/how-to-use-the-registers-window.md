---
title: Wyświetlanie wartości rejestru w debugerze | Microsoft Docs
description: Wyświetl wartości rejestru w oknie rejestry w programie Visual Studio. Podczas debugowania Zarejestruj wartości Zmień kod w aplikacji.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: ea0275a5186b58c9b9a07934b95351b597a816f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845012"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Wyświetl wartości rejestru w oknie rejestry (C#, C++, Visual Basic, F #)

W oknie **rejestry** jest wyświetlana zawartość rejestru podczas debugowania programu Visual Studio. Aby uzyskać szczegółowe informacje na temat pojęć związanych z rejestrami i oknem **rejestrów** , zobacz [podstawy debugowania: okno rejestrów](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informacje dotyczące rejestrowania nie są dostępne dla aplikacji skryptowych i SQL.

Podczas debugowania Zarejestruj wartości Zmień kod w aplikacji. Ostatnio zmienione wartości są wyświetlane na czerwono w oknie **rejestry** .

Aby zmniejszyć liczbę bałaganów, w oknie **rejestry** są organizowane rejestry w grupach, które różnią się w zależności od typu platformy i procesora. Można wyświetlić lub ukryć grupy rejestrów. Aby uzyskać więcej informacji, zobacz [How to: Display and Hide Groups](../debugger/how-to-display-and-hide-register-groups.md).

Aby uzyskać informacje na temat flag widocznych w oknie **rejestry** , zobacz [Informacje o oknie rejestrów](../debugger/debugging-basics-registers-window.md)

Można edytować wartości rejestru. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie wartości rejestru](../debugger/how-to-edit-a-register-value.md).

**Aby otworzyć okno rejestry**

1. Włącz debugowanie na poziomie adresu, wybierając opcję **Włącz debugowanie na poziomie adresu** w **narzędziu** (lub **Debuguj**) >  >  **debugowanie** opcji.

1. Gdy debugowanie jest uruchomione lub w punkcie przerwania, wybierz kolejno opcje **Debuguj**  >    >  **rejestry** systemu Windows lub naciśnij klawisze **Alt** + **5**.

>[!NOTE]
>Okna dialogowe i polecenia menu mogą się różnić w zależności od wersji lub ustawień programu Visual Studio. Aby zmienić ustawienia, wybierz pozycję **Importuj i Eksportuj ustawienia** w menu **Narzędzia** programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Zobacz też

- [Podstawy debugowania: okno rejestrów](../debugger/debugging-basics-registers-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
