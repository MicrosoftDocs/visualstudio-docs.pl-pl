---
title: Opcje, Edytor tekstu, Wszystkie języki, Paski przewijania
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
ms.openlocfilehash: 54ce07537adc436f719de8596657d1367afcb87d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588801"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Opcje, Edytor tekstu, Wszystkie języki, Paski przewijania
To okno dialogowe umożliwia zmianę domyślnego zachowania paska przewijania edytora kodu. Aby wyświetlić te opcje, wybierz **polecenie Opcje** z menu **Narzędzia.** W folderze **Edytor tekstu** rozwiń podfolder **Wszystkie języki,** a następnie wybierz polecenie **Paski przewijania**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Zresetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji Pasków przewijania we wszystkich językach do wyboru, niezależnie od wybranych w tym miejscu opcji. Aby zmienić opcje edytora tekstu tylko dla jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

## <a name="show-horizontal-scroll-bar"></a>Pokaż poziomy pasek przewijania

Gdy ta opcja jest zaznaczona, wyświetla poziomy pasek przewijania, który umożliwia przewijanie z boku na bok, aby wyświetlić elementy, które mieszczą się poza obszarem wyświetlania edytora. Jeśli poziome paski przewijania są niedostępne, można przewijać za pomocą klawiszy kursora.

## <a name="show-vertical-scroll-bar"></a>Pokaż pionowy pasek przewijania

Gdy ta opcja jest zaznaczona, wyświetla pionowy pasek przewijania, który umożliwia przewijanie w górę i w dół, aby wyświetlić elementy, które mieszczą się poza obszarem wyświetlania edytora. Jeśli pionowe paski przewijania nie są dostępne, można przewijać za pomocą klawiszy Page Up, Page Down i cursor.

## <a name="display"></a>Monitor

### <a name="show-annotations-over-vertical-scroll-bar"></a>Wyświetlanie adnotacji na pionowym pasku przewijania

Wybierz, czy na pionowym pasku przewijania są wyświetlane następujące adnotacje:

- zmiany
- znaki
- błędy
- pozycja cieczy

> [!TIP]
> Opcja **Pokaż znaczniki** zawiera punkty przerwania i zakładki.

Wypróbuj, otwierając duży plik kodu i zastępując tekst, który występuje w kilku miejscach w pliku. Pasek przewijania pokazuje efekt zamienników, dzięki czemu możesz wycofać zmiany, jeśli zastąpiono coś, czego nie powinieneś mieć.

Zobacz post w blogu [rozszerzonego paska przewijania,](https://blogs.msdn.microsoft.com/cdnstudents/2014/01/21/visual-studio-tips-and-tricks-enhanced-scroll-bar/) co oznaczają różne kolory i symbole podczas edytowania kodu.

## <a name="behavior"></a>Zachowanie

Pasek przewijania ma dwa tryby: tryb paskowy i tryb mapy.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Używanie trybu paska dla pionowego paska przewijania

*Tryb paska* wyświetla wskaźniki adnotacji na pasku przewijania. Kliknięcie paska przewijania powoduje przewijanie strony w górę lub w dół, ale nie powoduje przeskakiwania do tej lokalizacji w pliku.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Korzystanie z trybu mapy dla pionowego paska przewijania

W *trybie mapy*po kliknięciu lokalizacji na pasku przewijania kursor przeskakuje do tej lokalizacji w pliku, a nie tylko przewijanie strony w górę lub w dół. Linie kodu są wyświetlane w miniaturze na pasku przewijania. Możesz wybrać, jak szeroka jest kolumna mapy, wybierając wartość w **przeglądzie źródła**. Aby włączyć większy podgląd kodu podczas umieszczenia wskaźnika na mapie, wybierz opcję **Pokaż podgląd etykietki narzędzia.** Zwinięte regiony są inaczej zacieniowane i rozszerzane po dwukrotnym kliknięciu.

> [!TIP]
> Miniaturowy widok kodu można wyłączyć w trybie mapy, ustawiając **podgląd źródła** na **Wyłączone**. Jeśli zaznaczona jest **etykietka narzędzia Pokaż podgląd,** po kliknięciu wskaźnika na pasku przewijania nadal jest wyświetlany podgląd kodu w tej lokalizacji, a kursor nadal przechodzi do tej lokalizacji w pliku.

## <a name="see-also"></a>Zobacz też

- [Jak: Dostosowywanie paska przewijania](../how-to-track-your-code-by-customizing-the-scrollbar.md)
