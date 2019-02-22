---
title: 'Instrukcje: Programowo Wyślij wiadomość e-mail'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 280b4f526bad3e0ba646058b3e2410a98ca910fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646008"
---
# <a name="how-to-programmatically-send-email"></a>Instrukcje: Programowo Wyślij wiadomość e-mail
  W tym przykładzie wysyła wiadomość e-mail do kontaktów, które mają taką nazwę domeny **example.com** adresu e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

-   Kontakty, które mają taką nazwę domeny **example.com** adresu e-mail.

## <a name="robust-programming"></a>Skuteczne programowanie
 Nie usuwaj kodu filtr, który wyszukuje nazwy domeny **example.com**. Rozwiązanie będzie wysyłać wiadomości e-mail do wszystkich kontaktów, jeśli usuniesz filtr.

## <a name="see-also"></a>Zobacz także
- [Praca z elementami poczty](../vsto/working-with-mail-items.md)
- [Instrukcje: Programowe tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Instrukcje: Programowy dostęp do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
