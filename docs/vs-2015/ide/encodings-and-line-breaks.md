---
title: Kodowania i podziały wierszy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e1b13cc101ea4d7609633fd9c11bf87946d7b7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665725"
---
# <a name="encodings-and-line-breaks"></a>Kodowania i linie podziału
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można użyć ustawień **opcji Zapisz plik/zaawansowane** , aby określić typ znaków podziału wiersza. Możesz również zmienić kodowanie pliku przy użyciu tych samych ustawień.

> [!NOTE]
> Jeśli masz pewne typy ustawień deweloperskich (Visual Basic, F#, Programowanie dla sieci Web), w menu mogą nie być widoczne **Zaawansowane opcje zapisywania** . Aby zmienić ustawienia (na przykład ogólne), Otwórz pozycję **Narzędzia/Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 W programie Visual Studio następujące znaki są interpretowane jako podziały wierszy:

- CRLF: powrót karetki + wysuw wiersza, znaki Unicode 000D + 000A

- LF: wiersz wysuwu wiersza, 000A znaków Unicode

- NEL: Następny wiersz, znak Unicode 0085

- LS: separator wiersza, znak Unicode 2028

- PS: Separator akapitu, znak Unicode 2029

  Tekst skopiowany z innych aplikacji zachowuje pierwotne kodowanie i znaki podziału wiersza. Na przykład podczas kopiowania tekstu z programu Notepad i wklejania go do pliku tekstowego w programie Visual Studio, tekst ma te same ustawienia, które miały w Notatniku.

  Po otwarciu pliku, który ma różne znaki podziału wiersza, może pojawić się okno dialogowe z pytaniem, czy niespójne znaki podziału wiersza powinny być znormalizowane i jakiego typu podziały wierszy mają być wybierane.
