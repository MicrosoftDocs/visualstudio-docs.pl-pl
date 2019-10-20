---
title: Strona opcji, czcionki i kolory — właściwości węzła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662427"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Strona opcji, czcionki i kolory — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym dokumencie opisano właściwości czcionki i koloru okna narzędzia, które jest zarejestrowane do wyświetlania w obszarze **czcionki i kolory** w kategorii **środowisko** okna dialogowego **Opcje** . Obsługuje to dynamiczny charakter grup elementów, które można zmienić, jeśli pakietów VSPackage są zainstalowane lub odinstalowane.

 W poniższej sekcji przedstawiono przykład zarejestrowanego typu okna i właściwości, które są dostępne dla każdego okna.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Edytor tekstu lub drukarka, okna dialogowe i narzędzia
 `DTE.Properties("FontsAndColors", "TextEditor")`

 —lub—

 `DTE.Properties("FontsAndColors", "Printer")`

 —lub—

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|FontFamily|Get/set (ciąg)|Nazwa czcionki do użycia, taka jak "Courier New".|
|FontCharacterSet|Pobierz/ustaw (<xref:EnvDTE.vsFontCharSet>)|Wartość <xref:EnvDTE.vsFontCharSet>, określająca typ zestawu znaków, który ma być używany, na przykład hebrajski lub rosyjski.|
|FontSize|Pobierz/ustaw (krótki)|Rozmiar czcionki do użycia w punktach. Na przykład 10 lub 12.|

## <a name="see-also"></a>Zobacz też
 [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Określanie nazw elementów właściwości na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stronie Opcje strony Opcje, Strona Opcje [właściwości węzła środowiska](../../ide/reference/options-page-environment-node-properties.md) [, właściwości węzła edytora tekstu](../../ide/reference/options-page-text-editor-node-properties.md)
