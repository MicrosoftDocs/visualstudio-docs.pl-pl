---
title: Strona opcji, czcionki i kolory — Właściwości węzła
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5363d71082128c13146c445fe312424be7e4340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945597"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Strona opcji, czcionki i kolory — Właściwości węzła
Ten dokument zawiera opis właściwości czcionek i kolorów dla okna narzędzi, które jest zarejestrowana w celu są wyświetlane w obszarze **czcionki i kolory** w **środowiska** kategorii **opcje** okno dialogowe. Obejmuje to obsługę dynamiczny charakter grup z możliwością kolorowania elementów, które można zmienić w przypadku instalowania lub odinstalowywania pakietów VSPackage.

 W poniższej sekcji pokazano przykład typu zarejestrowanych okna i właściwości, które są dostępne dla każdego okna.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Edytor tekstu lub drukarki lub oknami dialogowymi i narzędzie Windows
 `DTE.Properties("FontsAndColors", "TextEditor")`

 —lub—

 `DTE.Properties("FontsAndColors", "Printer")`

 —lub—

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nazwa elementu właściwości|Wartość|Opis|
| - |-----------|-----------------|
|fontFamily|Get/Set (ciąg)|Nazwa czcionki do użycia, takie jak "Courier New."|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|A <xref:EnvDTE.vsFontCharSet> określająca typ znaku skonfigurowany do używania takich jak hebrajski lub rosyjski.|
|FontSize|Get/Set (krótki)|Rozmiar czcionki do użycia w punktach. Na przykład 10 lub 12.|

## <a name="see-also"></a>Zobacz też

- [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Określanie nazw elementów właściwości na stronach opcji](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Strona opcji, środowisko — Właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)
- [Strona opcji, edytor tekstu — Właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)