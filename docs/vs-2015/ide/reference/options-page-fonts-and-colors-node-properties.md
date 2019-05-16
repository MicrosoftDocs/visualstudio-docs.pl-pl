---
title: Strona opcji, czcionki i kolory — właściwości węzła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 788d6077af99e6fe9fa99328aa9281d6327297b1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697185"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Strona opcji, czcionki i kolory — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten dokument zawiera opis właściwości czcionek i kolorów dla okna narzędzi, które jest zarejestrowana w celu są wyświetlane w obszarze **czcionki i kolory** w **środowiska** kategorii **opcje** okno dialogowe. Obejmuje to obsługę dynamiczny charakter grup z możliwością kolorowania elementów, które można zmienić w przypadku instalowania lub odinstalowywania pakietów VSPackage.  
  
 W poniższej sekcji pokazano przykład typu zarejestrowanych okna i właściwości, które są dostępne dla każdego okna.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Edytor tekstu lub drukarki lub oknami dialogowymi i narzędzie Windows  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 —lub—  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 —lub—  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|fontFamily|Get/Set (ciąg)|Nazwa czcionki do użycia, takie jak "Courier New."|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|A <xref:EnvDTE.vsFontCharSet> określająca typ znaku skonfigurowany do używania takich jak hebrajski lub rosyjski.|  
|FontSize|Get/Set (krótki)|Rozmiar czcionki do użycia w punktach. Na przykład 10 lub 12.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Określanie nazw elementów właściwości na stronach opcji](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Strona opcji, środowisko — właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)   
 [Strona opcji, edytor tekstu — Właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)
