---
title: Formatowanie kodu
description: W tym artykule opisano różne opcje, których można użyć w celu zmodyfikowania zachowania edytora tekstu w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: dca21119a73c03b63a273f7b4c22d70ecdb2a583
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984684"
---
# <a name="editor-behavior"></a>Zachowanie edytora

Zachowania edytora można ustawić tak, aby umożliwić formatowanie kodu podczas pisania. Te akcje są ustawiane w obszarze **Preferencje programu Visual Studio > > zachowanie > edytora tekstu**, a niektóre z bardziej często używanych funkcji opisano poniżej:

![Opcje zachowania edytora](media/source-editor-image9.png)

* Dopasowywanie zamykających nawiasów klamrowych może być automatycznie dodawane do kodu podczas tworzenia nowych klas, metod lub właściwości. Gdy ta opcja jest zaznaczona, wpisywanie `{` zostanie automatycznie dodane `}` .
* Formatowanie kodu na bieżąco jest wyzwalane przez prasy znakowe, takie jak średnika lub nawiasy klamrowe, które będą emulować ustawione preferencje formatowania.
* Możesz również wybrać formatowanie pliku podczas zapisywania go, co pozwala na pisanie kodu zgodnie z potrzebami i pozostawia środowisko IDE odpowiedzialne za formatowanie kodu zgodnie z istniejącymi preferencjami.
* Wcięcia można ustawić na brak, automatyczne lub inteligentne. Wykonaj następujące czynności:
  * Brak — ustawia karetkę na początek następnego wiersza.
  * Autoustawianie karetki do tej samej kolumny w następnym wierszu
  * Inteligentne wcięcia w następującym wierszu w oparciu o kod
* Zachowanie dzielenia wyrazów różni się między systemów operacyjnych i w celach nawigacyjnych, Edytor tekstu musi wiedzieć, gdzie wyrazy zaczynają się lub kończą. Formatowanie można ustawić na system UNIX lub Windows.

Możesz również ustawić reguły formatowania dla plików XML, CSS, HTML i JSON.

## <a name="see-also"></a>Zobacz też

- [Preferencje stylu kodu (Visual Studio w systemie Windows)](/visualstudio/ide/code-styles-and-quick-actions)
