---
title: 'Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1e2502d2844b32f6f5e1c22c7fcddf7d6287c8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039348"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)

`Icon` Właściwość dla projektu określa plik ikony (*.ico*), będzie on wyświetlany dla aplikacji skompilowanych w **Eksploratora plików** i na pasku zadań Windows.

`Icon` Właściwości można uzyskiwać w **aplikacji** okienku **projektanta projektu**; zawiera on listę ikon, które zostały dodane do projektu jako zasoby lub pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikony dla aplikacji, możesz również ustawić `Icon` właściwości każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacji na temat okna ikony dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

## <a name="to-specify-an-application-icon"></a>Aby określić ikony aplikacji

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).

1. Na pasku menu wybierz **projektu** > **właściwości**.

1. Gdy **projektanta projektu** pojawi się, wybierz **aplikacji** kartę.

1. **(Visual Basic)**  &mdash;w **ikonę** listy, wybierz ikonę (*.ico*) pliku.

    **C#**&mdash;W pobliżu **ikonę** wybierz  **\<Przeglądaj … >** przycisk, a następnie przejdź do lokalizacji pliku ikony, która ma.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)