---
title: 'Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1e137eda77f1807b80409872d9fe0c2966df2a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656604"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)

Właściwość `Icon` projektu określa plik ikony ( *. ico*), który będzie wyświetlany dla skompilowanej aplikacji w **Eksploratorze plików** i na pasku zadań systemu Windows.

Do właściwości `Icon` można uzyskać dostęp w okienku **aplikacji** **projektanta projektu**; zawiera listę ikon, które zostały dodane do projektu jako zasoby lub jako pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji można również ustawić właściwość `Icon` każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacje na temat ikon okna dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

## <a name="to-specify-an-application-icon"></a>Aby określić ikonę aplikacji

1. W **Eksplorator rozwiązań**wybierz węzeł projektu (nie węzeł **rozwiązania** ).

1. Na pasku menu wybierz kolejno opcje **projekt** > **Właściwości**.

1. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **aplikacja** .

1. **(Visual Basic)** &mdash;In listy **ikon** , wybierz plik ikony ( *. ico*).

    **C#** &mdash;Near liście **ikon** wybierz **\<Browse... >** przycisk, a następnie przejdź do lokalizacji pliku ikony, który chcesz.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)