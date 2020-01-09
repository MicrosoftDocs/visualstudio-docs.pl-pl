---
title: 'Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e78bd32bf9c21829adeb04a22cd30abb47a3379
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596141"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)

Właściwość `Icon` projektu określa plik ikony ( *. ico*), który będzie wyświetlany dla skompilowanej aplikacji w **Eksploratorze plików** i na pasku zadań systemu Windows.

Do właściwości `Icon` można uzyskać dostęp w okienku **aplikacji** **projektanta projektu**; zawiera listę ikon, które zostały dodane do projektu jako zasoby lub jako pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji można również ustawić właściwość `Icon` każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacje na temat ikon okna dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

## <a name="to-specify-an-application-icon"></a>Aby określić ikonę aplikacji

1. W **Eksplorator rozwiązań**wybierz węzeł projektu (nie węzeł **rozwiązania** ).

1. Na pasku menu wybierz **projekt** > **Właściwości**.

1. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **aplikacja** .

1. **(Visual Basic)** &mdash;na liście **ikon** wybierz plik ikony ( *. ico*).

    **C#** &mdash;obok listy **ikon** wybierz pozycję **\<Przeglądaj... >** przycisk, a następnie przejdź do lokalizacji pliku ikony, który chcesz.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
