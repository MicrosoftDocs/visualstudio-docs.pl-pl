---
title: Jak programowo ustalić bieżący element programu Outlook
description: Dowiedz się, jak programowo określić bieżący element programu Microsoft Outlook. W tym przykładzie użyto zdarzenia Explorer.SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cddc4bdc99e97c12a04e57639f990a1484c6581
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823932"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Jak programowo ustalić bieżący element programu Outlook
  W tym przykładzie użyto zdarzenia do wyświetlenia nazwy bieżącego folderu i niektórych `Explorer.SelectionChange` informacji o wybranym elementie. Następnie kod wyświetla wybrany element.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Terminy, kontakty i wiadomości e-mail w programie Microsoft Office Outlook.

## <a name="see-also"></a>Zobacz też
- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)
- [How to: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [How to: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
