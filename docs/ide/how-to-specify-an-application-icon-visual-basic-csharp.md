---
title: 'Jak: Określ ikonę aplikacji (Visual Basic, C#)'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596141"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Jak: Określ ikonę aplikacji (Visual Basic, C#)

Właściwość `Icon` projektu określa plik ikony (*.ico*), który będzie wyświetlany dla skompilowaną aplikacji w **Eksploratorze plików** i na pasku zadań systemu Windows.

Właściwość `Icon` jest dostępna w okienku **aplikacji** **projektanta projektów;** zawiera listę ikon, które zostały dodane do projektu jako zasoby lub jako pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikony dla aplikacji, `Icon` można również ustawić właściwość każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacje na temat ikon okien dla aplikacji autonomicznych <xref:System.Windows.Window.Icon%2A> programu Windows Presentation Foundation (WPF), zobacz właściwość.

## <a name="to-specify-an-application-icon"></a>Aby określić ikonę aplikacji

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu (nie węzeł **Rozwiązanie).**

1. Na pasku menu wybierz polecenie**Właściwości** **projektu** > .

1. Po wyświetleniu **projektanta projektu** wybierz kartę **Aplikacja.**

1. **(Visual Basic)** &mdash;Na liście **Ikona** wybierz plik ikony (*.ico).*

    **C#**&mdash;W pobliżu listy **Ikony** wybierz przycisk ** \<Przeglądaj...>,** a następnie przejdź do lokalizacji odpowiedniego pliku ikony.

## <a name="see-also"></a>Zobacz też

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
