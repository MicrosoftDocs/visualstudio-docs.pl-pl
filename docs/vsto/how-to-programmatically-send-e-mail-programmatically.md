---
title: 'Instrukcje: Programowane wysyłanie wiadomości e-mail'
description: Użyj programu Visual Studio, aby programowo wysłać wiadomość e-mail z programu Microsoft Outlook. Ten przykład wysyła wiadomość e-mail do kontaktów, które mają nazwę domeny example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c2b702d2986315ce32a9ab489db239f2c784f3e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877866"
---
# <a name="how-to-programmatically-send-email"></a>Instrukcje: Programowane wysyłanie wiadomości e-mail
  Ten przykład wysyła wiadomość e-mail do kontaktów, które mają nazwę domeny **example.com** w swoich adresach e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga:

- Kontakty, które mają nazwę domeny **example.com** w swoich adresach e-mail.

## <a name="robust-programming"></a>Niezawodne programowanie
 Nie usuwaj kodu filtru, który wyszukuje nazwę domeny **example.com**. Po usunięciu filtru Twoje rozwiązanie wyśle wiadomości e-mail do wszystkich kontaktów.

## <a name="see-also"></a>Zobacz też
- [Pracuj z elementami poczty](../vsto/working-with-mail-items.md)
- [Instrukcje: programowe tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Instrukcje: programowe uzyskiwanie dostępu do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Instrukcje: Programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
