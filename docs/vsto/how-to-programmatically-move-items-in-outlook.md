---
title: 'Instrukcje: Programowe przenoszenie elementów w programie Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10b0f05e758f71830d5377c738ff9dee683022b8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641627"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Instrukcje: Programowe przenoszenie elementów w programie Outlook
  W tym przykładzie przenosi nieprzeczytanych wiadomości e-mail z **skrzynki odbiorczej** w folderze o nazwie **testu**. Przykład dotyczy tylko przeniesienia wiadomości, które zawierają wyraz **testu** w `Subject` pola.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

-   Folder poczty programu Outlook o nazwie **testu**.

-   Wiadomość e-mail zawierająca nadejściu wyrazami **testu** w `Subject` pola.

## <a name="see-also"></a>Zobacz także
- [Praca z folderami](../vsto/working-with-folders.md)
- [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Instrukcje: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
