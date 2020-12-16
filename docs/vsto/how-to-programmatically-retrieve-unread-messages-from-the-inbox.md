---
title: Programowe pobieranie nieprzeczytanych wiadomości z skrzynki odbiorczej
description: Dowiedz się, jak używać programu Visual Studio do programistycznego pobierania nieprzeczytanych wiadomości ze skrzynki odbiorczej w programie Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6dae629c008c04f7ee9fb66b9dbc5f8f31e53d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528258"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Instrukcje: programowe pobieranie nieprzeczytanych wiadomości ze skrzynki odbiorczej
  Ten przykład pobiera nieprzeczytane wiadomości e-mail ze **skrzynki odbiorczej** programu Outlook i wyświetla liczbę elementów.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z elementami poczty](../vsto/working-with-mail-items.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Instrukcje: programowe tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Instrukcje: Programowane wysyłanie wiadomości e-mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Instrukcje: Programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
