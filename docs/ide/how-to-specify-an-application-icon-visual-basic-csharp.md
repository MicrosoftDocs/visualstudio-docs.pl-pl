---
title: 'Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)'
description: Dowiedz się, jak za pomocą właściwości Icon określić ikonę wyświetlaną w Eksploratorze plików i na pasku zadań systemu Windows dla skompilowanej aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596914"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)

`Icon`Właściwość projektu określa plik ikony (*. ico*), który będzie wyświetlany dla skompilowanej aplikacji w **Eksploratorze plików** i na pasku zadań systemu Windows.

`Icon`Właściwość może być dostępna w okienku **aplikacji** **projektanta projektu**. zawiera listę ikon, które zostały dodane do projektu jako zasoby lub jako pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji można również ustawić `Icon` Właściwość każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacje na temat ikon okna dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> Właściwość.

## <a name="to-specify-an-application-icon"></a>Aby określić ikonę aplikacji

1. W **Eksplorator rozwiązań** wybierz węzeł projektu (nie węzeł **rozwiązania** ).

1. Na pasku menu wybierz **Project**  >  **Właściwości** projektu.

1. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **aplikacja** .

1. **(Visual Basic)** &mdash; Na liście **ikon** wybierz plik ikony (*. ico*).

    Język **C#** &mdash; Obok listy **ikon** wybierz **\<Browse...>** przycisk, a następnie przejdź do lokalizacji pliku ikony, który chcesz.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
