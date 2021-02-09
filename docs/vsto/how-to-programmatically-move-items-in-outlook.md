---
title: 'Instrukcje: Programowane przenoszenie elementów w programie Outlook'
description: Dowiedz się, jak można programistycznie przenosić elementy w programie Microsoft Outlook. Ten przykład przenosi nieprzeczytane wiadomości e-mail ze skrzynki odbiorczej do folderu o nazwie test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888865"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Instrukcje: Programowane przenoszenie elementów w programie Outlook
  Ten przykład przenosi nieprzeczytane wiadomości e-mail ze **skrzynki odbiorczej** do folderu o nazwie **test**. W tym przykładzie tylko przenosi komunikaty, które mają wyraz **test** w `Subject` polu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga:

- Folder poczty programu Outlook o nazwie **test**.

- Wiadomość e-mail, która dociera do programu Word **test** w `Subject` polu.

## <a name="see-also"></a>Zobacz też
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Instrukcje: Programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
