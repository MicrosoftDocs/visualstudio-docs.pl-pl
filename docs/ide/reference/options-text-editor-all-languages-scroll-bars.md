---
title: Opcje, Edytor tekstu, wszystkie języki, paski przewijania
description: Dowiedz się, jak za pomocą strony paski przewijania w sekcji wszystkie języki zmienić domyślne zachowanie pasków przewijania edytora kodu w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f75ba02b65b7025f9cf1e4f2eb9b5b6e3de96be0
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039799"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Opcje, Edytor tekstu, wszystkie języki, paski przewijania
To okno dialogowe umożliwia zmianę domyślnego zachowania paska przewijania edytora kodu. Aby wyświetlić te opcje, wybierz opcję **Opcje** z menu **Narzędzia** . W folderze **Edytor tekstu** rozwiń podfolder **wszystkie języki** , a następnie wybierz **paski przewijania**.

> [!CAUTION]
> Ta strona służy do ustawiania opcji domyślnych dla wszystkich języków deweloperskich. Resetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji pasków przewijania we wszystkich językach do wybranych opcji. Aby zmienić opcje edytora tekstu dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

## <a name="show-horizontal-scroll-bar"></a>Pokaż poziomy pasek przewijania

Po wybraniu Wyświetla poziomy pasek przewijania, który umożliwia przewijanie z boku do widoku elementów, które znajdują się poza obszarem wyświetlania edytora. Jeśli poziome paski przewijania są niedostępne, możesz użyć klawiszy kursora do przewinięcia.

## <a name="show-vertical-scroll-bar"></a>Pokaż pionowy pasek przewijania

Po wybraniu Wyświetla pionowy pasek przewijania, który umożliwia przewijanie w górę i w dół w celu wyświetlenia elementów, które znajdują się poza obszarem wyświetlania edytora. Jeśli pionowe paski przewijania nie są dostępne, można użyć klawiszy Page Up, Page Down i Cursor do przewinięcia.

## <a name="display"></a>Wyświetlanie

### <a name="show-annotations-over-vertical-scroll-bar"></a>Pokaż adnotacje na pionowym pasku przewijania

Wybierz, czy pionowy pasek przewijania zawiera następujące adnotacje:

- zmiany
- znaki
- błędy
- położenie karetki

> [!TIP]
> Opcja **Pokaż znaczniki** zawiera punkty przerwania i zakładki.

Wypróbuj ją, otwierając plik dużego kodu i zastępując jakiś tekst występujący w kilku miejscach w pliku. Pasek przewijania pokazuje efekt zamian, dzięki czemu można cofnąć zmiany, jeśli zamienisz coś, czego nie trzeba.

Zapoznaj się z wpisem w blogu [Ulepszony pasek przewijania](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) , który oznacza różne kolory i symbole podczas edycji kodu.

## <a name="behavior"></a>Zachowanie

Pasek przewijania ma dwa tryby: tryb paskowy i tryb mapowania.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Użyj trybu paska dla pionowego paska przewijania

W *trybie paska* są wyświetlane wskaźniki adnotacji na pasku przewijania. Kliknięcie paska przewijania Przewija stronę w górę lub w dół, ale nie przechodzi do tej lokalizacji w pliku.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Użyj trybu mapy dla pionowego paska przewijania

W *trybie mapy*, gdy klikniesz lokalizację na pasku przewijania, kursor przejdzie do tej lokalizacji w pliku, a nie tylko przewijanie w górę lub w dół strony. Wiersze kodu są wyświetlane na pasku przewijania w miniaturach. Możesz wybrać szerokość kolumny mapy, wybierając wartość w **przeglądzie źródła**. Aby włączyć większą wersję zapoznawczą kodu po umieszczeniu wskaźnika na mapie, wybierz opcję **Pokaż podgląd etykietki narzędzia** . Zwinięte regiony są zacienione inaczej i rozszerzane po dwukrotnym kliknięciu.

> [!TIP]
> Miniaturowy widok kodu można wyłączyć w trybie mapy, ustawiając opcję **Źródło przegląd** na **off**. Jeśli zaznaczona jest **etykietka narzędzia Pokaż podgląd** , nadal zobaczysz Podgląd kodu w tej lokalizacji po umieszczeniu wskaźnika na pasku przewijania, a kursor nadal przeskakuje do tej lokalizacji w pliku po kliknięciu.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Dostosowywanie paska przewijania](../how-to-track-your-code-by-customizing-the-scrollbar.md)