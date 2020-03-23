---
title: Formatowanie kodu
description: W tym artykule opisano różne opcje, za pomocą których można zmodyfikować zachowanie edytora tekstu w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: dca21119a73c03b63a273f7b4c22d70ecdb2a583
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984684"
---
# <a name="editor-behavior"></a>Zachowanie edytora

Zachowania edytora można ustawić, aby umożliwić kod, który ma być sformatowany w miarę jego zapisu. Te akcje są ustawiane w obszarze **Preferencje > programu Visual Studio > Edytor tekstu > zachowanie**, a niektóre z najczęściej używanych funkcji są opisane poniżej:

![Opcje zachowania edytora](media/source-editor-image9.png)

* Pasujące nawiasy klamrowe zamknięcia mogą być dodawane automatycznie do kodu podczas tworzenia nowych klas, metod lub właściwości. Gdy ta opcja jest `{` zaznaczona, `}`wpisanie automatycznie spowoduje dodanie .
* Formatowanie kodu w locie jest wyzwalane przez naciśnięcia znaków, takie jak średnik lub nawiasy klamrowe, które będą emulować ustawione preferencje formatowania.
* Można również sformatować plik podczas zapisywania go, co umożliwia pisanie kodu zgodnie z potrzebami i pozostawia IDE odpowiedzialny za formatowanie kodu, jak ustawiane przez istniejące preferencje.
* Wcięcie można ustawić na Brak, Auto lub Inteligentne. Wykonaj następujące czynności:
  * Brak - ustawia cieszę na początek następnego wiersza
  * Auto - ustawia cieszę na tę samą kolumnę w następnym wierszu
  * Smart - wcięcie w następującym wierszu na podstawie kodu
* Zachowanie łamiące wyrazy różni się między systemami operacyjnymi, a do celów nawigacji edytor tekstu musi wiedzieć, gdzie słowa zaczynają się lub kończą. Formatowanie można ustawić na Uniksa lub system Windows.

Można również ustawić reguły formatowania dla formatów XML, CSS, HTML i JSON.

## <a name="see-also"></a>Zobacz też

- [Preferencje stylu kodu (Visual Studio w systemie Windows)](/visualstudio/ide/code-styles-and-quick-actions)
