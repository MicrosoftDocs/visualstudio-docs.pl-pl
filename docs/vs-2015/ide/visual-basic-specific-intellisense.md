---
title: Funkcja IntelliSense specyficzna dla Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c6895abd85a4394e4ddcaebcd6f09bc0a39936cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663028"
---
# <a name="visual-basic-specific-intellisense"></a>IntelliSense specyficzne dla Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor kodu źródłowego Visual Basic oferuje następujące funkcje IntelliSense:

- Wskazówki dotyczące składni

     Wskazówki dotyczące składni wyświetlają składnię wpisywanej instrukcji. Jest to przydatne w przypadku instrukcji, takich jak [DECLARE](https://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).

## <a name="automatic-completion"></a>Automatyczne uzupełnianie

- Uzupełnianie dla różnych słów kluczowych

   Na przykład po wpisaniu `goto` i spacji funkcja IntelliSense wyświetli listę zdefiniowanych etykiet w menu rozwijanym. Inne obsługiwane słowa kluczowe obejmują `Exit` , `Implements` , `Option` , i `Declare` .

- Ukończenie `Enum` i `Boolean`

   Gdy instrukcja odwołuje się do elementu członkowskiego wyliczenia, funkcja IntelliSense wyświetli listę elementów członkowskich `Enum` . Gdy instrukcja odwołuje się do programu `Boolean` , funkcja IntelliSense wyświetli menu rozwijane true-false.

  Zakończenie można wyłączyć domyślnie, usuwając zaznaczenie pozycji **autolista członków** z **ogólnej** strony właściwości w folderze **Visual Basic** .

  Można ręcznie wywołać uzupełnianie, wywołując członków listy, kompletny wyraz lub ALT + Strzałka w prawo. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Technologia IntelliSense w strefie
 Funkcja IntelliSense w strefie pomaga Visual Basic deweloperom, którzy muszą wdrażać aplikacje w systemie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i są ograniczone do ustawień częściowej relacji zaufania. Ta funkcja:

- Umożliwia wybranie uprawnień, z którymi będzie uruchamiana aplikacja.

- Wyświetlaj interfejsy API w wybranej strefie jako dostępne w liście członków i wyświetlaj interfejsy API, które wymagają dodatkowych uprawnień jako niedostępne.

  Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="see-also"></a>Zobacz też
 [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
