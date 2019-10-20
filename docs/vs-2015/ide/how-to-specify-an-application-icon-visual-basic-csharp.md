---
title: 'Instrukcje: Określanie ikony aplikacji (Visual Basic, C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670700"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Porady: określanie ikony aplikacji (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Właściwość `Icon` projektu określa plik ikony (. ico), który będzie wyświetlany dla skompilowanej aplikacji w Eksploratorze plików i na pasku zadań systemu Windows.

 Do właściwości `Icon` można uzyskać dostęp w okienku **aplikacji** **projektanta projektu**; zawiera listę ikon, które zostały dodane do projektu jako zasoby lub jako pliki zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji można również ustawić właściwość `Icon` każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacje na temat ikon okna dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

### <a name="to-specify-an-application-icon"></a>Aby określić ikonę aplikacji

1. W **Eksplorator rozwiązań**wybierz węzeł projektu (nie węzeł **rozwiązania** ).

2. Na pasku menu wybierz **projekt**, **Właściwości**.

3. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **aplikacja** .

4. **(Visual Basic)** Na liście **ikon** wybierz plik ikony (. ico).

     **C#** Obok listy **ikon** wybierz **\<Browse... >** przycisk, a następnie przejdź do lokalizacji pliku ikony, który chcesz.

## <a name="see-also"></a>Zobacz też
 Strona aplikacji [, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) [Zarządzanie właściwościami aplikacji](../ide/application-properties.md) [instrukcje: Dodawanie lub usuwanie zasobów](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
