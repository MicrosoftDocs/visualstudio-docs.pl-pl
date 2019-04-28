---
title: Formatowanie kodu
description: W tym artykule opisano różne opcje, które mogą służyć do modyfikowania zachowania edytora tekstu w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 4a34076d06bfceb741b987377487a97291e8f726
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983678"
---
# <a name="editor-behavior"></a>Zachowanie edytora

Edytor zachowania można ustawić uruchamianie kodu do sformatowania, jak jest pisany. Te akcje są ustawiane w obszarze **programu Visual Studio > Preferencje > Edytor tekstu > zachowanie**, a niektóre z najczęściej używanych funkcji zostały opisane poniżej:

![Opcje zachowanie edytora](media/source-editor-image9.png)

* Dopasowywanie zamykające nawiasy klamrowe mogą być dodawane automatycznie do kodu podczas tworzenia nowej klasy, metody lub właściwości. Gdy ta opcja jest zaznaczona, wpisując `{` automatycznie doda `}`.
* Formatowanie kodu na bieżąco jest wyzwalana przez naciśnięcie znaków, takich jak rozdzielonych średnikami lub nawiasy klamrowe, które będą emulować preferencje formatowania, które są ustawione.
* Możesz również format pliku, zapisując go, co umożliwia pisanie kodu, zgodnie z potrzebami i pozostawia odpowiedzialny za formatowanie kodu według stawki ustalonej przez preferencje istniejącego środowiska IDE.
* Wcięcia można ustawić na wartość None, Auto, lub inteligentne. Te należy wykonać następujące czynności:
   * Brak — ustawia karetkę do początku następnego wiersza
   * Auto — ustawia karetkę do tej samej kolumny w następnym wierszu
   * Blokada Smart - wcięcia w następującym wierszu na podstawie kodu
* Zachowanie dzielącego wyrazy różni się od systemów operacyjnych, a do celów nawigacji, Edytor tekstu musi wiedzieć, gdzie słów rozpoczynać się ani kończyć. Formatowanie może być równa systemu Unix lub Windows.

Można również ustawić reguły formatowania dla XML, CSS, HTML i JSON.

## <a name="see-also"></a>Zobacz także

- [Preferencji stylu kodu (Visual Studio Windows)](/visualstudio/ide/code-styles-and-quick-actions)